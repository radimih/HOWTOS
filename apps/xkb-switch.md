# [xkb-switch](https://github.com/ierton/xkb-switch)

Утилита и библиотека для ручного переключения раскладки клавиатуры в X-сессии. В частности,
используется в vim-плагине [Vim-xkbswitch](https://github.com/lyokha/vim-xkbswitch).

### Установка из исходных текстов

#### Непосредственно на рабочей системе

```bash
$ sudo apt install -y build-essential cmake libxkbfile-dev
$ git clone git@github.com:ierton/xkb-switch.git
$ cd xkb-switch && mkdir build && cd build
$ cmake ..
$ make
$ sudo make install
$ cd ../.. && rm -rf xkb-switch
```

#### Через Docker, не "засоряя" систему

```bash
$ mkdir xkb-switch && cd xkb-switch
$ cat <<EOF | docker build -t xkb-switch -
FROM ubuntu:latest
RUN apt-get update \
 && apt-get install -y git build-essential cmake libxkbfile-dev \
 && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/ierton/xkb-switch.git
RUN cd xkb-switch && mkdir build
WORKDIR /xkb-switch/build
EOF
$ docker run -t --rm -v `pwd`:/xkb-switch/build xkb-switch sh -c "cmake .. && make"
```

В текущем каталоге появятся необходимые артефакты:

* `xkb-switch`
* `xkb-switch.1.xz`
* `libxkbswitch.so.1.6.0`

Далее можно удалить уже ненужный Docker-образ:

```bash
$ docker image rm xkb-switch
```
