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

###  Тюнинг файловой системы

* Для несистемных ext4-разделов (например, `/home`) убрать резервирование 5% для root'а:
    1. `$ mount -l -t ext4`
    1. `$ sudo tune2fs -m 0 /dev/sda<номер>`
