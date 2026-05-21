Trunk:
```asterisk
[RobovoiceTrunk1]
disallow=all
type=friend
username=RobovoiceTrunk1
secret=****
context=from-robovoice
canreinvite=no
allow=ulaw,alaw,gsm
host=dynamic
directmedia=no
insecure=invite,port
nat=force_rport,comedia
qualify=yes
qualifyfreq=60
```

Context:
```asterisk
[from-robovoice]
exten => _7XXXXXXXXXX/RobovoiceTrunk1,1,NoOp(From RobovoiceTrunk1 to ${EXTEN})
  same => n,Gosub(sub-record-check,s,1(out,${EXTEN},force))
  same => n,Dial(SIP/trunk_provider_name1/${EXTEN},50,Tb(func-apply-sipheaders^s^1,(2)))
  same => n,Hangup()

exten => _7XXXXXXXXXX/RobovoiceTrunk2,1,NoOp(From RobovoiceTrunk2 to ${EXTEN})
  same => n,Gosub(sub-record-check,s,1(out,${EXTEN},force))
  same => n,Dial(SIP/trunk_provider_name2/${EXTEN},50,Tb(func-apply-sipheaders^s^1,(2)))
  same => n,Hangup()

exten => 500,1,NoOp(From robovoice to QUEUE 500)
  same => n,Answer()
  same => n,Goto(ext-queues,500,1)
  same => n,Hangup()

exten => _.,1,NoOp(From robovoice to other call. Its block. EXT: ${EXTEN})
 	same => n,DumpChan(8)
	same => n,Hangup()

exten => h,1,NoOp(From robovoice hangup. Call to ${EXTEN})
  same => n,DumpChan(8)
  same => n,Hangup()
```