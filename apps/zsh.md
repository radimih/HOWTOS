# Командная оболочка zsh
*Крутая командная оболочка, совместимая с bash:*

* *автодополнение по клавише* `Tab` *c дальнейшим выбором вариантов клавишей* `Tab` *или стрелками;*
* *разворачивание путей вида* `/u/s/f/tr` *клавишей* `Tab` *(*`/usr/share/fonts/truetype/`*);*
* *переход в каталог без команды* `cd` *(просто набираем путь к каталогу);*
* *ссылка на предыдущую команду с помощью* `!!` *(например,* `sudo !!`*)*
* *рекурсивный поиск (*`ls images/**/*.png`*).*

### Установка zsh

```bash
sudo apt install -y zsh
chsh -s /usr/bin/zsh
```
### Установка [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

oh-my-zsh и сторонние плагины к нему устанавливаются в виде git-подмодулей
в репозитории [dotfiles](https://github.com/radimih/dotfiles):
* каталог `~/.oh-my-zsh` - сам oh-my-zsh (путь указывается в переменной `ZSH`)
* каталог `~/.oh-my-zsh-custom` - сторонние модули и плагины (путь указывается в переменной `ZSH_CUSTOM`)

Внимание! предполагается, что [dotfiles](/dotfiles.md) уже установлен.

1. Установить oh-my-zsh:
    ```bash
    cd ~
    dotfiles submodule add https://github.com/robbyrussell/oh-my-zsh.git .oh-my-zsh
    cp -r .oh-my-zsh/custom .oh-my-zsh-custom
    ```

1. Добавить в `.zshrc` строки:

    ```bash
    export ZSH=$HOME/.oh-my-zsh
    export ZSH_CUSTOM=$HOME/.oh-my-zsh-custom
    
    ZSH_THEME="robbyrussell"
    COMPLETION_WAITING_DOTS="true"
    
    plugins=(git)

    source $ZSH/oh-my-zsh.sh
    ```
  
    Полный список параметров oh-my-zsh смотрите в файле [`~/.oh-my-zsh/templates/zshrc.zsh-template`](https://github.com/robbyrussell/oh-my-zsh/blob/master/templates/zshrc.zsh-template).
    
    Список встроенных тем: [](https://github.com/robbyrussell/oh-my-zsh/wiki/themes)

### Установка стороннего плагина, не входящего в oh-my-zsh

1. Добавить в каталог `$ZSH_CUSTOM/plugins` плагин в виде git-подмодуля репозитория `dotfiles`:

    ```bash
    cd $ZSH_CUSTOM/plugins
    dotfiles submodule add {URL репозитория плагина}
    ```
  
1. Активировать плагин в `~/.zshrc`:

    `plugins=( [plugins...] `*`{название плагина}`*`)`

### Интересные сторонние плагины

* [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) - подсветка синтаксиса в командной строке
* [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) - автодополнение командной строки
