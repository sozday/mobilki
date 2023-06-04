Практические задания №2:

1. 
```FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

CMD ["python", "app.py"]
```


2.
```FROM node:14-alpine

WORKDIR /app

COPY ./src .

RUN npm install --production

CMD ["npm", "run", "prod"]```
