# [xkb-switch](https://github.com/ierton/xkb-switch)

Утилита и библиотека для ручного переключения раскладки клавиатуры в X-сессии. В частности,
используется в vim-плагине [Vim-xkbswitch](https://github.com/lyokha/vim-xkbswitch).

### Установка из исходных текстов

```bash
$ sudo apt install -y build-essential cmake libxkbfile-dev
$ git clone git@github.com:ierton/xkb-switch.git
$ cd xkb-switch && mkdir build && cd build
$ cmake ..
$ make
$ sudo make install
$ cd ../.. && rm -rf xkb-switch
```
