# events4friends-firestore - описание базы данных

Данные сайта хранятся в firebase. Основой сайта являются услуги и анонсы мероприятий. 

## Анонс

Коллекция [events](https://console.firebase.google.com/u/0/project/events4friends/firestore/data~2Fevents)

Мероприятия создаются организаторами:

| поле        | тип    | обязательно | описание                                                                       |
| ----------- | ------ | ----------- | ------------------------------------------------------------------------------ |
| id          | строка | да          | уникальный идентификатор                                                       |
| summary     | строка | да          | короткое название мероприятия                                                  |
| description | текст  | да          | полное описание                                                                |
| isOnline    | булево | да          | true - онлайн, false - офлайн                                                  |
| location    | строка | да          | адрес мероприятия/ссылка мероприятия                                           |
| contact     | строка | да          | контакт организатора                                                           |
| name        | строка | да          | имя организатора                                                               |
| timezone    | строка | да          | часовой пояс может принимать значения '+0200'(Калининград) или '+0300'(Москва) |
| start       | строка | да          | начало, dateTime, например "2019-09-14T11:00:00", ISO-8601                     |
| end         | строка | нет         | конец, dateTime                                                                |

## Услуга

Коллекция [services](https://console.firebase.google.com/u/0/project/events4friends/firestore/data~2Fservices)

Услуги предоставляю участники сообщества:

| поле        | тип    | обязательно | описание                                        |
| ----------- | ------ | ----------- | ----------------------------------------------- |
| id          | строка | да          | уникальный идентификатор                        |
| name        | строка | да          | имя того, кто оказывает услугу (обычно человек) |
| service     | текст  | да          | название услуги                                 |
| description | текст  | да          | полное описание услуги                          |
| isFree      | булево | нет         | true - услуга оказывается безоплатно            |
| instagram   | текст  | нет         | ссылка на инстаграм                             |
| website     | текст  | нет         | ссылка на сайт                                  |
| price       | число  | нет         | цена в рублях                                   |
| whatsapp    | текст  | нет         | номер в вотсапп в формате 7XXXXXXXXXX           |
| telegram    | текст  | нет         | id пользователя в телеграм                      |
| vkontakte   | текст  | нет         | ссылка на вконтакте                             |
| phone       | текст  | нет         | номер телефона в формате +7XXXXXXXXXX           |

## Идентификаторы закрепленных сообщений

В чатах месседжера Telergam можно закрепить сообщение. Эта коллекция управляется только с помощью Телеграм-бота @events4friendsbot.

Коллекция - [pinnedMessages](https://console.firebase.google.com/u/0/project/events4friends/firestore/data~2FpinnedMessages)

| поле        | тип    | обязательно | описание                                                                       |
| ----------- | ------ | ----------- | ------------------------------------------------------------------------------ |
| communityId   | число | да          | идентификатор сообщества                                                       |
| chatName     | string | да          | ник телеграм чата                                                  |
| pinnedMessageId | число  | нет          | Id закрепленного сообщения                                          |
| date    | строка | да          | дата, когда сообщение было закреплено, например "2019-09-14", ISO-8601.    |

Так как пока реализовано только одно сообщество communityId всегда равно 1

## Push-уведомления мобильных приложений

Уведомления работаею для iOS и Android.

Коллекция - [reminder](https://console.firebase.google.com/u/0/project/events4friends/firestore/data~2Freminders)

| поле        | тип    | обязательно | описание                                                                       |
| ----------- | ------ | ----------- | ------------------------------------------------------------------------------ |
| eventId   | string | да          | идентификатор анонса мероприятия                                                 |
| expoPushToken     | string | да          | Токен для (уведомлений expo)[https://docs.expo.io/push-notifications/overview/]                                               |
| value | boolean  | да          | Уведомление может быть "включено" или "выключено"                                  |

## Конфигурация

Это - служебная таблица. Пока содержит Только номер версии. Используется только в проекте сайта [events4friends.ru-react](https://github.com/VadimCpp/events4friends.ru-react)

Коллекция - [config](https://console.firebase.google.com/u/0/project/events4friends/firestore/data~2Fconfig~2Fgeneral)

| поле        | тип    | обязательно | описание                                                                       |
| ----------- | ------ | ----------- | ------------------------------------------------------------------------------ |
| version | string  | да          | Версия изменений софта                                   |
