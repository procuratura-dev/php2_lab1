# php2_lab1

Лабораторная работа №1. Основы HTTP  

Целью данной лабораторной работы является изучение основных принципов протокола HTTP.

Задание №1. Анализ HTTP-запросов

    Зайдите на сайт http://sandbox.usm.md/login.
    Откройте вкладку Network в инструментах разработчика браузера.
    Введите неверные данные для входа (например, username: student, password: studentpass).
    Проанализируйте запросы, которые были отправлены на сервер.
    Ответьте на следующие вопросы:
        Какой метод HTTP был использован для отправки запроса?
        Какие заголовки были отправлены в запросе?
        Какие параметры были отправлены в запросе?
        Какой код состояния был возвращен сервером?
        Какие заголовки были отправлены в ответе?
    Повторите шаги 3-5, введя верные данные для входа (username: admin, password: password).

Задание №2. Составление HTTP-запросов

    Составьте GET-запрос к серверу по адресу http://sandbox.com, указав в заголовке User-Agent ваше имя и фамилию.
    Составьте POST-запрос к серверу по адресу http://sandbox.com/cars, указав в теле запроса следующие параметры:
        make: Toyota
        model: Corolla
        year: 2020
    Составьте PUT-запрос к серверу по адресу http://sandbox.com/cars/1, указав в заголовке User-Agent ваше имя и фамилию, в заголовке Content-Type значение application/json и в теле запроса следующие параметры: json { "make": "Toyota", "model": "Corolla", "year": 2021 }
    Напишите один из возможных вариантов ответа сервера следующий запрос. http POST /cars HTTP/1.1 Host: sandbox.com Content-Type: application/json User-Agent: John Doe model=Corolla&make=Toyota&year=2020 Предположите ситуации, когда сервер может вернуть HTTP-коды состояния 200, 201, 400, 401, 403, 404, 500.

Задание №3. Дополнительное задание. HTTP_Quest

    TIP
    Пройдите квест отправляя запросы на сервер.

    Отправьте POST-запрос на сервер по адресу http://sandbox.usm.md/quest, указав в заголовке User-Agent вашу фамилию и имя (Например User-Agent: John Doe).

POST /quest HTTP/1.1
Host: sandbox.usm.md
User-Agent: John Doe

curl:

curl -X POST http://sandbox.usm.md/quest -H "User-Agent: John Doe"

    Следуйте инструкциям на сервере, выполняя их по порядку.
    В конце квеста Вам будет показано секретное слово, которое Вы должны будете предоставить в отчете.

Примечание к заданию 3:

    Используйте инструмент curl, postman или любой другой инструмент для отправки запросов.
    Вы можете начинать квест заново, выполнив первый шаг.

Отчет

    Отчет по лабораторной работе должен соответсовать Гиду по написанию отчетов по лабораторным работам.
    Отчет должен быть составлен в формате Markdown и загружен в репозиторий на Git.


## Задание 1

#### 1. Какой метод HTTP был использован для отправки запроса? POST
#### 2. Какие заголовки были отправлены в запросе?

```http
POST /login/process.php HTTP/1.1
Host: sandbox.usm.md
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:125.0) Gecko/20100101 Firefox/125.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 37
Origin: http://sandbox.usm.md
Connection: keep-alive
Referer: http://sandbox.usm.md/login/
```

#### 3.Какие параметры были отправлены в запросе?

```http
username=student&password=studentpass
```
#### 4.Какой код состояния был возвращен сервером? 401 Unauthorized

#### 5.Какие заголовки были отправлены в ответе?

```http
HTTP/1.1 401 Unauthorized
Server: nginx/1.24.0 (Ubuntu)
Date: Thu, 19 Sep 2024 09:14:38 GMT
Content-Type: text/plain;charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
````

#### 6.Повторите шаги 3-5, введя верные данные для входа (username: admin, password: password):  
##### 6.1 Какие параметры были отправлены в запросе?
```http
username=admin&password=password
```
##### 6.2 Какой код состояния был возвращен сервером? 200 OK


##### 6.3 Какие заголовки были отправлены в ответе?
```http
HTTP/1.1 200 OK
Server: nginx/1.24.0 (Ubuntu)
Date: Thu, 19 Sep 2024 09:28:02 GMT
Content-Type: text/plain;charset=UTF-8
Transfer-Encoding: chunked
Connection: keep-alive
```

## Задание 2

#### 1.Составьте GET-запрос к серверу по адресу http://sandbox.com, указав в заголовке User-Agent ваше имя и фамилию.
```http
GET / HTTP/1.1
Host: sandbox.com
User-Agent: Иван Иванов
```

#### 2.Составьте POST-запрос к серверу по адресу http://sandbox.com/cars, указав в теле запроса следующие параметры: 

```http
POST /cars HTTP/1.1
Host: http://sandbox.com
model=Corolla&make=Toyota&year=2020
```

#### 3.Составьте PUT-запрос к серверу по адресу http://sandbox.com/cars/1, указав в заголовке User-Agent ваше имя и фамилию, в заголовке Content-Type значение application/json и в теле запроса следующие параметры: json { "make": "Toyota", "model": "Corolla", "year": 2021 }

```http
PUT /cars/1 HTTP/1.1
Host: sandbox.com
User-Agent: Иван Иванов
Content-Type: application/json

