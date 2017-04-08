# dotfiles

## Первоначальная настройка репозитория

1. Создать репозиторий `dotfiles` на [GitHub](https://github.com)

1. Выполнить следующие команды в своем **домашнем** каталоге (заменить URL `git@github.com:radimih/dotfiles.git` на актуальный):
    ```bash
    cd ~
    git init --bare .dotfiles
    alias dotfiles='git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
    dotfiles remote add origin git@github.com:radimih/dotfiles.git
    dotfiles config --local status.showUntrackedFiles no
    echo ".dotfiles" > .gitignore
    dotfiles add .gitignore
    dotfiles commit -m "Initial commit"
    dotfiles push --set-upstream origin master
    ```

ВНИМАНИЕ! Не забыть добавить алиас в `.bash_aliases` и `.zshrc`:

```bash
alias dotfiles='git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
```

## Использование

```bash
dotfiles status
dotfiles add .zshrc
dotfiles commit -m 'Add zsh config'
dotfiles push
```

## Развертывание на новом компьютере

```bash
git clone --bare git@github.com:radimih/dotfiles.git $HOME/.dotfiles
alias dotfiles='git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
dotfiles config --local status.showUntrackedFiles no
dotfiles checkout --force
dotfiles submodule update --init
```

## Разделение по компьютерам
