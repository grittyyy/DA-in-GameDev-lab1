# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил:
- Ершов Александр Николаевич
- РИ210943
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.

## Задание 1
- Создал новый пустой 3D проект в Unity
- В созданный проект добавил ML Agent (добавил .json файлы из папки)
![image](https://user-images.githubusercontent.com/105643001/198303262-167bc7d5-6e0f-4d25-bd17-40859f3fc729.png)
- Далее запустил Anaconda Prompt
![image](https://user-images.githubusercontent.com/105643001/198303536-4d29afb0-3560-4a6f-a17b-87fb2b261a97.png)
- Написал серию команд для создания и активации нового ML-агента, а также для скачивания необходимых библиотек

- На сцене создал куб, сферу и плоскость и подключил C# файл (RollerAgent.cs) к сфере
![image](https://user-images.githubusercontent.com/105643001/198304933-06e74979-1524-40dd-acf1-af7a165df6d9.png)

- В нём написал такой код
```C#
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
   Rigidbody rBody;
   void Start()
   {
       rBody = GetComponent<Rigidbody>();
   }

   public Transform Target;
   public override void OnEpisodeBegin()
   {
       if (this.transform.localPosition.y < 0)
       {
           this.rBody.angularVelocity = Vector3.zero;
           this.rBody.velocity = Vector3.zero;
           this.transform.localPosition = new Vector3(0, 0.5f, 0);
       }

       Target.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
   }
   public override void CollectObservations(VectorSensor sensor)
   {
       sensor.AddObservation(Target.localPosition);
       sensor.AddObservation(this.transform.localPosition);
       sensor.AddObservation(rBody.velocity.x);
       sensor.AddObservation(rBody.velocity.z);
   }
   public float forceMultiplier = 10;
   public override void OnActionReceived(ActionBuffers actionBuffers)
   {
       Vector3 controlSignal = Vector3.zero;
       controlSignal.x = actionBuffers.ContinuousActions[0];
       controlSignal.z = actionBuffers.ContinuousActions[1];
       rBody.AddForce(controlSignal * forceMultiplier);

       float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);

       if(distanceToTarget < 1.42f)
       {
           SetReward(1.0f);
           EndEpisode();
       }
       else if (this.transform.localPosition.y < 0)
       {
           EndEpisode();
       }
   }
}
```
- Сфере добавил компоненты Rigidbody, Decision Requester и Behaviour Parametres
![image](https://user-images.githubusercontent.com/105643001/198305953-347803cb-6c2e-4843-82fa-d68f2869f2cf.png)

- Добавил файл конфигурации нейронной сети в корень проекта
```C#
behaviors:
  RollerBall:
    trainer_type: ppo
    hyperparameters:                 
      batch_size: 10
      buffer_size: 100
      learning_rate: 3.0e-4
      beta: 5.0e-4
      epsilon: 0.2
      lambd: 0.99
      num_epoch: 3
      learning_rate_schedule: linear
    network_settings: 
      normalize: false
      hidden_units: 128
      num_layers: 2
    reward_signals:
      extrinsic:
        gamma: 0.99
        strength: 1.0
    max_steps: 500000
    time_horizon: 64
    summary_freq: 10000
```

- Запустил работу ML агента

![image](https://user-images.githubusercontent.com/105643001/198307067-ad8135cf-0ba2-4eec-b286-61a55495f622.png)

- Наблюдаем за результатом


https://user-images.githubusercontent.com/105643001/198307540-3b0fde7e-02b5-4b17-922e-7b7e5ec22450.mp4

- Создал 3 копии


https://user-images.githubusercontent.com/105643001/198321874-3f011fbf-3e05-45a3-8fa6-4f2c74f9e616.mp4

- Создал 9 копий


https://user-images.githubusercontent.com/105643001/198323785-f650166a-3f4c-421c-b790-d764df38ddea.mp4

- Создал 27 копий


https://user-images.githubusercontent.com/105643001/198327255-affad864-9677-4e92-a7c2-e1e0e8b825bf.mp4

- После завершения обучения получаил это:


https://user-images.githubusercontent.com/105643001/198330318-ecac8455-65b8-4502-8235-ddcec49534e2.mp4

- Выводы: после того, как я обучил модель, шар начал непосредственно двигаться к кубу более плавно, перестал падать за пределы плоскости

## Задание 2
```C#
behaviors:
  RollerBall:                        #Имя агента
    trainer_type: ppo                #Устанавливаем режим обучения (Proximal Policy Optimization).
    hyperparameters:                 #Задаются гиперпараметры.
      batch_size: 10                 #Количество опытов на каждой итерации для обновления экстремумов функции.
      buffer_size: 100               #Количество опыта, которое нужно набрать перед обновлением модели.
      learning_rate: 3.0e-4          #Устанавливает шаг обучения (начальная скорость).
      beta: 5.0e-4                   #Отвечает за случайность действия, повышая разнообразие и иследованность пространства обучения.
      epsilon: 0.2                   #Порог расхождений между старой и новой политиками при обновлении.
      lambd: 0.99                    #Определяет авторитетность оценок значений во времени. Чем выше значение, тем более авторитетен набор предыдущих оценок.
      num_epoch: 3                   #Количество проходов через буфер опыта, при выполнении оптимизации.
      learning_rate_schedule: linear #Определяет, как скорость обучения изменяется с течением времени, линейно уменьшает скорость.
    network_settings:                #Определяет сетевые настройки.
      normalize: false               #Отключается нормализация входных данных.
      hidden_units: 128              #Количество нейронов в скрытых слоях сети.
      num_layers: 2                  #Количество скрытых слоев для размещения нейронов.
    reward_signals:                  #Задает сигналы о вознаграждении.
      extrinsic:
        gamma: 0.99                  #Коэффициент скидки для будущих вознаграждений.
        strength: 1.0                #Шаг для learning_rate.
    max_steps: 500000                #Общее количество шагов, которые должны быть выполнены в среде до завершения обучения.
    time_horizon: 64                 #Количество циклов ML агента, хранящихся в буфере до ввода в модель.
    summary_freq: 10000              #Количество опыта, который необходимо собрать перед созданием и отображением статистики.
```

- Decision Requester - запрашивает решение через регулярные промежутки времени и обрабатывает чередование между ними во время обучения.

- Behavior Parameters - определяет принятие объектом решений, в него указывается какой тип поведения будет использоваться: уже обученная модель или удалённый процесс обучения.

## Задание 3
- Создал второй куб на сцене
- Изменил код скрипта
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }

    public Transform Target;
    public Transform Target2;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }

        Target.localPosition = new Vector3(Random.value * 8 - 4, 0.5f, Random.value * 8 - 4);
        Target2.localPosition = new Vector3(Random.value * 8 - 4, 0.5f, Random.value * 8 - 4); // Добавил строку
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target2.localPosition); 
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);

        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);
        float distanceToTarget2 = Vector3.Distance(this.transform.localPosition, Target2.localPosition); // Добавил строку

        if (distanceToTarget < 1.42f || distanceToTarget2 < 1.42f)
        {
            SetReward(1.0f);
            EndEpisode();
        }
        else if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}
```
- Наблюдаем результат



https://user-images.githubusercontent.com/105643001/198332294-28338a09-4745-4395-a0a5-b1cd5c2ef83b.mp4

## Выводы
- Игровой баланс в играх - это субъективное «равновесие» между персонажами, командами, тактиками игры и другими игровыми объектами. Игровой баланс является одним из требований к «честности» правил.

- Относительно простой нейронной сети достаточно, чтобы достичь высокой эффективности игры против игроков и традиционного игрового ИИ. Таких агентов можно использовать различными способами, например, для тренировки новых игроков или для выявления неожиданных стратегий. Так же системы машинного обучения могут использоваться для того, чтобы выявить дисбаланс в игре.



| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
