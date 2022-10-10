# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил(а):
- Ершов Александр Николаевич
- РИ210943
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
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
Познакомиться с программными средствами для организции передачи данных между инструментами google, Python и Unity.
## Задание 1
- В облачном сервисе google console подключил API для работы с google sheets и google drive.

<img width="1260" alt="image" src="https://user-images.githubusercontent.com/105643001/194899659-690101e3-6dc9-454a-9989-92ec5673e7a0.png">

- Написал скрипт на python, который ввдодит данные об инфляции в таблицу Google Sheets

<img width="616" alt="image" src="https://user-images.githubusercontent.com/105643001/194900419-1d2e8625-fde9-4fd6-821f-3124265290c5.png">

<img width="1260" alt="GoogleSheetsLast" src="https://user-images.githubusercontent.com/105643001/194900445-d1eb855e-11b0-4986-af3a-2d4690d25e9c.png">

```py
import gspread
import numpy as np
gs = gspread.service_account(filename='celestial-feat-364617-38d786a51576.json')
sh = gs.open("UnitySheets")
price = np.random.randint(2000, 10000, 11)
mon = list(range(1, 11))
i = 0
while i <= len(mon):
    i += 1
    if i == 0:
        continue
    else:
        tempInf = ((price[i-1]-price[i-2])/price[i-2])*100
        tempInf = str(tempInf)
        tempInf = tempInf.replace('.', ',')
        sh.sheet1.update(('A' + str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), str(price[i-1]))
        sh.sheet1.update(('C' + str(i)), str(tempInf))
        print(tempInf)
```

- Создал проект на Unity, который принимает данные из таблицы и сопровождает их подходящей озвучкой

<img width="1260" alt="image" src="https://user-images.githubusercontent.com/105643001/194901214-704c1cf1-53ae-4114-9af2-173bb168396c.png">

<img width="1260" alt="image" src="https://user-images.githubusercontent.com/105643001/194900838-97b6f69b-ba73-4fd7-bdc4-636cb016d4b5.png">


## Задание 2
### Пошагово выполнить каждый пункт раздела "ход работы" с описанием и примерами реализации задач
Ход работы:
- Произвести подготовку данных для работы с алгоритмом линейной регрессии. 10 видов данных были установлены случайным образом, и данные находились в линейной зависимости. Данные преобразуются в формат массива, чтобы их можно было вычислить напрямую при использовании умножения и сложения.
<img width="1260" alt="task2 1" src="https://user-images.githubusercontent.com/105643001/192557182-7d8e43da-33ee-4b31-ab69-ed2656f56fc1.png">

- Определите связанные функции. Функция модели: определяет модель линейной регрессии wx+b. Функция потерь: функция потерь среднеквадратичной ошибки. Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.
<img width="1260" alt="task2 2" src="https://user-images.githubusercontent.com/105643001/192557270-1eb56b67-8f7f-44c5-91bf-c978e7906155.png">

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

Я написал программы вывода Hello World в консоль на Python, используя Google Colab и на Unity на языке C#, используя VS Code. Также с помощью Google Colab я познакомился с основыными операторами языка Python на примере реализации линейной регрессии.

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
