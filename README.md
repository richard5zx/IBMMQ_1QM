# Message Queue Projects/Configurations
## Goal
Demonstrate different message queue configurations containing 1 queue manager and its functions

## Environment
* VM: Virtual Machine Manager
* Operating System: REHL 8.9
* Message queue version: IBM MQ 9.3.4.0
* IBMQ Installtion path: /opt/mqm
* Data path: /var/mqm

## Configuration 1
* Setup:

File related: QM.mqsc

One Queue manager: QM

One local queue: LQ.QM

Listener: MQ1414 (Port:1414)

* How to use/run:
Create a queue manager called 'QM'

Run the queue manager 'QM'

Import the QM.mqsc file in the queue manger 'QM':runmqsc QM < /PATH/LOCATION/OF/QM.mqsc

Local Binding:
Put message
```script
amqsput <Local_Queue_Name> <Queue_Manager_Name>
```
Get message
```script
amqsget <Local_Queue_Name> <Queue_Manager_Name>
```

### Local Binding Diagram

Client Binding:
Change environment variable: 
```script
$ export MQSERVER="QMSVRCONN/TCP/localhost(1414)"
```
Put message
```script
$ amqsputc <Local_Queue_Name> <Queue_Manager_Name>
```
Get message
```script
$ amqsgetc <Local_Queue_Name> <Queue_Manager_Name>
```

### Client Binding Diagram

## Configuration 2

## Configuration 3

## Configuration 4
