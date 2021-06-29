---
title : "Внутренняя архитектура"
description : ""
weight : 5
---

![Архитектура приложения](/SC_Lite/desc/scl_internal.png)

Приложение Protei_CAPL состоит из следующих подсистем:
- [модуль CPM](#cpm) - модуль центрального процессора;
- [модуль TSP](#tsp) - телекоммуникационная периферия;
- [модуль SIM](#sim) - модуль контроля.

Модули конструктивно выполнены в виде стандартных плат половинного размера
конструктива ISA, объединенных кросс–платой. Вместе с источником питания PS и панелью индикации модули устанавливаются в общем корпусе.

В состав системы может входить модем для дистанционного управления и технического обслуживания по коммутируемой телефонной линии.

### <a name="cpm">Модуль CPM</a>

Модуль CPM является устройством управления и представляет собой одноплатный IBM–совместимый компьютер для промышленного применения. Устройство содержит процессор уровня Pentium II, оперативную память, Flash–память для ПО емкостью 64Мб.

Модуль CPM контролирует выполнение всех функций роумингового брокера под управлением резидентного программного обеспечения, хранящегося во Flash–памяти.

### <a name="tsp">Модуль TSP</a>

Модуль TSP состоит из нескольких узлов:

- схем интерфейса Е1;
- системы коммутации;
- контроллера HDLC;
- генератора сигналов синхронизации;
- цифровых сигнальных процессоров;
- интерфейса с системной шиной.

![Схема модуля TSP](/SC_Lite/desc/scl_tsp.png)

Схемы интерфейса Е1 построены на БИС, которые осуществляют поддержку обмена по ИКМ–тракту.

Функции:

- синхронизация потоков с привязкой их к импульсам синхронизации системы, с использованием внутренней буферной памяти разговорных каналов;
- выделение и формирование в потоке канала синхронизации, 0 – канал, и формирование импульсов тактовой частоты приема для внешних схем синхронизации;
- выделение сигнальных каналов и передача их в HDLC–обработчик;
- автоматическая обработка аварийных ситуаций и подсчет ошибок;
- выполнение различных режимов тестирования схемы, задаваемых программно.

Управление БИС осуществляется программно центральным процессором по шине.

Программа осуществляет инициализацию БИС для работы в требуемом режиме и контроль за состояниями ИКМ–тракта путем обмена информацией с внутренними регистрами БИС.

Система коммутации построена на основе БИС и выполняет функции пространственно–временной коммутации каналов в потоках.

Контроллер HDLC осуществляет обмены HDLC–пакетами в каналах ИКМ–трактов.

Генератор сигналов синхронизации формирует тактирующие и синхронизирующие сигналы, необходимые для функционирования системы.

Петля цифровой фазовой автоподстройки частоты обеспечивает подстройку частоты системных синхросигналов. Автоподстройка обеспечивается в диапазоне ±100х10^(–6) в зависимости от частоты, выделяемой схемами интерфейса Е1 из входных потоков ИКМ. При этом осуществляется фильтрация быстрых колебаний опорного сигнала.

Цифровые сигнальные процессоры осуществляют обработку и генерацию акустических сигналов и осуществляют поддержку обмена HDLC–пакетами в сигнальных каналах ИКМ–трактов.

### <a name="sim">Модуль SIM</a>

Модуль SIM служит для контроля за работой модуля центрального процессора.

Модуль SIM содержит два устройства:

- монитор напряжения питания +5В;
- сторожевой таймер Watchdog.

Также модуль выполняет функции управления светодиодами на панели индикации по командам центрального процессора.

Сторожевой таймер используется для защиты устройства управления и всей системы от зависания и сбоев. Он отслеживает проблемы в работе процессора и перезапускает процессор.

Различные помехи могут возникать в результате скачков напряжения в сети питания. В случае, когда такого рода помехи сказываются на стабильности напряжения питания электронных схем +5В, схема монитора напряжения питания производит перезапуск процессора. Перезапуск гарантирует нормальное функционирование системы, даже если помеха вызвала сбой схемы сторожевого таймера.