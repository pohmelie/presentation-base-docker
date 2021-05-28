# Docker overview

---

# Зачем нужны контейнеры?

---

# Зачем нужны контейнеры?

- Доставка кода

---

# Зачем нужны контейнеры?

- Доставка кода
#
    !console
    $ docker push image:tag

---

# Зачем нужны контейнеры?

- Доставка кода
#
    !console
    $ docker push image:tag
    $ docker pull image:tag

---

# Зачем нужны контейнеры?

- Доставка кода
- Воспроизводимость

---

# Зачем нужны контейнеры?

- Доставка кода
- Воспроизводимость
#
    !console
    $ docker build -t image:tag ./

---

# Зачем нужны контейнеры?

- Доставка кода
- Воспроизводимость
- Изоляция

---

# Зачем нужны контейнеры?

- Доставка кода
- Воспроизводимость
- Изоляция
- Масштабируемость

---

# Image

---

# Image

    !console
    $ docker save ubuntu:20.04 -o ubuntu2004.tar

---

# Image

    !console
    $ ll ubuntu2004
    drwxrwxr-x 5 poh poh 4096 мая 25 03:15 ./
    drwxrwxr-x 4 poh poh 4096 мая 25 03:15 ../
    drwxr-xr-x 2 poh poh 4096 окт 23  2020 46f8a7...e8d39e/
    drwxr-xr-x 2 poh poh 4096 окт 23  2020 4ad07a...704c1b/
    drwxr-xr-x 2 poh poh 4096 окт 23  2020 68e187...9ae867/
    -rw-r--r-- 1 poh poh 3352 окт 23  2020 d70eaf...decaf1.json
    -rw-r--r-- 1 poh poh  355 мая 25 03:15 manifest.json
    -rw-r--r-- 1 poh poh   88 мая 25 03:15 repositories

---

# Image

    !console
    $ ll ubuntu2004/68e187...9ae867/
    total 73512
    drwxr-xr-x  3 poh poh     4096 мая 25 03:17 ./
    drwxrwxr-x  5 poh poh     4096 мая 25 03:15 ../
    -rw-r--r--  1 poh poh      406 окт 23  2020 json
    -rw-r--r--  1 poh poh 75250176 окт 23  2020 layer.tar
    -rw-r--r--  1 poh poh        3 окт 23  2020 VERSION

---

# Image

    !console
    $ ls -l ubuntu2004/68e187...9ae867/layer
    lrwxrwxrwx  1 poh poh    7 мая 25 03:18 bin -> usr/bin/
    drwxr-xr-x  2 poh poh 4096 апр 15  2020 boot/
    drwxr-xr-x  2 poh poh 4096 окт  8  2020 dev/
    drwxr-xr-x 30 poh poh 4096 окт  8  2020 etc/
    drwxr-xr-x  2 poh poh 4096 апр 15  2020 home/
    lrwxrwxrwx  1 poh poh    7 мая 25 03:18 lib -> usr/lib/
    lrwxrwxrwx  1 poh poh    9 мая 25 03:18 lib32 -> usr/lib32/
    lrwxrwxrwx  1 poh poh    9 мая 25 03:18 lib64 -> usr/lib64/
    lrwxrwxrwx  1 poh poh   10 мая 25 03:18 libx32 -> usr/libx32/
    drwxr-xr-x  2 poh poh 4096 окт  8  2020 media/
    drwxr-xr-x  2 poh poh 4096 окт  8  2020 mnt/
    drwxr-xr-x  2 poh poh 4096 окт  8  2020 opt/
    drwxr-xr-x  2 poh poh 4096 апр 15  2020 proc/
    drwxr--r--  2 poh poh 4096 окт  8  2020 root/
    drwxr-xr-x  4 poh poh 4096 окт  8  2020 run/
    lrwxrwxrwx  1 poh poh    8 мая 25 03:18 sbin -> usr/sbin/
    drwxr-xr-x  2 poh poh 4096 окт  8  2020 srv/
    drwxr-xr-x  2 poh poh 4096 апр 15  2020 sys/
    drwxrwxrwt  2 poh poh 4096 окт  8  2020 tmp/
    drwxr-xr-x 13 poh poh 4096 окт  8  2020 usr/
    drwxr-xr-x 11 poh poh 4096 окт  8  2020 var/

---

# Image

- Метаданные образа

---

# Image

- Метаданные образа
- Метаданные слоёв

