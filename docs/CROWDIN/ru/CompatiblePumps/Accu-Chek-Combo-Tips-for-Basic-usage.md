# Советы для пользователей Accu-Chek Combo

**NOTE:** Starting with AAPS version 3.2, a [new Combo driver](../CompatiblePumps/Accu-Chek-Combo-Pump-v2.md) (referred to as "combov2" sometimes) has been added. Старый драйвер также называется "драйвер, основанный на Ruffy. Некоторые части этого документа относятся только к старому драйверу. Они будут соответствующим образом аннотированы.

## Как обеспечить бесперебойную работу

* Всегда ** носите смартфон с собой **, оставляя его рядом с кроватью ночью. Так как помпа может оказаться за или под вами во время сна, лучше всего оставлять ее где-то повыше (на полке).
* Всегда убеждайтесь, что батарея помпы максимально заряжена. Информацию о батарее смотрите в разделе подсказок по использованию батареи.

* (Относится только к старому драйверу) Лучше всего ** не трогать приложению ruffy ** во время работы системы. Если приложение запускается заново, соединение с помпой может прерваться. Как только помпа соединится с ruffy, нет необходимости в повторном подключении. Даже после перезапуска телефона соединение восстанавливается автоматически. По возможности переместите приложение на неиспользуемый экран или папку на смартфоне, чтобы случайно его не открыть.

* (Относится только к старому драйверу) Если вы непреднамеренно откроете приложение во время работы цикла, лучше сразу же перезапустить смартфон.
* Всякий раз, когда это возможно, управляйте помпой с помощью приложения AAPS. Для этого активируйте блокировку кнопок на помпе в ** PUMP SETTINGS/KEY LOCK/ON **. Кнопками помпы следует пользоваться только при замене батареи или картриджа. 

![Блокировка клавиш](../images/combo/combo-tips-keylock.png)

## Помпа недоступна. Что делать?

### Активируйте сигнализацию "помпа недоступна"

* В AAPS перейдите в ** Настройки/Локальные оповещения **, активируйте ** оповещение при недоступности помпы ** и задайте для него лимит **помпа недоступна [Min]** до ** 31 ** минут.
* Это даст вам достаточно времени, чтобы не активировать сигнал при выходе из помещения, пока телефон останется на столе, но информирует вас, если помпа будет недоступна на время, превышающее длительность временного базала.

### Восстановление доступности помпы

* Когда AAPS сообщает о том, что **помпа недоступна** разблокируйте кнопки помпы и ** нажмите на любую кнопку ** (например, "вниз"). Как только экран помпы отключится, нажмите кнопку ** ОБНОВИТЬ** на вкладке ** СOMBO ** в AAPS. В большинстве случаев связь с помпой восстанавливается.
* Если это не поможет, перезагрузите смартфон. После перезапуска, AAPS и ruffy будут реактивированы, и с помпой будет установлено новое соединение. Если вы используете старый драйвер, то ruffy также будет активирован.

