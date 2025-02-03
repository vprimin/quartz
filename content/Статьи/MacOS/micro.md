---
date: 2025-01-28
title: Micro text editor
tags:
  - MacOS
---
Мне нравится Micro за то, что в него встроена подстветка синтаксиса документов. 

Ставим очень просто

```
curl https://getmic.ro | bash
```

Потом переносим в директорию с приложениями:

```
sudo mv /Users/slava.primin/micro /usr/local/bin/
```
замените имя пользователя на ваше

Если вдруг будет ругаться что такой папки нет, создадим
```
sudo mkdir -p /usr/local/bin
```

проверим 
```
micro --version
```