---

# Image

- Метаданные образа
- Метаданные слоёв
- Данные слоёв (наборы файлов)

---

# Dockerfile

---

# Dockerfile

    !docker
    FROM ubuntu:20.04

---

# Dockerfile

    !docker
    FROM node:lts

---

# Dockerfile

    !docker
    FROM python:3.8-slim

---

# Dockerfile

    !docker
    FROM python:3.8-slim
    COPY . /project

---

# Dockerfile

    !docker
    FROM python:3.8-slim
    COPY . /project
    RUN pip install -e /project

---

# Dockerfile

    !docker
    FROM python:3.8-slim
    COPY . /project
    RUN pip install -e /project
    CMD ["python", "-m", "project"]

---

# Container

---

# Container

- Образ, в котором запущен процесс

---

# Container

- Образ, в котором запущен процесс
#
    !console
    $ docker run --name my-container ubuntu:20.04 bash

---

# Container

- Образ, в котором запущен процесс
- Сконфигурированы ресурсы

---

# Container

- Образ, в котором запущен процесс
- Сконфигурированы ресурсы
    - Добавлен ещё один «слой» файловой системы

---

# Container

- Образ, в котором запущен процесс
- Сконфигурированы ресурсы
    - Добавлен ещё один «слой» файловой системы
    - Сеть (виртуальная или хост, порты)
#
    !console
    $ docker run --name my-container -p 80:80 ubuntu:20.04 bash
---

# Container

- Образ, в котором запущен процесс
- Сконфигурированы ресурсы
    - Добавлен ещё один «слой» файловой системы
    - Сеть (виртуальная или хост, порты)
    - Точки монтирования (volumes)
#
    !console
    $ docker run --name my-container -p 80:80  \
        -v /home/user:/ext ubuntu:20.04 bash

---

# Container

- Образ, в котором запущен процесс
- Сконфигурированы ресурсы
    - Добавлен ещё один «слой» файловой системы
    - Сеть (виртуальная или хост, порты)
    - Точки монтирования (volumes)
    - Очень много других

---

- Image

---

- Image = class

---

- Image = class
- Container

---

- Image = class
- Container = instance

---

# Docker build cache

---

# Docker build cache

    !docker
    FROM python
    COPY . /project
    RUN apt update && apt install -y libgdal-dev
    RUN pip install -e /project
    CMD ["python", "-m", "project"]

---

# Docker build cache

    !docker
    FROM python
    COPY . /project
    RUN apt update && apt install -y libgdal-dev
    RUN pip install -e /project
    CMD ["python", "-m", "project"]

Что тут не так?

---

# Docker build cache

    !docker
    FROM python
    COPY . /project
    RUN apt update && apt install -y libgdal-dev
    RUN pip install -e /project
    CMD ["python", "-m", "project"]

Как это исправить?

---

# Docker build cache

    !docker
    FROM python
    RUN apt update && apt install -y libgdal-dev

    COPY ./requirements.txt /project/requirements.txt
    RUN pip install -r /project/requirements.txt

    COPY . /project
    RUN pip install -e /project

    CMD ["python", "-m", "project"]

Редко изменяемое и тяжёлое раньше часто изменяемого и лёгкого

---

# Воспроизводимость сборки образа

---

# Воспроизводимость сборки образа

    !dockerfile
    FROM python
    RUN pip install flake8
    CMD ["flake8"]

---

# Воспроизводимость сборки образа

    !dockerfile
    FROM python
    RUN pip install flake8
    CMD ["flake8"]

Что тут не так?

---

# Воспроизводимость сборки образа

    !dockerfile
    FROM python
    RUN pip install flake8
    CMD ["flake8"]

Как это исправить?

---

# Воспроизводимость сборки образа

    !dockerfile
    FROM python:3.8.5-slim
    RUN pip install flake8==1.2.3
    CMD ["flake8"]

Dependencies pin!

---

# Dendencies pin

---

# Dendencies pin
- На уровне базового образа: `python:3.8.5-slim`

---

# Dendencies pin
- На уровне базового образа: `python:3.8.5-slim`
- На уровне пакетного менеджера: pip (pip-tools/pip-compile), npm, etc.

---

# Dendencies pin
- На уровне базового образа: `python:3.8.5-slim`
- На уровне пакетного менеджера: pip (pip-tools/pip-compile), npm, etc.
- На уровне исходного кода: git submodules

---

# Вопросы
