```asterisk
[recall]
exten => _1XXX,1,NoOp(Звонок распределился на внутренний номер ${recall})
	same => n,Set(CDR(userfield)=from_1c: ${EXTEN})
    ;same => n,Set(GLOBAL(RINGTIMER)=10)
    ;В макросе macro-exten-vm идет проверка па параметрам и задается переменная RINGTIMER, которая указывает сколько секунд звонить на внутренний номер
    ;прежде, чем перевести звонок в очередь. И т.к наследуется много переменных, RINGTIMER явно указана здесь
    same => n,Set(RINGTIMER=10)
    same => n,NoOp(Глобальная переменная RINGTIMER равна: ${RINGTIMER})
	same => n,Macro(exten-vm,novm,${recall},1,1,1)
    same => n,NoOp(Dialstatus для звонка равен: ${DIALSTATUS})
    same => n,GotoIf($["${DIALSTATUS}" = "BUSY" | "${DIALSTATUS}" = "NOANSWER"]?${EXTEN_QUEUE},1)
    same => n,Hangup()

;Сначала в Custom destination и направляем звонок в очередь, но если 1с или любой другой API найдет свободного оператора, то звонок направится ему, а если он не отвечает то уходит дальше в очередь
exten => _90[02]X,1,NoOp(Отслеживание звонка на очередь или внутренний номер)
	same => n,GotoIf($["${EXTEN_QUEUE}" != ""]?gotoqueue)
	same => n,Set(EXTEN_QUEUE=${EXTEN})
    same => n,NoOp(CustomDestination передал очередь: ${EXTEN_QUEUE})
    same => n,AGI(/var/lib/asterisk/agi-bin/1c_check.sh,8${CALLERID(num):-10:10},${IF($["${CALLERID(rdnis)}" != ""]?${CALLERID(rdnis)}:${CALLERID(dnid)})})
    same => n,NoOp(Найденный внутренний номер для вызова: ${recall})
    same => n,GotoIf($["${recall}" != "" & "${EXTENSION_STATE(${recall}@ext-local)}" = "NOT_INUSE"]?${recall},1)
	same => n(gotoqueue),Goto(ext-queues,${EXTEN_QUEUE},1)
    same => n,Hangup()

exten => h,1,Hangup()
```