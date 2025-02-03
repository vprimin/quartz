---
title: oh-my-zsh
date: 2025-01-28
tags:
  - MacOS
---
Установка oh-my происходит с сайта https://ohmyz.sh/ 

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

`micro ~/.zshrc`
theme= 'dst' 
[Каталог тем](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes#gallifrey)
`plugins=(sudo macos sublime)`

Ставим шрифты:
```
brew tap homebrew/cask-fonts
brew install font-iosevka
```



Список плугинов 
https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins
Я использую три
1. [macos](9https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/macos) 
2. [sublime](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sublime)
3. [sudo](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/sudo)