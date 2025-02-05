---
tags:
  - windows
title: bginfo
date: 03/02/2025
---
> [!quote] Задача, сдеать Youtube ролик, в котором я раскатываю эту утилиту на все компьютеры в домене

Существует как минимум 5 основных способов, как это можно сделать.

1. Через планировщик задач (Win+R taskschd.msc)
2. Редактор реестра (Win+R regedit)
3. Меню "общий автозапуск" (Win+R shell:common startup) 
4. Через групповую политику (Win+R gpedit.msc) - предпочтительно для домен контроллеров
5. .bat или PowerShell script (ChatGPT в Помощь)

Скачиваем, https://learn.microsoft.com/ru-ru/sysinternals/downloads/bginfo 

Распаковываем например в C:\BGinfo\
Создаем себе файл bginfo.bgi сохраняем в эту же директорию.

## Regedit
Win+R 'regedit'

Ветка HKLM\Software\Microsoft\Windows\CurrentVersion\Run
Добавляем значение "строковый параметр"
```
"C:\BGinfo\Bginfo64.exe" "C:\BGinfo\bginfo.bgi" /timer:0 /silent /nolicprompt
```
Таким образом программа будет запускаться для всех пользователей на хосте

## Gpedit
Данный способ предпочтителен, если используется домен контроллер.

