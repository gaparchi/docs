# Входящее текстовое сообщение с URL

В данном разделе описываются поля webhook уведомления объекта `messageData` специфичные для входящего текстового сообщение с URL. Для получения описания общих полей входящих сообщений обратитесь к разделу [Входящие сообщения](/api/receiving/webhook/incoming-message/Webhook-IncomingMessageReceived). 

Для получения webhook уведомлений данного вида требуется выполнение двух условий:

`typeWebhook` = `incomingMessageReceived`

`messageData.typeMessage` = `extendedTextMessage`

## Webhook {#webhook}

### Поля webhook {#webhook-parameters}

Поля объекта `messageData`

Параметр | Тип | Описание
----- | ----- | -----
`typeMessage` | **string** | Тип принятого сообщения. Для сообщений данного типа поле принимает значение `extendedTextMessage`
`extendedTextMessageData` | **object** | Объект данных о принятой ссылке с метаданными

Поля объекта `extendedTextMessageData`

Параметр | Тип | Описание
----- | ----- | -----
`text` | **string** | Текст ссылки
`description` | **string** | Описание ссылки
`title` | **string** | Заголовок ссылки
`previewType` | **string** | Тип превью ссылки
`jpegThumbnail` | **string** | Превью изображения в `base64` кодировке

### Пример тела webhook {#webhook-example-body}

```json
{
    "typeWebhook": "incomingMessageReceived",
    "instanceData": {
        "idInstance": 1234,
        "wid": "79001234567@c.us",
        "typeInstance": "whatsapp"
    },
    "timestamp": 1588091580,
    "idMessage": "F7AEC1B7086ECDC7E6E45923F5EDB825",
    "senderData": {
        "chatId": "79001234568@c.us",
        "sender": "79001234568@c.us",
        "senderName": "Green API"
    },
    "messageData": {
        "typeMessage": "extendedTextMessage",
        "extendedTextMessageData": {
            "text": "https://www.youtube.com/xxxxxxxxxxxxxxxxxxx",
            "description": "Green API docs shows how you can develop the WhatsApp bot",
            "title": "How to develop WhatsApp bot",
            "previewType": "video",
            "jpegThumbnail": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAYEBQYFBAYGBQYHBwYIChAKCgkJChQODwwQFxQYG=="
        }
    }
}
```