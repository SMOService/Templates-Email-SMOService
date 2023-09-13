# Email Templates by SMOSERVICE

Этот репозиторий содержит набор оптимизированных шаблонов электронных писем для сайта [smoservice.net](https://smoservice.net) и [smoservice.biz](https://smoservice.biz).

## Содержание

- 5 улучшенных шаблонов электронных писем.
- Код для генерации композиций на основе текста.

## Особенности

1. **Мобильная оптимизация**: Шаблоны писем были оптимизированы для отображения на мобильных устройствах.
2. **Оптимизация стилей**: Дублирующиеся стили были заменены на классы для уменьшения размера и упрощения поддержки.

## API Документация

### Подключение API

#### Общая информация

- Получить API ключ вы можете в личном кабинете.
- Все запросы отправляются как Form data методом POST на адрес - `https://smoservice.media/api/`

#### Пример запроса для CURL:

```bash
curl --location --request POST 'https://smoservice.media/api/' \
--form 'action=balance' \
--form 'user_id=123' \
--form 'api_key=123123123xx123123123'
```

#### Список методов:

- Баланс
- Список услуг
- Создание заказа
- Проверка заказа

##### Получение баланса

Запрос:

```plaintext
user_id   10322
api_key   345E138109F67E2F843BBEF1B4D428A0
action    balance
```

Ответ:

```json
{
"type": "success",
"desc": "Balance info",
"data": {
"balance": "14625.36"
}
}
```

##### Список услуг

Запрос:

```plaintext
user_id   10322
api_key   345E138109F67E2F843BBEF1B4D428A0
action    services
```

Ответ:

```json
{
"type": "success",
"desc": "Service list",
"data": [
{
"id": "805",
"name": "Просмотры на видео (стандартные с удержанием)",
"min": "1000",
"max": "10000000",
"price": "0.35",
"code": "yt-views-retention"
},
{
"id": "807",
"name": "Просмотры на видео (стандартные)",
"min": "1000",
"max": "1000000",
"price": "0.33",
"code": "yt-views-standart"
}
]
}
```

##### Создание заказа

Запрос:

```plaintext
user_id      10322
api_key      345E138109F67E2F843BBEF1B4D428A0
action       create_order
service_id   807       (ID услуги)
count        3500      (Количество)
url          https://www.youtube.com/user/smoserviceru (URL заказа)
```

Ответ:

```json
{
"type": "success",
"desc": "Order info",
"data": {
"order_id": "17",
"price": "45.33"
}
}
```

##### Проверка заказа

Запрос:

```plaintext
user_id   10322
api_key   345E138109F67E2F843BBEF1B4D428A0
action    check_order
order_id  17          (ID заказа)
```

Ответ:

```json
{
"type": "success",
"desc": "Order status",
"data": {
"order_id": "17",
"status": "completed"
}
}
```

---
