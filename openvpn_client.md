# Настройка доступа к VPN (OpenVPN)

Доступ настраивается без использования **Network Manager**

### Установка и настройка

1. Установить:

  ```bash
  $ sudo apt install openvpn resolvconf
  $ sudo mv /etc/resolv.conf /etc/resolv.conf.orig
  $ sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
  ```

1. Скопировать конфигурационный файл vpn-соединения и соответствующие сертификаты и ключи
   в каталог `/etc/openvpn/client/`. Чтобы не смешивать ключи и сертифакты от разных
   соединений, можно для каждого соединения создать _подкаталог_. Тогда в конфигурационном
   файле соединения указывается относительный путь к сертификатам и ключам.

Пример конфигурационного файла:

```
client
proto tcp-client
dev tun
verb 0
mute 20
keepalive 10 120
persist-key
persist-tun
float
resolv-retry infinite
nobind

script-security 2
up   /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf

remote     185.118.64.212 1194
cipher     AES-256-CBC
tls-cipher "DEFAULT:@SECLEVEL=0"

ca   it2g-home/ca.crt
cert it2g-home/mikhailovrv2-it2g.ru.crt
key  it2g-home/mikhailovrv2-it2g.ru.key
```

При желании можно ключи и сертификаты встроить в сам конфигурационный файл:

```
<ca>
-----BEGIN CERTIFICATE-----
…
-----END CERTIFICATE-----
</ca>

<cert>
-----BEGIN CERTIFICATE-----
…
-----END CERTIFICATE-----
</cert>

<key>
-----BEGIN PRIVATE KEY-----
…
-----END PRIVATE KEY-----
</key>
```

### Использование

Соединение устанавливается/прерывается через **Unit systemd**:

  `openvpn-client@`_{имя конфиг-файла без расширения}_
  
- Соединение:

  ```bash
  $ sudo systemctl start openvpn-client@it2g-home
  ```

- Разъединение:

  ```bash
  $ sudo systemctl stop openvpn-client@it2g-home
  ```
