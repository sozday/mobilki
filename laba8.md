Для выполнения поставленных задач я использовал следующие команды:

1. Запуск контейнера и получение информации о состоянии Docker на хосте:
```
docker info > docker_info.txt
```

2.Запуск произвольного контейнера и выполнение тестирования производительности в течение 3 минут:

```
docker run -d --name my_container ubuntu
sleep 180
docker stop my_container
```

3.Заморозка и разморозка контейнера:

```
docker pause my_container
docker unpause my_container
```

4.Просмотр логов веб-сервера Apache, когда контейнер находится под тестированием производительности:

```
docker logs my_container > apache_logs.txt
```

5.Запуск еще одного контейнера с MongoDB и получение статистики всех контейнеров (без столбца PIDS) с записью результатов в файл:

```
docker run -d --name mongodb_container mongo
docker stats --no-stream --format "table Container ID\tContainer Name\tCPU Usage\tMemory Usage" > container_stats.txt
```
