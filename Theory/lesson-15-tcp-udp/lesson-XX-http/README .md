1. Теория
HTTP — HyperText Transfer Protocol. Протокол передачи гипертекста. Назначение: передача данных (HTML, JSON, изображений и т.д.) между клиентом и сервером по модели «запрос — ответ». Не хранит состояние.

HTTPS vs HTTP — HTTPS = HTTP + шифрование TLS/SSL. Порт 443 вместо 80. Данные зашифрованы, сервер аутентифицируется сертификатом. HTTP передаёт всё открытым текстом.

Клиент-серверная модель — архитектура, где клиент отправляет запросы, а сервер их обрабатывает и возвращает ответы. Клиентов много, сервер хранит данные и логику.

Идемпотентность — свойство операции давать один и тот же результат при многократном выполнении. В HTTP идемпотентны: GET, HEAD, PUT, DELETE, OPTIONS. Не идемпотентны: POST, PATCH.

2.1. Разбор запроса
Метод — POST

Путь — /api/users

Версия — HTTP/1.1

Content-Type — тип данных в теле запроса (application/json — JSON)

Authorization — данные для аутентификации (Bearer-токен JWT)

Тело — после пустой строки: {"name": "Иван", "email": "ivan@mail.com"}

Разбор ответа
201 Created — запрос успешен, создан новый ресурс

Location — URL созданного ресурса (/api/users/42)

Тело — {"id": 42, "name": "Иван", "email": "ivan@mail.com"}
2.3. Собери запрос сам
Список всех товаров:
GET /api/products HTTP/1.1
Host: example.com
Создание товара:
POST /api/products HTTP/1.1
Host: example.com
Content-Type: application/json

{"name": "Ноутбук", "price": 50000}

Удаление товара id=7:
DELETE /api/products/7 HTTP/1.1
Host: example.com

Обновление товара id=3 (цена 45000):
PATCH /api/products/3 HTTP/1.1
Host: example.com
Content-Type: application/json

{"price": 45000}