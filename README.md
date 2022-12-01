# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил:
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

Научиться интегрировать экономическую систему в Unity и обучить ей пользоваться Ml Agent.



## Задание 1

Открыл проект Unity скачанный из методички.

![image](https://user-images.githubusercontent.com/105643001/205067776-4759a06d-256c-425c-878f-e597cba5557b.png)

Запустил и разобрался с его работой

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

![image](https://user-images.githubusercontent.com/105643001/205094349-21a182d9-5f7c-4b25-a8c4-f68c278ad062.png)

![image](https://user-images.githubusercontent.com/105643001/205094392-50d4ef7e-24be-431c-bb11-a915396f05ce.png)

Cumulative Reward - это вознаграждение. Это значение должно приближаться к единице.

Episode Length - чем меньше эпизод, тем эффективнее обучение.

Policy Loss - изменение политики.

Entropy - чем меньше величина, тем меньше агенту нужно изучить.

Learning Rate - это значение должно постепенно уменьшаться.

## Выводы
В данной лабораторной при помощи ml-агента я выполнил реализацию поиска параметров сбалансированной экономической системы. Воспользовался библиотекой TensorBoard для визуализации метрик обучения агента. Изменил количество слоёв, размер выборки, epsilon и как итог у меня получилось успешно обучить агента.



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
