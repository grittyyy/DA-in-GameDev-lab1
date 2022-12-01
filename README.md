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

## Задание 1

![image](https://user-images.githubusercontent.com/105643001/205067776-4759a06d-256c-425c-878f-e597cba5557b.png)


![image](https://user-images.githubusercontent.com/105643001/205067514-094450bc-0c6c-40b4-9512-10842b15a96e.png)


## Задание 2

Установил TensorBoard

![image](https://user-images.githubusercontent.com/105643001/205069879-b67dfbc1-b25e-470a-be3c-d3a397e0175e.png)

Запустил с параметрами Economic

![image](https://user-images.githubusercontent.com/105643001/205072187-8b5329f3-bdba-4fc8-82c2-4833bafb7b77.png)

![image](https://user-images.githubusercontent.com/105643001/205072233-d2a65ef3-0946-4284-bef2-8e95b9b78553.png)

Запустил  с параметрами Economic и RollerBall

![image](https://user-images.githubusercontent.com/105643001/205073104-d248d828-45a0-4a72-a20c-1b1195eb531a.png)

Изменил переменные в файле Economic.yaml
batch_size: 2000
epsilon: 0.5
num_layers: 5
И получил такие графики:

![image](https://user-images.githubusercontent.com/105643001/205084720-bdd5fab6-9924-4921-8df4-9b86434f935d.png)

![image](https://user-images.githubusercontent.com/105643001/205084855-e24490c6-0dd9-4b50-9ec9-93c2839b158b.png)

График Cumulative Reward - это вознаграждение. Это значение следует максимизировать и приближать к единице.

График Episode Length - чем меньше данное значение (эпизод), тем эффективнее обучение.

График Policy Loss - изменение политики.

График Entropy - чем меньше величина, тем меньше агенту нужно изучить.

График Learning Rate - это значение должно постепенно уменьшаться.

Вывод

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
