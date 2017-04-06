# Командная оболочка zsh
*Крутая командная оболочка, совместимая с bash:*

* *автодополнение по клавише* `Tab` *c дальнейшим выбором вариантов клавишей* `Tab` *или стрелками;*
* *разворачивание путей вида* `/u/s/f/tr` *клавишей* `Tab` *(*`/usr/share/fonts/truetype/`*);*
* *переход в каталог без команды* `cd` *(просто набираем путь к каталогу);*
* *ссылка на предыдущую команду с помощью* `!!` *(например,* `sudo !!`*)*
* *рекурсивный поиск (*`ls images/**/*.png`*).*

### Установка

```bash
sudo apt install -y zsh
chsh -s /usr/bin/zsh
```
### Установка [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

```bash
git clone --depth=1 https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
```

Внимание! предполагается, что [dotfiles](/dotfiles.md) уже установлен.
