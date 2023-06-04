В третьей лабораторной я использовал эти команды:

Для начала:

docker stop $(docker ps -a -q)
docker container rm $(docker ps -a -q)
docker image prune -a
docker volume rm $(docker volume ls -q)
docker system prune -a

Затем:

docker run -d --name registry-ui -p 8080:80 jc21/registry-ui

Потом:

docker run -d --name shipyard --link registry-ui:registry-ui -v /var/run/docker.sock:/var/run/docker.sock shipyard/shipyard
А после этого подключался к APIdocker: 
a)открыл порт 8000 
b)перешел по адресу моего сеанса в pwd 
c)ввел логин и пароль по умолчанию 
d)добавил реестр docker

Далее:

docker run -d -p 80:80 --name my-apache httpd:latest
docker exec -it my-apache /bin/bash
ulimit -n 1024
Эта команда установит максимальное количество открытых файлов в 1024
