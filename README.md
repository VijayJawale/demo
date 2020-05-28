## Notification Service
Notification service for Stock Trader application will subscribe to RabbitMq for the messages sentfrom the Portfolio service, when user perfroms the operations like 
* Create Portfolio
* Update Portfolio -add stcok
* Delete Portfolio
Then the notification service will publish these message to IBM cloud push notification service.

## Building

`mvn clean install` To package and create application executable jar

`docker build -t stocktrader/notifications .` To creta the docker image from the jar file

### example run cmd

` docker run  -e MQ_USR=user -e MQ_PWD=bitnami -e MQ_VIRTUAL_HOST=/ -e MQ_HOST_NAME=172.17.76.28 -e MQ_PORT=5672 -e MQ_QUEUE=TESTQ -e server.port=8888 -e TENANT_ID=77955822-7290-4cd9-b80a-3091b6892fe8  -e API_KEY_ID=52XE_c9OkJJ6NfHDjTXxrYWcUUph86mwOLIZXyGlY2aA  -e REGION=.us-east.bluemix.net  -e TAG_NAME=Notifications-VJ -e ALERT_MSG_URL=www.ibm.com stocktrader/notifications`    


## Configuration

The application/container expects the following environment variables to be populated and carry configuration forthe application.

| Env Var | Purpose |
|---------|---------|
|`MQ_USR` | The rabbitmq user name . eg. `user`|
|`MQ_PWD` | The rabbitmq password . eg. `bitnami`|
|`MQ_VIRTUAL_HOST` | The rabbitmq virtual host . eg.(default) `/`|
|`MQ_HOST_NAME` | The rabbitmq host name or ip address . eg. `http://myrabbitmq.local`|
|`MQ_PORT` | The rabbitmq port . eg. `5672`|
|`MQ_QUEUE` | The rabbitmq queue name . eg. `TESTQ`|
|`TENANT_ID` | The api guuid of the IBM cloud  push notification service . eg. `user`|
|`API_KEY_ID` | The api key from the credentials of the IBM cloud  push notification service . eg. `52XE_c9OkJJ6NfHDjTXxrYWcUUph86mwOLIZXyGlYaaa`|
|`REGION` | The region of IBM cloud push notification service . eg. `.us-east.bluemix.net`|
|`TAG_NAME` | The tag for push notifiaction message  . eg. `user`|
|`ALERT_MSG_URL` | The URL to be sent with push notifiaction alert . eg. `www.ibm.com` |

