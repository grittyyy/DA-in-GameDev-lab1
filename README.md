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

## Задание 1

Создал новый проект в Unity и добавил пустой объект 'perceptron'

![image](https://user-images.githubusercontent.com/105643001/204279686-caebbaf8-b693-452c-b194-d3c05ac6eedf.png)

К нему прикрепил файл со скриптом, который скачал из материалов к ЛР

![image](https://user-images.githubusercontent.com/105643001/204280354-b01c1c82-10c5-476a-b85c-12a06d92fe6e.png)

Добавил в массив Ts логический элемент OR

![image](https://user-images.githubusercontent.com/105643001/204282018-15237f0d-4c82-4568-89cf-924b7f65094f.png)

Запустил 8 итераций

![image](https://user-images.githubusercontent.com/105643001/204282940-dcc5df3a-3ab1-440b-87e7-af316a011a02.png)

![image](https://user-images.githubusercontent.com/105643001/204283025-e5b31de3-91a1-4784-8b52-9b78963431a0.png)

![image](https://user-images.githubusercontent.com/105643001/204283064-5d9056cb-7425-46aa-88da-f490b5485d4a.png)

Можно увидеть, что перцептрон справляется с обучением гораздо быстрее, чем за 8 итераций. В конкретном случае хватило лишь 4-ёх.

Далее я добавил в массив логический элемент AND

![image](https://user-images.githubusercontent.com/105643001/204286533-5b659dc8-80b5-482d-9b37-9a2136ef2790.png)

![image](https://user-images.githubusercontent.com/105643001/204286580-78125417-5358-462a-936f-7758944797b9.png)

![image](https://user-images.githubusercontent.com/105643001/204286641-38f86b12-19d0-4687-886a-41ebf2e573c4.png)

Иногда перцептрон справляется с обучением ровно на восьмой итериации, но бывают случае когда он может не справиться, поэтому для 100% прохождения обучения можно увеличить переменную в функции Train до 10.
```
Train(10);
```

Далее я добавил в массив логический элемент NAND

![image](https://user-images.githubusercontent.com/105643001/204286923-3bab89dc-0ed2-438d-ba1e-4b6c9890a40c.png)

Перцептрон запросто справляется с обучением.

После чего я добавил в массив логический элемент XOR

![image](https://user-images.githubusercontent.com/105643001/204288418-6f6dcb90-9e3c-466f-ad02-12d2e281c771.png)

Можно увидеть, что не зависимо от колличества итераций перцептрон не справляется с обучением. Даже на 30 итерациях он выдаёт TOTAL ERROR: 4

Следовательно - перцептрон не может обучиться этой операции.

## Задание 2

Для каждой операции было запущено 5 попыток с 8-ю эпохами обучения. На графиках указано среднее значение Total Error за 5 попыток.

![image](https://user-images.githubusercontent.com/105643001/204300138-5c192f85-9644-4510-b109-1ba70fbf2228.png)

![image](https://user-images.githubusercontent.com/105643001/204300322-bdebbafc-18a0-489e-bb7f-9167bb68d746.png)

Количество эпох обучения зависит от решаемой операции. Допустим операция OR проходилась в среднем менее, чем за 6 итераций. Операция AND менее, чем за 7. Операция NAND также менее, чем за 7, а операция XOR так и не находила решения.

## Задание 3



## Выводы




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
