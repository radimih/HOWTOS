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

oh-my-zsh и его кастомные плагины устанавливаются в виде git-подмодулей
в репозитории [dotfiles](https://github.com/radimih/dotfiles):
* каталог `~/.oh-my-zsh` - сам oh-my-zsh (путь указывается в переменной `ZSH`)
* каталог `~/.oh-my-zsh-custom` - кастомные модули и плагины (путь указывается в переменной `ZSH_CUSTOM`)

Поэтому если они уже есть 
Внимание! предполагается, что [dotfiles](/dotfiles.md) уже установлен.

1. Установить oh-my-zsh:
    ```bash
    cd ~
    dotfiles submodule add https://github.com/robbyrussell/oh-my-zsh.git .oh-my-zsh
    dotfiles commit -m "Add Oh-my-zsh"
    ```

1. В `.zshrc` добавить следующие строки:

    ```bash
    ZSH=
    ```
  
    Другие параметры смотрите в файле `~/.oh-my-zsh/templates/zshrc.zsh-template`

### Установка произвольного кастомного плагина

1. Добавить в каталог `$ZSH_CUSTOM/plugins` плагин в виде git-подмодуля репозитория `dotfiles`:

    ```bash
    cd $ZSH_CUSTOM/plugins
    dotfiles submodule add {URL модуля}
    dotfiles commit -m "Add custom oh-my-zsh plugin"
    ```
  
1. Активировать плагин в `~/.zshrc`:

    `plugins=([plugins...] `*`{название плагина}`*`)`

### Интересные кастомные плагины

* [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) - подсветка синтаксиса в командной строке
* [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) - автодополнение в командной строке
