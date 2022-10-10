# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил:
- Ершов Александр Николаевич
- РИ210943

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
gs = gspread.service_account(filename='unitydata-365112-fa890e9be9ae.json')
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
### Реализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1.
Ход работы:

- Реализовал запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1.

<img width="1260" alt="image" src="https://user-images.githubusercontent.com/105643001/194902251-43125ce9-bbe0-4e50-b942-b0a08a8af94c.png">

```py
import gspread
import numpy as np

def loss_function(a, b, x, y):
    num = len(x)
    prediction = model(a, b, x)
    return (0.5 / num) * (np.square(prediction - y)).sum()

def model(a, b, x):
    return a * x + b

def optimize(a, b, x, y):
    num = len(x)
    prediction = model(a, b, x)
    da = (1.0 / num) * ((prediction - y) * x).sum()
    db = (1.0 / num) * ((prediction - y).sum())
    a = a - Lr * da
    b = b - Lr * db
    return a, b

def iterate(a, b, x, y, times):
    for i in range(times):
        a, b = optimize(a, b, x, y)
    return a, b

gc = gspread.service_account(filename='unitydata-365112-fa890e9be9ae.json')
sh = gc.open("UnitySheets")

x = [3, 21, 22, 34, 54, 34, 55, 67, 89, 99]
x = np.array(x)
y = [2, 22, 24, 65, 79, 82, 55, 130, 150, 199]
y = np.array(y)
a = np.random.rand(1)
b = np.random.rand(1)
Lr = 0.000001
price = np.random.randint(2000, 10000, 11)
mon = list(range(1, 11))
i = 0

while i <= len(mon):
    i += 1
    if i == 0:
        continue
    else:
        a, b = iterate(a, b, x, y, 100)
        prediction = model(a, b, x)
        loss = loss_function(a, b, x, y)
        tempInf = loss
        tempInf = str(tempInf)
        tempInf = tempInf.replace('.', ',')
        sh.sheet1.update(('A' + str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), str(tempInf))
        print(tempInf)
```

<img width="1258" alt="image" src="https://user-images.githubusercontent.com/105643001/194902809-26d43609-bcac-482e-af4d-00fba31a1ce9.png">

## Задание 3
### Самостоятельно разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от изменения считанных данных в задании 2.

```c#
void Update()
{
        if (dataSet["Mon_" + i.ToString()] <= 200 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioGood());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if (dataSet["Mon_" + i.ToString()] > 200 & dataSet["Mon_" + i.ToString()] < 500 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioNormal());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if (dataSet["Mon_" + i.ToString()] >= 500 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioBad());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }
    }   

    IEnumerator GoogleSheets()
    {
        UnityWebRequest curentResp = UnityWebRequest.Get("https://sheets.googleapis.com/v4/spreadsheets/1SwiTNXR8hpYxwXhl6UEeoc85sc5-SGpJqg-1ePr_mbE/values/Лист1?key=AIzaSyBisUEeyMSdgR-GQ0imQV8gX0NvtioNs_w");
        yield return curentResp.SendWebRequest();
        string rawResp = curentResp.downloadHandler.text;
        var rawJson = JSON.Parse(rawResp);
        foreach (var itemRawJson in rawJson["values"])
            {
            var parseJson = JSON.Parse(itemRawJson.ToString());
            var selectRow = parseJson[0].AsStringList;
            dataSet.Add(("Mon_" + selectRow[0]), float.Parse(selectRow[1]));
        }
    }
```
- Изменил значения границ

<img width="1260" alt="image" src="https://user-images.githubusercontent.com/105643001/194904719-ec68ce8d-7270-4eb6-8b0b-92ff7a9de48a.png">


## Выводы

В ходе выполнения лабораторной работы я ознакомился с программными средствами для организции передачи данных между инструментами google, Python и Unity. Написал програму на Phyton, которая выводит значения в таблицу Google Sheets и после написал программу для Unity, которая в зависимости от этих значений оформляет звуковое сопровождение.

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
