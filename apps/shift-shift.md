# shift-shift

Немодальный переключатель раскладки клавиатуры для X-сессии. Отвечает только за переключение раскладки
и не занимается индикацией текущей раскладки. Поэтому независим от WM и DE. Может спокойно уживаться
с каким-нибудь стандартным переключателем от DE.

* левый `Shift` - первая раскладка (обычно `EN`)
* правый `Shift` - вторая раскладка (обычно `RU`)

Страница проекта: [github.com/grafov/shift-shift](https://github.com/grafov/shift-shift)

### Сборка из исходников

#### На Debian/Ubuntu:

```bash
sudo apt install golang libx11-dev
mkdir ss
cd ss
GOPATH=ss
go get github.com/gvalkov/golang-evdev/evdev
go build github.com/grafov/shift-shift
```
#### В контейнере Docker

### Установка

ВНИМАНИЕ! Так как для работы программы требуются root-права для доступа к клавиатурным устройствам ввода
`/dev/input/event*`, то, как вариант, у исполняемого модуля можно сменить владелеца и установить флаг
SUID:

```bash
sudo chown root:root shift-shift
sudo chmod u+s shift-shift
```
