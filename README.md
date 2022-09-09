# nbrb_rates
Тестовое задание для "ОАО Банковский процессинговый центр" - "Получение и отображение курсов валют с сайта НБ РБ".

По заданию реализованы две точки входа:
1. rates/import_rates/ (http://127.0.0.1:8000/rates/import_rates/) - для загрузки курсов в систему. Это POST запрос, параметрами передается json словарь вида {'date_import': '2022-09-09'}
2. rates/get_rate/YYYY-MM-DD/CUR_CODE (http://127.0.0.1:8000/rates/get_rate/2022-09-09/USD/), т.е. можно ввести прямо в браузере, код валюты, это текстовый код, типа EUR

Установка
1. В начале установить miniconda, скачать можно здесь https://conda.io/en/latest/miniconda.html .
2. Запустить cmd.exe
3. Перейти в папку проекта nbrb_rates\nbrb_rates, например так cd D:\src\nbrb_rates\nbrb_rates\
4. Создать окружение conda - conda create -n nbrb_rates python=3.9.12
5. Активировать окружение - conda activate nbrb_rates
6. Установить пакеты - pip install -r requirements.txt
7. Запустить сервер - python manage.py runserver

После этого можно тестировать сервис:
1. В браузере зайти на страницу http://127.0.0.1:8000/rates/ и далее можно щелкать по ссылкам.
2. Либо для просмотра курса можно перейти по ссылке вида http://127.0.0.1:8000/rates/get_rate/2022-09-09/GBP/ . В систему загружены курсы с 1 августа 2022 года по 11 сентября 2022 года.
3. Для тестирования post запроса можно воспользоваться соответствующими плагинами либо выполнить код в питоне:

import requests  
date_import = {'date_import': '2022-07-02'}  
resp = requests.post('http://127.0.0.1:8000/rates/import_rates/', json=date_import)  
print(resp.json())  
