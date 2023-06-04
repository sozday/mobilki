Команды которые я использовал в 4 лабе

Найдя уже готовый в интернете html файл с использованием js, взял его за основу

создал dockerfile в корне репозитория и в него прописал следующий код

FROM nginx
COPY js.html /usr/share/nginx/html
COPY style.css /usr/share/nginx/html
COPY script.js /usr/share/nginx/html

после чего я создал docker образ

docker build -t js

запустил его

docker run -d -p 80:80 js
