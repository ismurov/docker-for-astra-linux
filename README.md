# Инструкция по установке Docker на Astra Linux CE 1.6

### Установка Docker Engine
1. Обновите индексацию пакетов apt и установите пакеты, чтобы apt мог использовать репозиторий через HTTPS:
```
$ sudo apt-get update

$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

2. Добавте официальный ключ GPC Docker:
```
$ curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
```
Убедитесь, что у вас добавился ключ с отпечатком 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, выполнив поиск последних 8 символов отпечатка ключа.
```
$ sudo apt-key fingerprint 0EBFCD88

pub   4096R/0EBFCD88 2017-02-22
      Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid                  Docker Release (CE deb) <docker@docker.com>
sub   4096R/F273FCD8 2017-02-22
```

3. Подключите Docker репозиторий.
 - для x86_64/amd64
```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   stretch \
   stable"
```

4. Установите Docker Engine
```
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

5. Убедитесь, что Docker Engine установлен правильно, запустив образ hello-world.
```
$ sudo docker run hello-world
```

### Установка Docker Compose
1. Запустите эту команду, чтобы загрузить текущую стабильную версию Docker Compose:
```
$ sudo curl -L \
    "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" \
    -o /usr/local/bin/docker-compose
```

2. Примените исполняемые права доступа к двоичному файлу:
```
$ sudo chmod +x /usr/local/bin/docker-compose
```

3. Cоздать символическую ссылку в /usr/bin:
```
$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

4. Убедитесь, что Docker Compose установлен:
```
$ docker-compose --version
docker-compose version 1.26.0, build 1110ad01
```

