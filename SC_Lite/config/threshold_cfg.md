---
title : "threshold.cfg"
description : "Файл настройки порогов аварийной индикации"
weight : 3
---

В файле настраиваются пороговые значения для активации и снятия аварий.

Ключ для reload - **reload threshold.cfg**.

## Описание параметров
|Name|Description|Type|Default|O/M|P/R|Version|
|:---|:----------|:---|:------|:--|:--|:------|
|**[HandlersAlarms]**||
|MaxBusyHandlers|Максимальное количество занятых логик SL, при котором активируется авария OVRLOAD.|int|0.9\*[Handlers](/Protei_SCL/docs/common/config/gsm_cfg/#handlers)|O|R||
|NormalBusyHandlers|Максимальное количество занятых логик SL, при котором снимается авария OVRLOAD.|int|0.8\*MaxBusyHandlers|O|R||
|**[QueueAlarms]**||
|MaxQueueSize|Максимальная длина очереди примитивов, при котором активируется авария OVRLOAD.|int|0.1\*[Handlers](/Protei_SCL/docs/common/config/gsm_cfg/#handlers)|O|R||
|NormalQueueSize|Максимальная длина очереди примитивов, при котором снимается авария OVRLOAD.|int|0.8\*MaxQueueSize|O|R||
|**[TcapAlarms]**||
|InThreshold|Аварийный порог входящего трафика.<br>**Примечание.** При значении 0 авария не используется.|int||O|R||
|OutThreshold|Аварийный порог исходящего трафика.<br>**Примечание.** При значении 0 авария не используется.|int||O|R||
|TotalThreshold|Аварийный порог суммарного трафика.<br>**Примечание.** При значении 0 авария не используется.|int||O|R||
|CheckInterval|Время до генерации аварии.|int s|1|O|R||
|CheckMultiplier|Множитель для интервала снятия аварии относительно времени до генерации.|int|1|O|R||