# [shift-shift](https://github.com/grafov/shift-shift)

Немодальный переключатель раскладки клавиатуры для X-сессии. Отвечает только за переключение раскладки
и не занимается индикацией текущей раскладки. Поэтому независим от WM и DE. Может спокойно уживаться
с каким-либо стандартным переключателем от DE.

* левый `Shift` - первая раскладка (обычно `EN`)
* правый `Shift` - вторая раскладка (обычно `RU`)

### Сборка из исходников

#### На Debian/Ubuntu:

```bash
sudo apt install libx11-dev golang
mkdir ss
cd ss
export GOPATH=~/ss
go get github.com/gvalkov/golang-evdev/evdev # возможна ошибка компиляции, игнорируем
go get github.com/grafov/shift-shift
mv bin/shift-shift ~/bin
cd ~
rm -rf ss
sudo apt remove -y golang
sudo apt autoremove
```
#### В контейнере Docker:

### Установка

ВНИМАНИЕ! Так как для работы программы требуются root-права для доступа к клавиатурным устройствам ввода
`/dev/input/event*`, то, как вариант, у исполняемого модуля можно сменить владелеца и установить флаг
SUID:

```bash
sudo chown root:root shift-shift
sudo chmod u+s shift-shift
```
