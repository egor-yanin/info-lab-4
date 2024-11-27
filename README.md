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

Затем я запустил контейнер с именем container1 на основе образа latest

```bash
sudo docker run --name container1 -it latest
```
