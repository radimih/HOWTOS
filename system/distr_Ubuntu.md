Актуализировать систему:

```bash
$ sudo apt update && sudo apt full-upgrade -y
$ sudo apt clean && sudo apt autoclean -y && sudo apt autoremove -y
```

Скорее всего, эти пакеты уже установлены:

```bash
$ . /etc/os-release; sudo apt install --install-recommends linux-generic-hwe-$VERSION_ID xserver-xorg-hwe-$VERSION_ID
```

### Файловые системы

Для **ext4**: `noatime,barrier=0,commit=600`

`tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0`
