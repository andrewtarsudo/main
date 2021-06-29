---
title : "Статистика принятых USSD-сообщений"
description : ""
weight : 1
---

Идентификатор журнала в файле *trace.cfg* - statussd.
Формат названия файла: statussd–YYYYMMDD–hhmm.log.
YYYYMMDD-hhmm - дата и время начала сбора статистики.

### Формат записи:

DateTime; StatType; Start_stat_time; MSISDN; SuccessCount; MsgTypeCount;

### Описание полей

1. DateTime - Дата и время формирования записи.
2. StatType - Имя статистики. Возможные значения: USSD МО/USSD МТ.
3. Start_stat_time - Время начала сбора статистики. Формат: YYYY–MM–DD hh:mm:ss.
4. MSISDN - Номер, для которого ведется статистика по времени.<br>
**Примечание.** Если значение не задано, то используются два предопределенных номера:
* total - статистика по вcем номерам за период;
* start - статистика по всем номерам с момента старта системы.
5. SuccessCount - Количество успешно обработанных SMS–сообщений.<br>
**Примечание.** Поле может отображаться в формате:<br>
#successUssd|#currentRate|#maxRate;<br>
* successUssd - количество успешно обработанных USSD–сообщений;
* currentRate - текущая производительность;
* maxRate - максимальная производительность за этот период.<br>
6. MsgTypeCount - Количество USSD–сообщений, приходящихся на каждую определенную ошибку из 13 возможных.