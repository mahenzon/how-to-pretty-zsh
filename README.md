# Делаем красивый терминал zsh

> Если вы работаете на Ubuntu, используйте пакетный менеджер `apt`. 
> На macOS используйте `brew` ([ссылка](https://brew.sh/)).

## Узнайте, какая оболочка используется:

### Какая оболочка по умолчанию

```shell
echo $SHELL
```

Пример:

```
john@7e2102f43af0:/$ echo $SHELL
/bin/sh
```

### Какая оболочка используется сейчас

```shell
ps -p $$
```

Пример:

```
john@7e2102f43af0:/$ ps -p $$
  PID TTY          TIME CMD
    8 pts/0    00:00:00 bash
```

## Установка `zsh`

Руководство на английском
https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH

### Шаги

#### Установите `zsh`

Если `zsh` у вас уже установлен, пропустите этот шаг

```shell
sudo apt install -y zsh
```

#### Проверьте версию `zsh`

```shell
zsh --version
```

Пример:

```
john@7e2102f43af0:/$ zsh --version
zsh 5.9 (aarch64-unknown-linux-gnu)
```

#### Проверьте расположение `zsh`

```shell
which zsh
```

Пример:

```
john@7e2102f43af0:/$ which zsh
/usr/bin/zsh
```

#### Установите `zsh` как оболочку по умолчанию

```shell
chsh -s $(which zsh)
```

> Перезайдите в систему, чтобы применить новые настройки

#### Проверьте, какая оболочка используется по умолчанию, а также какая сейчас запущена (первые команды в инструкции)

## Установка `oh-my-zsh`

Руководство https://github.com/ohmyzsh/ohmyzsh/wiki

### Скачайте и выполните скрипт установки `oh-my-zsh`

Используйте одну из команд (для подходящей программы. Если не знаете, какую использовать, выбирайте первую).

| Method    | Command                                                                                           |
|:----------|:--------------------------------------------------------------------------------------------------|
| **curl**  | `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |
| **wget**  | `sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`   |
| **fetch** | `sh -c "$(fetch -o - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"` |


> Если `curl` (или другой инструмент) ещё не установлен, установите командой `sudo apt install -y curl`

> Если `git` ещё не установлен, установите командой `sudo apt install -y git`

В терминале может появиться запрос:

```
Time to change your default shell to zsh:
Do you want to change your default shell to zsh? [Y/n] 
```

Нажмите `Enter`, чтобы подтвердить (даже если ранее вы уже установили `zsh` как оболочку по умолчанию).

Если всё прошло успешно, вы увидите в терминале:

```
Shell successfully changed to '/usr/bin/zsh'.

         __                                     __   
  ____  / /_     ____ ___  __  __   ____  _____/ /_  
 / __ \/ __ \   / __ `__ \/ / / /  /_  / / ___/ __ \ 
/ /_/ / / / /  / / / / / / /_/ /    / /_(__  ) / / / 
\____/_/ /_/  /_/ /_/ /_/\__, /    /___/____/_/ /_/  
                        /____/                       ....is now installed!


Before you scream Oh My Zsh! look over the `.zshrc` file to select plugins, themes, and options.
```

Перезапустите оболочку (или перезагрузите компьютер).

## Настройка `oh-my-zsh`, установка плагинов

- Темы https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
- Плагины https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins-Overview
- Шпаргалка https://github.com/ohmyzsh/ohmyzsh/wiki/Cheatsheet

### Смена темы

Отредактируйте файл `~/.zshrc`, измените переменную `ZSH_THEME`

```shell
ZSH_THEME="half-life"
```

Темы могут меняться автоматически при каждом новом запуске (если вы не можете выбрать одну). 
Перечислите в массиве список тем, переменная `ZSH_THEME_RANDOM_CANDIDATES`, например:

```shell
ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )
```

### Установка специальных шрифтов

Используйте шрифты [Powerline Font](https://github.com/powerline/fonts) 
или шрифт [Nerd Font](https://www.nerdfonts.com/) (говорят, он даже лучше)
Хороший выбор это шрифт `Fira Code`, я использую `Source Code Pro`.

Чтобы проверить, работают ли у вас специальные шрифты, выполните в терминале команду:
```shell
echo -e "\xee\x82\xa0"

# Будет распечатан символ 
```


### Плагины

Я использую всего несколько плагинов:
- `z`
- `git`
- `zsh-autosuggestions`
- `zsh-syntax-highlighting`

#### Установка `z`

Это встроенный плагин для быстрой навигации по директориям

Добавьте `z` в массив `plugins` в `~/.zshrc`

#### Установка `zsh-autosuggestions`

"Умные" подсказки в терминале

Страница проекта
https://github.com/zsh-users/zsh-autosuggestions

Инструкция для установки в `oh-my-zsh`:
https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#oh-my-zsh

Скачайте плагин:
```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Добавьте `zsh-autosuggestions` в массив `plugins` в `~/.zshrc`

#### Установка `zsh-syntax-highlighting`

Страница проекта
https://github.com/zsh-users/zsh-syntax-highlighting

Инструкция для установки в `oh-my-zsh`:
https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md#oh-my-zsh

Скачайте плагин:
```shell
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Добавьте `zsh-syntax-highlighting` в массив `plugins` в `~/.zshrc`

### Тема `spaceship-prompt`

Страница проекта
https://github.com/spaceship-prompt/spaceship-prompt

Скачайте тему
```shell
git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
```

Добавьте папку с темой в список доступных тем
```shell
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

Установите тему. Отредактируйте файл `.zshrc`:
```shell
ZSH_THEME="spaceship"
```

#### Готово 🎉
