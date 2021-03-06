# API сервиса организации встреч
API реализует функции создание, удаление и изменение объектов сервиса

## Основные объекты
- Пользователь (таблица `user`)
- Встреча (таблица `meeting`)
  - Расписание встречи (таблица `schedule`)
  - Вопросы анкеты для регистрации на встречу (таблица `question`)
- Организатор встречи (таблица `organizer`)
- Участник встречи (таблица `visitor`)
  - Ответы на вопросы анкеты встречи (таблица `answer`)

[ссылка на структуру бд](https://drive.google.com/file/d/1a-PT8_bB9P_0Y4-xweLbE5hc2bcfPStW/view?usp=sharing)
## Сценарий использования
Для участия в мероприятиях и создания собственных необходима регистрация в системе (`/user/register`). Для авторизации в системе в качестве логина в системе используется `email` адрес пользователя (`/user/login`, `/user/logout`)

Далее пользователь может просматривать и менять свои настройки (`/user/{email}`), создавать новые мероприятия и просматривать их список (`/user/meeting`), просматривать параметры мероприятий, менять их параметры и удалять их (`/user/meeting/{id}`)

Так же пользователь может указать или убрать соорганизатора встречи (`/user/meeting/{id}/organizer/{email}`)

Для настройки регистрации на мероприятия доступно создание анкет с вопросами (`/user/meeting/{id}/question`, `/user/meeting/{id}/question/{id}`)

В качестве посетителя пользователь может:
- просматривать список открытых мероприятий (`/meeting`)
- просматривать параметры мероприятий (`/meeting/{id}`)
- зарегистрироваться на мероприятие, ответив на необходимые вопросы (`/meeting/{id}/signup`)
- отказаться от участия в мероприятии (`/meeting/{id}/reject`)
- просмотреть список мероприятий на которые он подписался (`/meeting?show=signed`)

## Функции API
- __POST__ `/user/register`
- __POST__ `/user/login`
- __GET__ `/user/logout`
- __GET__|__PATCH__ `/user/{email}`
- __GET__|__POST__ `/user/meeting`
- __GET__|__PATCH__|__DELETE__ `/user/meeting/{id}`
- __GET__|__POST__ `/user/meeting/{id}/schedule`
- __GET__|__PATCH__|__DELETE__ `/user/meeting/{id}/schedule/{id}`
- __GET__ `/user/meeting/{id}/organizer`
- __POST__|__DELETE__ `/user/meeting/{id}/organizer/{email}`
- __GET__|__POST__ `/user/meeting/{id}/question`
- __PATCH__|__DELETE__ `/user/meeting/{id}/question/{id}`
- __GET__ `/user/meeting/{id}/visitor`
- __GET__ `/user/meeting/{id}/visitor/{id}`
- __GET__ `/meeting`
- __GET__ `/meeting/{id}`
- __POST__ `/meeting/{id}/signup`
- __DELETE__(?) `/meeting/{id}/reject`


## Расширенные функции
- Отправка уведомлений о начале мероприятия
  - По почте
  - В telegram
  - СМС
  - ...
- Добавление мероприятия в календарь
- Указание адреса проведения мероприятия на картах
- Telegram бот для регистрации в системе и на мероприятия
- Формирование бэджа участника
- Платные встречи
- ...
