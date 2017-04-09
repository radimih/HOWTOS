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
        --with-compiledby="$USER"
    make VIMRUNTIMEDIR=/usr/share/vim/vim80
    ```

1. Установить vim с возможностью легкого удаления:

    ```bash
    sudo apt-get install checkinstall
    sudo checkinstall -y --pkgname vim-own
    ```
    
    Посмотреть текущую конфигурацию vim: `vim --version`
    Удалить vim из системы: `dpkg -r vim-own`

1. Сделать vim редактором по-умолчанию:

    ```bash
    sudo update-alternatives --install /usr/bin/editor editor /usr/bin/vim 1
    sudo update-alternatives --set editor /usr/bin/vim
    sudo update-alternatives --install /usr/bin/vi vi /usr/bin/vim 1
    sudo update-alternatives --set vi /usr/bin/vim
    ```

1. Удалить продукты жизнедеятельности :)

    ```bash
    cd ~
    rm -rf vim
    ```

### Установка менеджера плагинов [vim-plug](https://github.com/junegunn/vim-plug)

В файл `.vimrc` добавить команды, которые при первом запуске установят менеджер плагинов:

    ```bash
    if empty(glob('~/.vim/autoload/plug.vim'))
     silent !curl -fLo ~/.vim/autoload/plug.vim --create-dirs
        \ https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
      autocmd VimEnter * PlugInstall | source $MYVIMRC
    endif

    call plug#begin('~/.vim/plugins')
    
    Plug 'jszakmeister/vim-togglecursor'
    
    call plug#end()
    ```

