---
tags:
  - vpn
  - mikrotik
---
![](https://youtu.be/2tkeRGaDBGk)

> [!NOTE] В данной статье рассмотрим настройку Open VPN сервера для подключения клиентов из внешней сети.

## готовим наш RouterOS
- [ ] system>Identity (даем имя)
- [ ] admin user disable (удаляем пользователя admin)
- [ ] ip>services>disable (убираем лишние сервисы)
- [ ] system>packages (обновляемся до последней прошивки)
- [ ] включаем ip>cloud (аналог dyndns-опционально)
- [ ] Настраиваем правила ip>firewall открываем порты (1194-ovpn и 8291-winbox)
- [ ] Делаем отдельный ip>pool, например 172.10.10.2 - 172.10.10.255 (он нам пригодиться для профиля)
- [ ] Создаем отдельный профиль для подключений PPP>Profiles
      ![[Pasted image 20241110162929.png]]
  - [ ] опционально: во вкладке 'Limits' включаем опцию 'Only one - yes' если хотим ограничить только одно подключение с одного логина.
  - [ ] Включаем PPP > ovpn server, обращаем внимание на поля Default Profile & Certificate
        ![[Pasted image 20241110163130.png]]
- [ ] Создаем маршруты
##  создаем шаблоны

> [!warning] вводите команды по одной для избежания ошибок

```
/certificate
add name=ca-template common-name=ovpn.local days-valid=3650 key-size=2048 key-usage=crl-sign,key-cert-sign

/certificate add name=server-template common-name=server.ovpn.local days-valid=3650 key-size=2048 key-usage=digital-signature,key-encipherment,tls-server

/certificate add name=client-template common-name=client.ovpn.local days-valid=3650 key-size=2048 key-usage=tls-client
```
## подписываем сертификаты из шаблонов

```
/certificate sign ca-template name=ca-certificate

/certificate sign server-template name=server-certificate ca=ca-certificate

/certificate sign client-template name=client-certificate ca=ca-certificate
```
## экспортируем сертификаты в files

```
/certificate export-certificate ca-certificate export-passphrase=""
/certificate export-certificate server-certificate export-passphrase=""
/certificate export-certificate client-certificate export-passphrase=123456789
```
## Собираем .ovpn файл
Скачиваем в папку 
```
C:\Program Files\OpenVPN\bin  
```
client-certificate.key и переименовываем в client.key с openVPN Делаем  снятие пароля через командную строку.  запускаем cmd.exe от  админа   и  вводим команду

```
openssl.exe rsa -in client.key -out client.key
```

Открываем конфигурационный файл .ovpn  c помощью блокнота (Notepad +) и вставляем содержимое ключей а так же указываем маршрут назначения

Шпаргалка:

![[Pasted image 20241110174326.png|400]]

## Проверяем
Cоздаем пользователя в PPP>Secrets и проверяем подключение а также доступность удаленной сети.

[Ссылка на файлы, использованные в статье](https://drive.skp.kz/index.php/s/PYHdY3W9mposwt4): 