* Тесты с разными телефонами показали, что некоторые из них запускают ошибку "помпа недоступна" чаще, чем другие. В разделе [ Телефоны для AAPS ](https://docs.google.com/spreadsheets/d/1gZAsN6f0gv6tkgy9EBsYl0BQNhna0RDqA9QGycAqCQc/edit) перечислены успешно проверенные смартфоны.

### Причины и последствия частых ошибок связи

* На телефонах с ** небольшой памятью ** (или ** агрессивными параметрами экономии заряда батареи **) AAPS часто отключается. Это можно определить по тому, что кнопки Bolus и Calculator не присутствуют на главном экране при запуске AAPS, так как система инициализируется. Это может привести к оповещениям "помпа недоступна" при запуске. В поле ** недавнее соединение ** на вкладке Combo можно проверить, когда AAPS последний раз обменивался данными с помпой.

![Помпа недоступна](../images/combo/combo-tips-pump-unreachable.png)

![Нет соединения с помпой (как показано на вкладке старого драйвера)](../images/combo/combo-tips-no-connection-to-pump.png)

![Нет соединения с помпой (как показано на вкладке нового драйвера)](../images/combo/combov2-tips-no-connection-to-pump.png)

* Эта ошибка может ускорить снижение заряда батареи помпы, так как профиль базала считывается из помпы при перезапуске приложения.
* Кроме того, это увеличивает вероятность возникновения ошибки, которая заставляет помпу отклонять все входящие соединения до тех пор, пока на помпе не будет нажата кнопка. 

## Отмена временной базальной скорости не выполнена

* Иногда AAPS не может автоматически отменить оповещение ** Временная скорость базала TBR ОТМЕНЕНА **. В этом случае необходимо нажать кнопку ** ОБНОВИТЬ ** на вкладке **COMBO** или подтвердить получение сигнала на помпе.

## Особенности работы батареи помпы

### Замена батареи

* После сигнала оповещения ** низкий заряд батареи ** батарея должна быть заменена как можно скорее, чтобы всегда иметь достаточно энергии для надежной связи Bluetooth со смартфоном, даже на большом удалении от помпы.
* Даже после оповещения ** низкий заряд батареи ** батарея может прослужить еще значительное время. Тем не менее, рекомендуется всегда иметь с собой свежую батарею после оповещения "низкий заряд".
* Перед заменой батареи, нажмите на символ **Цикл** на главном экране и выберите **приостановить цикл на 1ч**. 
* Подождите, пока помпа завершит обмен с телефоном и исчезнет логотип Bluetooth на помпе.

![Bluetooth включен](../images/combo/combo-tips-compo.png)

* Разблокируйте кнопки на помпе, переведите ее в режим остановки, подтвердите возможно отмененный временный базал, и замените батарею.
* При использовании старого драйвера, если время на помпе не сохранилось при замене батареи, переустановите дату и время помпы в точности с датой/временем телефона, на котором работает AAPS. (Новый драйвер автоматически обновляет дату и время помпы)
* Затем переведите помпу в рабочий режим и выберите ** Возобновить ** при длинном нажатии на ** Приостановлено ** на главном экране.
* AAPS возобновит подачу необходимого временного базала с получением следующего значения ГК.

(Accu-Chek-Combo-Tips-for-Basic-usage-аккумулятор-тип и причинно-следственная связь аккумулятора)=

### Типы батарей и причины их короткой жизни

* Поскольку интенсивная связь Bluetooth потребляет много энергии, пользуйтесь только ** высококачественными батареями **, такими как Energizer Ultimate Lithium, Power One" из "большого" сервисного набора Accu-Chek, или, если вы собираетесь пользоваться перезаряжаемым аккумулятором, используйте аккумуляторы Eneloop. 

![Energizer](../images/combo/combo-tips-energizer.jpg) ![OnePower](../images/combo/combo-tips-power-one.png)

Диапазоны времени жизни различных типов батарей:

* **Energizer Ultimate Lithium**: от 4 до 7 недель
* ** Power One Alkaline ** (Varta) из сервисного набора: 2-4 недели
* Перезаряжаемые батареи ** Eenlook ** (BK-3MCCE): от 1 до 3 недель

Если срок службы батареи значительно короче указанных выше диапазонов, проверьте следующие возможные причины:

* (Относится только к старому драйверу) Версия после марта 2018 года приложения ruffy значительно улучшила время работы батареи помпы. Убедитесь, что у вас самая свежая версия ruffy, если есть проблемы с коротким сроком жизни батареи.
* Есть некоторые варианты закручивающегося колпачка батарейного отсека помпы Combo, которые частично замыкают батарейку и быстро ее истощают. Колпачки без этой проблемы можно узнать по золотым металлическим контактам.
* Если часы помпы не "выдерживают" быстрой замены батареи, то, скорее всего, сломался конденсатор, который поддерживает работу часов во время краткочного отключения питания. В этом случае поможет только замена помпы Roche, что не является проблемой в течение гарантийного срока. 
* Аппаратное и программное обеспечение смартфона (операционная система Android и модуль Bluetooth) также влияют на время работы батареи помпы, хотя точные факторы пока неясны. Если у вас есть возможность, попробуйте другой телефон и сравните время жизни батареи.

## Изменение сезонного времени

**ПРИМЕЧАНИЕ**: Новый драйвер автоматически устанавливает дату и время и самостоятельно обрабатывает переход на сезонное время. Все шаги ниже относятся только к старому драйверу.

* В настоящее время драйвер combo не поддерживает автоматическую корректировку времени помпы.
* В течение ночи перехода на летнее/зимнее время смартфон обновляется, но время на часах помпы остается неизменным. Это приводит к срабатыванию оповещения из-за разницы времени между системами в 3 часа утра.
* Если вы не хотите просыпаться ночью, ** деактивируйте автоматический переход на летнее время на мобильном телефоне ** вечером перед переходом и скорректируйте время вручную на следующее утро. Хороший способ решения вопроса о перееходе времени - переключиться на другой часовой пояс, расположенный на вашей же долготе, но ближе к экватору, где обычно не применяют переход на летнее/зимнее время. Пример: Для Центральной Европы летнее время (CEST/GMT+2), в ночь перед переходом на зимнее время можно переключиться на часовой пояс Зимбабве, а затем на следующее утро вернуться к центральноевропейскому времени CET/GMT+1 при одновременной смене времени на помпе. The other way around, switch to the time zone of Nigeria while on Winter Time CET/GMT+1 and go back to Central European Summer Time (CEST/GMT+2) the morning after the switch to summer time and change the pump time accordingly. Чтобы найти подходящую страну, смотрите здесь https://www.timeanddate.com/time/map/,.

## Пролонгированный болюс, многоволновый болюс

Алгоритм OpenAPS не поддерживает параллельное выполнение пролонгированного болюса или многоволнового болюса. Однако аналогичного результата можно достичь с помощью следующего:

* Используйте **e-Carbs** при занесении углеводов или использовании калькулятора путем ввода всех углеводов целого блюда и расчетного времени их поступления в кровь в виде глюкозы. Затем система вычислит мелкие углеводы, равномерно распределенные на всю продолжительность, что приведет к тому, что алгоритм обеспечит эквивалентную дозировку инсулина, при этом постоянно проверяя общее увеличение/снижение уровня глюкозы в крови. For a multiwave bolus approach, you can also combine a smaller immediate bolus with e-carbs. 
* Перед едой на вкладке **Действия** в AAPS установить временную цель **Ожидаемый прием пищи**с целевой ГК 80 (4,5) на несколько часов. Продолжительность должна основываться на интервале, который вы выбрали бы для пролонгированного болюса. This will keep your target lower than usual and therefore increase the amount of insulin delivered.
* Затем воспользуйтесь **Калькулятором** и введите общее количество принимаемых углеводов, но непосредственно не применяйте значения, предлагаемые калькулятором болюса. Если предполагается болюс двойной волны, снизьте дозировку инсулина. Чтобы противодействовать росту ГК, в зависимости от пищи, алгоритм обеспечит дополнительные микроболюсы SMB или более высокую временную скорость базала. В данном случае ограничение безопасности для базала должно быть тщательно изучено и, при необходимости, временно изменено.

* Если вы соблазнились просто использовать пролонгированный или многоволновый болюс непосредственно на помпе, AAPS накажет вас отключением замкнутого цикла на следующие шесть часов, чтобы убедиться, что отсутствует избыток подачи инсулина.

![Отключение цикла после многоволнового болюса](../images/combo/combo-tips-multiwave-bolus.png)

## Сигналы оповещений при введении болюса

* Если AAPS обнаружит, что идентичные болюсы были успешно введены в одну и ту же минуту, то подача болюса с одним и тем же количеством единиц инсулина будет предотвращена. If your really want to bolus the same insulin twice in short succession, just wait two more minutes and then deliver the bolus again. If the fist bolus has been interrupted or was not delivered for other reasons, you can immediately re-submit the bolus since AAPS 2.0.
* Такое оповещение есть механизм безопасности, который считывает историю помпы, прежде чем подавать новый болюс, чтобы правильно вычислить активный инсулин IOB, даже когда болюс подается непосредственно с помпы. Он не позволяет неразличимые записи.

![Двойной болюс](../images/combo/combo-tips-doppelbolus.png)

* Этот механизм также предотвращает другую причину ошибок: если во время использования калькулятора болюса с помпы подается другой болюс и тем самым меняется история болюсов, то основа расчета болюса становится неверной, и болюс отменяется. 

![Отмена болюса](../images/combo/combo-tips-history-changed.png)