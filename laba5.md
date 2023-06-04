1. Для монтирования volume в мой прошлый проект я:


1)создал директорию mkdir/var/www/html/data

2)```docker build -t kanye1```

3)```docker run -d -p 80:80 -v /var/www/html/data:/var/www/html/data kanye1```


2. Для генерации таблиц в PostgeSQL я:


1)```docker run --name postgres-container -e POSTGRES_PASSWORD=111111111 -p 5432:5432 -d postgres```

2)```docker exec -it postgres-container psql -U postgres```

3)После чего в оболочке psql
```
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50),
  email VARCHAR(50)
);
CREATE TABLE products (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  price DECIMAL(10,2)
);
```
3. Для проверки 12 примера я:


1)Я создал Dockerfile и скопировал туда код 12 примера после чего сохранил его

2)После чего собрал докер-образ ```docker build -t my-nginx-image и запустил контейнер docker run -d -p 80:80 --name my-nginx-container my-nginx-image```

3)И наконец командой ```docker inspect my-nginx-container``` проверил наличие примонтированного volume


4. Для выполнения 4 пункта:



1)создал "docker volume" ```docker volume create --name storage```

2)```sudo cp index.html /var/lib/docker/volumes/storage/_data```

3)```docker run -d -p 8080:80 -v storage:/usr/share/nginx/html -v /path/to/config/nginx.conf:/etc/nginx/nginx.conf --name nginx-container nginx``` (очень много думал над этим)

4)И наконец ```curl http://localhost:8080:80```
