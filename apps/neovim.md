# [neovim](https://neovim.io/)

### Установка

Для всех "вкусняшек" необходимо ставить версию не ниже 0.2. Поэтому для Ubuntu пока ставится из **unstable**-ppa.

```bash
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository ppa:neovim-ppa/stable
$ sudo apt-get update
$ sudo apt-get install neovim

$ sudo update-alternatives --install /usr/bin/vim vim /usr/bin/nvim 1
$ sudo update-alternatives --config vim
```

### Установка менеджера плагинов [vim-plug](https://github.com/junegunn/vim-plug)

В файл `~/.config/nvim/init.vim` добавить команды, которые при первом запуске установят менеджер плагинов:

```vim
"-------------------------------------------------------------------------------
" Автоматическая установка менеджера плагинов vim-plug
"-------------------------------------------------------------------------------
let vim_plug_file = expand('~/.config/nvim/autoload/plug.vim')

if !filereadable(vim_plug_file)
  silent execute '!curl -fL'
                    \ ' -o ' . vim_plug_file .
                    \ ' --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
  autocmd VimEnter * PlugInstall
endif

"-------------------------------------------------------------------------------
" Список плагинов
"-------------------------------------------------------------------------------
call plug#begin(expand('~/.config/nvim/plugged'))
    
Plug 'scrooloose/nerdtree'
    
call plug#end()
```

#### Команды менеджера плагинов:

* :**PlugInstall** [name ...] - для установки плагинов
* :**PlugUpdate** [name ...] - для обновления плагинов
* :**PlugUpgrade** - для обновления самого менеджера плагинов
