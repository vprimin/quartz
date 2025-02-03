---
tags:
  - windows
title: bginfo
date: 03/02/2025
---
> [!quote] Задача, сдеать Youtube ролик, в котором я раскатываю эту утилиту на все компьютеры в домене

Существует как минимум 5 основных способов, как это можно сделать.
1. Task scheduler (taskschd.msc)
2. Regedit (regedit)
3. shell:common startup 
4. gpedit.msc - предпочтительно для домен контроллеров
5. .bat или PowerShell script

В данном видео мы рассмотрим только два способа, которые я лично использую. Это через реестр и второй, более сложный - через групповую политику.

Скачиваем, https://learn.microsoft.com/ru-ru/sysinternals/downloads/bginfo 
Распаковываем например в C:\bginfo\
Создаем себе файл bginfo.bgi сохраняем в эту же директорию.

## Regedit
Win+R 'regedit'

Ветка HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
Добавляем значение
```
"C:\bginfo\bginfo64.exe" "C:\bginfo\bginfo.bgi" /timer:0 /silent /nolicprompt
```
Таким образом программа будет запускаться для всех пользователей на хосте

## Gpedit
Данный способ предпочтителен, если используется домен контроллер.

