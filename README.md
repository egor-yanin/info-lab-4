# Отчёт по лабораторной работe 4

Я создал dockerfile, в котором указал пакеты, которые необходимо установить: libaa-bin и iputils-ping, которые содержат aafire и ping соответственно.

```docker
FROM ubuntu:latest

RUN apt-get update && apt-get install -y libaa-bin iputils-ping
```

С помощью него я создал образ:

```bash
docker build -t latest .
```

Затем я запустил контейнер на основе образа latest:

![photo](https://i.ibb.co/YZT5vR6/aafire-cmd.png)

![](https://i.ibb.co/PYgjTFJ/aafire.png)

Пока работал этот контейнер, я вывел список всех контейнеров:

![aafire container](https://github.com/user-attachments/assets/536e78a0-aa79-47ef-97a4-c760d7e1192b)

Теперь нужно настроить сеть мужду двумя контейнерами. Для этого я прекратил работу aafire и создал два новых контейнера с именами container1 и container2.

![ps containers](https://github.com/user-attachments/assets/37123722-3ccc-49f0-a745-8ccdfb7aaf39)

Далее я создал сеть myNetwork и добавил в неё эти контейнеры.

```bash
docker network create myNetwork
docker network connect myNetwork mycontainer1
docker network connect myNetwork mycontainer2
```

Затем я узнал ip-адреса контейнеров в сети: 172.18.0.2 для container1 и 172.18.0.3 для container2

```bash
docker network inspect myNetwork
```

С помощью утилиты ping я проверил соединение между контейнерами.

![ping container1](https://github.com/user-attachments/assets/fcc437b1-633a-4538-8e6a-6a6f7df89328)

![ping conrtainer2](https://github.com/user-attachments/assets/e6bef5a2-4267-4a02-8b1a-49219edb6f95)
