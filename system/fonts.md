# Настройка шрифтов

### Внедрение [Powerline](https://github.com/powerline/powerline)-символов в системные шрифты

```bash
$ sudo apt install fontconfig
$ sudo curl -Lo /usr/share/fonts/X11/misc/PowerlineSymbols.otf \
    https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
$ sudo curl -Lo /etc/fonts/conf.d/10-powerline-symbols.conf \
    https://github.com/powerline/powerline/raw/develop/font/10-powerline-symbols.conf
$ fc-cache
```
Далее перезапустить X-сессию.
