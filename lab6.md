Что б создать простое приложение на Vuejs, я использовал следующие шаги:
1. Пришлось установить Node.js
2. Создал новую дерикторию
3. Инициализировал новый проект 
```vue create```
4. Установил зависимости 
```npm install```
5. Создал vue.config.js и добавил туда следующий код:
```
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'http://localhost:8000',
        changeOrigin: true
      }
    }
  }
}
```
6.Запустил при помощи команды ```npm run serve```
7.Установил конфигурацию:
```
server {
    listen 8000;
    
    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
8.Запустил при помощи команды ```nginx```
