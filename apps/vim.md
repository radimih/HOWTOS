# VIM

### Установка из исходных текстов

Источник: [Building Vim from source](https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source)

1. Удалить существующую установку vim:

    ```bash
    sudo apt-get remove vim vim-runtime gvim vim-common
    ```

1. Установить необходимые библиотеки:

    ```bash
    sudo apt-get install libncurses5-dev libgnome2-dev libgnomeui-dev \
        libgtk2.0-dev libatk1.0-dev libbonoboui2-dev \
        libcairo2-dev libx11-dev libxpm-dev libxt-dev python3-dev
    ```

1. Скачать исходники:

    ```bash
    cd ~
    git clone https://github.com/vim/vim.git
    cd vim
    ```

1. Сконфигурировать и скомпилировать:

    ```bash
    ./configure \
        --with-features=huge \
        --with-x \
        --enable-fail-if-missing \
        --enable-multibyte \
        --enable-fontset \
        --enable-cscope \
        --enable-gui=auto \
        --enable-gtk2-check \
        --enable-gnome-check \
        --enable-python3interp=yes \
        --with-python3-config-dir=`ls -1d /usr/lib/python*/config-* | tail -1` \
        --prefix=/usr \
        --with-compiledby="Radimir Mikhailov"
    make VIMRUNTIMEDIR=/usr/share/vim/vim80
    ```

1. Установить vim с возможностью легкого удаления:

    ```bash
    sudo apt-get install checkinstall
    sudo checkinstall
    ```
    
    
