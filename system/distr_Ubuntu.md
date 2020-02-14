```bash
$ sudo apt update && sudo apt full-upgrade -y
$ . /etc/os-release; sudo apt install --install-recommends linux-generic-hwe-$VERSION_ID xserver-xorg-hwe-$VERSION_ID
$ sudo apt clean && sudo apt autoclean && sudo apt autoremove
```

### Файловые системы

Для **ext4**: `noatime,barrier=0,commit=600`

`tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0`
