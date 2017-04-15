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

### Настройка Synaptics touchpad

1. `$ cd /etc/X11`
1. `$ sudo mkdir xorg.conf.d`
1. `$ sudoedit xorg.conf.d/synaptics.conf`
1. `$ sudo reboot`

synaptics.conf:
```
# Описание опций можно найти в man synaptics.
# Текущие значения можно посмотреть и изменить по команде synclient

Section "InputClass"
  Identifier "Touchpad special settings"
  MatchIsTouchpad "on"
  Driver "synaptics"
  Option "LockedDrags" "on" # Залипание левой кнопки до повторного нажатия
  Option "CircularScrolling" "on" # Включить круговую прокрутку
  Option "CircScrollTrigger" "2" # Круговая прокрутка начинается от правого верхнего угла
  Option "CircularPad" "on" # Круговой тачпад (для Packard Bell)
  Option "HorizEdgeScroll" "on" # Включить горизонтальную прокрутку (по нижнему краю)
  # Понизить чувствительность касаний
  Option "FingerLow" "10" # Когда давление пальца ниже этого значения, фиксируется отпускание (было 25)
  Option "FingerHigh" "50" # Когда давление пальца выше этого значения, фиксируется касание (было 30)
EndSection
```