{
    "make": "Toyota",
    "model": "Corolla",
    "year": 2021
}
```

#### Напишите один из возможных вариантов ответа сервера следующий запрос. http POST /cars HTTP/1.1 Host: sandbox.com Content-Type: application/json User-Agent: John Doe model=Corolla&make=Toyota&year=2020 Предположите ситуации, когда сервер может вернуть HTTP-коды состояния 200, 201, 400, 401, 403, 404, 500.

##### 200 OK
```http
{
    "status": "success",
    "message": "Vehicle information retrieved successfully",
    "data": {
        "make": "Toyota",
        "model": "Corolla",
        "year": 2020
    }
}
```

##### 201 Created
```http
{
    "status": "success",
    "message": "New vehicle created successfully",
    "data": {
        "make": "Toyota",
        "model": "Corolla",
        "year": 2020,
        "id": 123
    }
}
```

##### 400 Bad Request
```http
{
    "status": "error",
    "message": "Invalid request format. Expected JSON."
}
```

##### 401 Unauthorized
```http
{
    "status": "error",
    "message": "Unauthorized. Please provide valid credentials."
}
```
##### 403 Forbidden
```http
{
    "status": "error",
    "message": "Forbidden. You do not have permission to perform this action."
}
```

##### 404 Not Found
```http
{
    "status": "error",
    "message": "Not Found. The requested resource does not exist."
}
```
##### 500 Internal Server Error
```http
{
    "status": "error",
    "message": "Internal Server Error. Please try again later."
}
```
## Задание 3

curl -X POST http://sandbox.usm.md/quest -H "User-Agent: Ivan Ivanov"

```http
/home/devrdn/www/quest/progress/********** HEADERS RECEIVED **********
User-Agent: Ivan Ivanov
Accept: */*
Host: sandbox.usm.md
Content-Length: 
Content-Type: 
**************************************
********** RESPONSE HEADERS **********
Content-Type: text/plain; charset=UTF-8
**************************************
1. Excellent, you have created an Agent. Here is your unique ID: 769610. Now, to verify your identity, send a POST request to http://sandbox.usm.md/quest/login with the Authorization header containing the token: ABcMOkgsNAQdGz8=. Make sure to remember both your ID and token!
2. id: 769610
3. token: ABcMOkgsNAQdGz8=
4. instruction: Send a POST request to http://sandbox.usm.md/quest/login with Authorization: Bearer ABcMOkgsNAQdGz8=
```

curl -X POST http://sandbox.usm.md/quest/login -H "Authorization: Bearer ABcMOkgsNAQdGz8="

```http
/home/devrdn/www/quest/progress/********** HEADERS RECEIVED **********
Authorization: Bearer ABcMOkgsNAQdGz8=
Accept: */*
User-Agent: curl/8.4.0
Host: sandbox.usm.md
Content-Length: 
Content-Type: 
**************************************
********** RESPONSE HEADERS **********
Content-Type: text/plain; charset=UTF-8
**************************************
1. Excellent, you have created an Agent. Here is your unique ID: 527598. Now, to verify your identity, send a POST request to http://sandbox.usm.md/quest/login with the Authorization header containing the token: KhQfOEddbFFdRA==. Make sure to remember both your ID and token!
2. id: 527598
3. token: KhQfOEddbFFdRA==
4. instruction: Send a POST request to http://sandbox.usm.md/quest/login with Authorization: Bearer KhQfOEddbFFdRA==
********** HEADERS RECEIVED **********
Authorization: Bearer ABcMOkgsNAQdGz8=
Accept: */*
User-Agent: curl/8.4.0
Host: sandbox.usm.md
Content-Length: 
Content-Type: 
**************************************
********** RESPONSE HEADERS **********
Content-Type: text/plain; charset=UTF-8
**************************************
1. Step 2 completed! Now, send a PUT request to http://sandbox.usm.md/quest/age with the request body age=<your age> and with the Authorization header with the token you received in the previous step.
2. next_step: Send a PUT request to http://sandbox.usm.md/quest/age with age=<your age> in the request body
```

curl -X PUT http://sandbox.usm.md/quest/age -H "Authorization: Bearer KhQfOEddbFFdRA==" -d "age=21"

```http
/home/devrdn/www/quest/progress/********** HEADERS RECEIVED **********
Content-Type: application/x-www-form-urlencoded
Content-Length: 6
Authorization: Bearer KhQfOEddbFFdRA==
Accept: */*
User-Agent: curl/8.4.0
Host: sandbox.usm.md
**************************************
********** RESPONSE HEADERS **********
Content-Type: text/plain; charset=UTF-8
**************************************
1. Age successfully updated! Now, send a GET request to http://sandbox.usm.md/quest/secret with your final token: KhQfOEddbFFdRB9CU1RSRFJXQ1Fx
2. final_token: KhQfOEddbFFdRB9CU1RSRFJXQ1Fx
3. instruction: Send a GET request to http://sandbox.usm.md/quest/secret?token=KhQfOEddbFFdRB9CU1RSRFJXQ1Fx
```

curl -X GET "http://sandbox.usm.md/quest/secret?token=KhQfOEddbFFdRB9CU1RSRFJXQ1Fx"

```http
/home/devrdn/www/quest/progress/********** HEADERS RECEIVED **********
Accept: */*
User-Agent: curl/8.4.0
Host: sandbox.usm.md
Content-Length: 
Content-Type: 
**************************************
Decoded full name: curl/8.4.0
Expected progress file: 9e35c119fa9d1b9b02b39361d4f10240.json
********** RESPONSE HEADERS **********
Content-Type: text/plain; charset=UTF-8
**************************************
1. Congratulations, curl/8.4.0! You have successfully completed the quest! Here is your secret: CjkdGkpxTVFiUVlGVA==
2. secret: CjkdGkpxTVFiUVlGVA==
```

### secret word: CjkdGkpxTVFiUVlGVA==