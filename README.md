# hw8-systemd

## Основное задание

### Написать сервис, который будет раз в 30 секунд мониторить лог на предмет наличия клчевого слова. Файл и слово должны задаватся в /etc/sysconfig

Сервис был написан согласно инструкции. Название файла юнита для сервиса `watchlog.service`, а юнита для таймера `watchlog.timer`

###  Из epel установить spawn-fcgi и переписать init-скрипт на unit-файл. Имя сервиса должно также назваться.

Задание было выполнено по инструкции

###  Дополнить юнит-файл apache httpd возможность запустить несколько инстансов сервера с разными конфигами

Копируем шаблон Unit файла httpd и работаем с ним

```
cp /usr/lib/systemd/system/httpd.service /usr/lib/systemd/system/httpd@.service
```

Далее следовал по инструкции но получал ошибку при запуске второго сервиса:

```
(13)Permission denied: AH00072: make_sock: could not bind to address 0.0.0.0:9090
```

Решалось отключением SElinux

```
setenforce 0
```
