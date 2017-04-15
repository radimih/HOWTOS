# Тонкая настройка системы

### Отключение IPv6

ВНИМАНИЕ! Проверить, поддерживает ли текущий провайдер протокол IPv6:
[ipv6-test.com](http://ipv6-test.com)

    1. `$ sudoedit /etc/sysctl.conf`
    1. Вставить строку: `net.ipv6.conf.all.disable_ipv6 = 1`
    1. `$ sudo sysctl -p`
    1. `$ ifconfig`

### Символ '#' в русской раскладке

    1. `$ sudoedit /usr/share/X11/xkb/symbols/ru`
    1. 
