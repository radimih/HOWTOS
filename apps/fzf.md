# [fzf](https://github.com/junegunn/fzf)

### Клавиши

В командной строке (только в режиме вставки):
* `[каталог/][подстрока]**<Tab>` - поиск файла или каталога (например, `vim dev/css**<Tab>`)
* `export **<Tab>` - поиск по переменным окружения
* `kill [-сигнал]<Tab>` - выбор процесса
* `Ctrl-T` - поиск файла, начиная с текущего каталога (меняю на `Ctrl-F`)
* `Ctrl-R` - поиск команды в истории команд
* `Alt-C` - перейти в подкаталог, начиная с текущего (универсальнее использовать `cd **<Tab>`)

В списке выбора:
* `Ctrl-J` - вверх по списку
* `Ctrl-K` - вниз по списку
* `Enter` - выбор
* `ESC` - выход

### Установка

Стандартный способ установки, описанный в документации на GitHub'е - через `git clone`.
Здесь описан слегка модифицированный способ через git-submodule системы
[dotfiles](../dotfiles.md).

```bash
$ cd ~
$ dotfiles submodule add --depth 1 https://github.com/junegunn/fzf.git .fzf
$ .fzf/install --all
$ dotfiles add .fzf.zsh
```

Будет создан файл `~/.fzf.zsh`, который импортируется в `.zshrc` в самом конце.
ВНИМАНИЕ! Этот импорт дожен быть обязательно после команды включения VIM-режима
командной строки `bindkey -v`, чтобы корректно отработал key binding.

На другом компьютере:

```bash
$ dotfiles pull
$ .fzf/install --all
```

### Настройка

Опции утилиты `fzf`:

```
export FZF_DEFAULT_OPTS='--border'
```

Использовать утилиту [ag](https://github.com/ggreer/the_silver_searcher) вместо `find`,
включить в поиск скрытые файлы и игнорировать git-репы:

```bash
export FZF_DEFAULT_COMMAND='ag --hidden --ignore .git --silent -g ""'
export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"
```
