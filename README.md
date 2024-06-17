# Message Queue Projects/Configurations
## Goal
Demonstrate different message queue configurations containing **one** queue manager and its functions

## Environment
* VM: Virtual Machine Manager
* Operating System: REHL 8.9
* Message queue version: IBM MQ 9.3.4.0
* mqm user is system administrator
* IBMQ Installtion path: /opt/mqm
* Data path: /var/mqm

## Configuration 1
### Setup:

* File related: QM.mqsc
* One Queue manager: QM
* One local queue: LQ.QM
* Listener: MQ1414 (Port:1414)

### How to use/run:
Under mqm(System Admin) user Create a queue manager called 'QM'
```script
$ crtmqm -lc -lp 10 -ls 5 -lf 8196 -u SYSTEM.DEAD.LETTER.QUEUE QM
```

Start the queue manager 'QM'
```script
$ strmqm QM
```

Import the QM.mqsc file in the queue manger 'QM'

``` script
$ runmqsc QM < /PATH/LOCATION/OF/QM.mqsc
```

Start the listener
``` script
$ runmqsc QM
START LISTENER(MQ1414)
```

### Local Binding:
Change to a user that is not mqm
Put message
```script
$ amqsput <Local_Queue_Name> <Queue_Manager_Name>
$ amqsput LQ.QM QM
```

Get message
```script
$ amqsget <Local_Queue_Name> <Queue_Manager_Name>
$ amqsget LQ.QM QM
```

### Local Binding Diagram

### Client Binding:
Change to a user that is not mqm
Change environment variable: 
```script
$ export MQSERVER="QMSVRCONN/TCP/localhost(1414)"
```
Put message
```script
$ amqsputc <Local_Queue_Name> <Queue_Manager_Name>
$ amqsputc LQ.QM QM
```
Get message
```script
$ amqsgetc <Local_Queue_Name> <Queue_Manager_Name>
$ amqsgetc LQ.QM QM
```

### Client Binding Diagram

## Configuration 2

## Configuration 3

## Configuration 4
