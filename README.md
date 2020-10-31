# Demo of using nameko with microservices in Python 3.8
Based on Rocha's material: http://brunorocha.org/python/microservices-with-python-rabbitmq-and-nameko.html

## Commands for setting the environment:
```
$ docker run -d --hostname my-rabbit --name some-rabbit -p 15672:15672 -p 5672:5672 rabbitmq:3-management
$ mkdir myproject
$ cd myproject
$ pip install virtualenv
$ virtualenv service_env
$ .\service_env\Scripts\activate
(service_env)$ pip install nameko
(service_env)$ pip install yagmail
```
## Commands to perform the services:
```
(service_env)$ nameko run service --broker amqp://guest:guest@localhost
```
## Commands for running the application(another command prompt):
```
$ .\service_env\Scripts\activate
(service_env)$ nameko shell --broker amqp://guest:guest@localhost
>>> n.rpc.mail.send("xxxx@xxxx.com", "testing", "Just testing")
>>> n.rpc.compute.compute('sum', 30, 10, "xxxxx@xxxx.com")
```

It is necessary to fill the email in the service.py file