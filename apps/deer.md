# [deer](https://github.com/Vifon/deer)

[ranger](http://www.nongnu.org/ranger/)-подобная утилита выбора файла или каталога в командной строке.

### Установка

Устанавливается как плагин к `oh-my-zsh`. Так как из коробки не поддерживается `oh-my-zsh`, был сделан
форк проекта: [deer](https://github.com/radimih/deer).

Согласно [инструкции](https://github.com/radimih/HOWTOS/blob/master/apps/zsh.md#Установка-стороннего-плагина-не-входящего-в-oh-my-zsh)
по установке кастомного плагина `oh-my-zsh` через подсистему [dotfiles]():

```bash
$ cd $ZSH_CUSTOM/plugins
$ dotfiles submodule add https://github.com/radimih/deer.git
```

Добавить плагин в список плагинов `oh-my-zsh` в файле `.zshrc`:

```
plugins=(... deer)
```

### Настройка

Сменить клавишу по-умолчанию для активации утилиты `Atl-K` на комбинацию `Ctrl-D`:

```bash
bindkey '^d' deer
```
