# neovim

```vim
" Allow saving of files as sudo when I forgot to start vim using sudo.
cmap w!! w !sudo tee > /dev/null %
```

### Установка

### Установка менеджера плагинов [vim-plug](https://github.com/junegunn/vim-plug)

В файл `~/.config/nvim/init.vim` добавить команды, которые при первом запуске установят менеджер плагинов:

```vim
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
