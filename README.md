# Кроссплатформенный `C#` WebServer

# Описание
Реализация веб-сервера для отдачи статических файлов с диска. Язык написания: `C#`, используется фреймворк .NET Core, благодаря чему приложение обладает кроссплатформенностью. Есть возможность развернуть приложение при помощи Docker.

# Производительность
На данный момент разработанное API способно выдерживать **от 1000 до 2051 запроса в секунду** (request per second - rps) при разворачивании через docker-контейнер на машине со следующими характеристиками:
- RAM: 2GB
- CPU: Intel® Core™ i5-7400 
Разворачивание сервера, т.е. сборка docker-контейнера происходит в пределах 3 минут.

#Настройка
Для настройки сервера используется конфигурационный файл `/etc/httpd.conf`.
Config file spec:
```
cpu_limit 4       # maximum CPU count to use (for non-blocking servers)
thread_limit 256  # maximum simultaneous connections (for blocking servers)
document_root /var/www/html
```
#Тестирование
Более подробно о тестировании можно прочитать [здесь](https://github.com/init/http-test-suite). Там же можно найти бандл для тестирования сервера.

Контейнер можно собрать и запустить командами вида:
```
docker build -t y.van https://github.com/Meganster/tphighload_2k18.git
docker run -p 5000:5000 --name y.van -t y.van
```
