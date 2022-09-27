# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил(а):
- Ершов Александр Николаевич
- РИ210943
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | # | 20 |

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
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.
## Задание 1
- Зашёл на Google Collab
- Создал пустой блокнот
- Написал print('Hello World')
- Запустил код
<img width="1260" alt="py hello world" src="https://user-images.githubusercontent.com/105643001/192529165-f2dc35f6-983f-4b6b-b985-fb0a22aa5d18.png">

- Сохранил файл на свой google диск
<img width="1256" alt="saved program" src="https://user-images.githubusercontent.com/105643001/192529371-bff5c805-0291-4409-86a3-8d808e63cb33.png">

- Настроил VS Code для работы с Unity
- Создал c# скрипт в Unity
- Написал в VS Code C# скрипт с выводом Hello World в консоль
<img width="1260" alt="unity HelloWorld" src="https://user-images.githubusercontent.com/105643001/192533216-1fb9edc8-6f7a-4a5e-aa5b-2290e01154ba.png">

- Перешёл в Unity и накинул скрипт на Camera
- Запустил программу и сделал скриншот вывода
<img width="1260" alt="unity HelloWorld2" src="https://user-images.githubusercontent.com/105643001/192533607-516f9af4-8d73-431a-abc1-016628acd0ee.png">



## Задание 2
### Пошагово выполнить каждый пункт раздела "ход работы" с описанием и примерами реализации задач
Ход работы:
- Произвести подготовку данных для работы с алгоритмом линейной регрессии. 10 видов данных были установлены случайным образом, и данные находились в линейной зависимости. Данные преобразуются в формат массива, чтобы их можно было вычислить напрямую при использовании умножения и сложения.
<img width="1260" alt="task2 1" src="https://user-images.githubusercontent.com/105643001/192551033-a6df3126-21fa-4670-b34e-cd5d7e1264b7.png">

- Определите связанные функции. Функция модели: определяет модель линейной регрессии wx+b. Функция потерь: функция потерь среднеквадратичной ошибки. Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.
<img width="1260" alt="task2 2" src="https://user-images.githubusercontent.com/105643001/192551246-37780a9d-dd0c-41ee-98d3-48a05c82a90f.png">

- Начать итерацию

- Инициализация и модель итеративной оптимизации
<img width="1231" alt="task2 3" src="https://user-images.githubusercontent.com/105643001/192551621-5152430d-523e-4220-ab52-bb3b0f06fb03.png">

- На 2 итерации отображаются значения параметров, значения потерь и эффекты визуализации после итерации
<img width="1232" alt="task2 4" src="https://user-images.githubusercontent.com/105643001/192551725-0c689eec-8055-47c7-827e-08269a931f58.png">

- На 3 итерации отображаются значения параметров, значения потерь и эффекты визуализации после итерации
<img width="1232" alt="task2 5" src="https://user-images.githubusercontent.com/105643001/192551818-809e42a1-9db6-45b9-b359-2a728ea483d1.png">

- На 4 итерации отображаются значения параметров, значения потерь и эффекты визуализации после итерации
<img width="1231" alt="task2 6" src="https://user-images.githubusercontent.com/105643001/192551935-1d69a036-81bd-4644-aad1-46d33cb41ace.png">

- На 5 итерации отображаются значения параметров, значения потерь и эффекты визуализации после итерации
<img width="1232" alt="task2 7" src="https://user-images.githubusercontent.com/105643001/192552000-5bb0864b-4051-46fe-a706-519a31814114.png">

- На 10000 итерации отображаются значения параметров, значения потерь и эффекты визуализации после итерации
<img width="1260" alt="task2 8" src="https://user-images.githubusercontent.com/105643001/192552083-76687638-39c9-4495-a843-c8626cbe3ac4.png">

## Задание 3
### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.

- Перечисленные в этом туториале действия могут быть выполнены запуском на исполнение скрипт-файла, доступного [в репозитории](https://github.com/Den1sovDm1triy/hfss-scripting/blob/main/ScreatingSphereInAEDT.py).
- Для запуска скрипт-файла откройте Ansys Electronics Desktop. Перейдите во вкладку [Automation] - [Run Script] - [Выберите файл с именем ScreatingSphereInAEDT.py из репозитория].

```py

import ScriptEnv
ScriptEnv.Initialize("Ansoft.ElectronicsDesktop")
oDesktop.RestoreWindow()
oProject = oDesktop.NewProject()
oProject.Rename("C:/Users/denisov.dv/Documents/Ansoft/SphereDIffraction.aedt", True)
oProject.InsertDesign("HFSS", "HFSSDesign1", "HFSS Terminal Network", "")
oDesign = oProject.SetActiveDesign("HFSSDesign1")
oEditor = oDesign.SetActiveEditor("3D Modeler")
oEditor.CreateSphere(
	[
		"NAME:SphereParameters",
		"XCenter:="		, "0mm",
		"YCenter:="		, "0mm",
		"ZCenter:="		, "0mm",
		"Radius:="		, "1.0770329614269mm"
	], 
)

```

## Выводы

Абзац умных слов о том, что было сделано и что было узнано.

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
