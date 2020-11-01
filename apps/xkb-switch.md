# [xkb-switch](https://github.com/ierton/xkb-switch)

Утилита и библиотека для ручного переключения раскладки клавиатуры в X-сессии. В частности,
используется в vim-плагине [Vim-xkbswitch](https://github.com/lyokha/vim-xkbswitch).

Состав:

* `xkb-switch` -> `/usr/local/bin/`
* `xkb-switch.1.gz` -> `/usr/local/share/man/man1/`
* `libxkbswitch.so.X.Y.Z` -> `/usr/local/lib/`
* symlink `libxkbswitch.so.X` -> `libxkbswitch.so.X.Y.Z`
* symlink `libxkbswitch.so` -> `libxkbswitch.so.X`

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
$ cat <<EOF | docker build -t xkb-switch -
FROM ubuntu:latest
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
 && apt-get install -y git build-essential cmake libxkbfile-dev \
 && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/ierton/xkb-switch.git
RUN cd xkb-switch && mkdir build && cd build \
 && cmake .. \
 && make
WORKDIR /xkb-switch/build
EOF
$ docker run -t --rm -v /usr/local:/usr/local xkb-switch make install
$ docker image rm xkb-switch
$ sudo ldconfig
```

#### Просто получить артефакты, не "засоряя" систему

```bash
$ mkdir xkb-switch && cd xkb-switch
$ cat <<EOF | docker build -t xkb-switch -
FROM ubuntu:latest
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
 && apt-get install -y git build-essential cmake libxkbfile-dev \
 && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/ierton/xkb-switch.git
RUN cd xkb-switch && mkdir build
WORKDIR /xkb-switch/build
EOF
$ docker run -t --rm -v `pwd`:/xkb-switch/build xkb-switch sh -c "cmake .. && make"
$ docker image rm xkb-switch
```

В текущем каталоге появятся необходимые артефакты.
