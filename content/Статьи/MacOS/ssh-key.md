Если уже есть ключ, обычно я держу в менеджере паролей, то можно вот так вот установить на свежую машину
```
cd ~ 
mkdir .ssh 
cp /Users/vprimin/downloads/id_rsa ~/.ssh/
cp /Users/vprimin/downloads/id_rsa.pub ~/.ssh/
chmod 600 ~/.ssh/id_rsa
```

Либо сделать новый, 
```
ssh-keygen -t rsa
```

Далее можно скопировать его на рабочий стол если хотим потом открыть, передать

```
sudo cp ~/.ssh/id_rsa.pub /Users/slava.primin/Desktop/key.pub
```

Не забудьте удалить

> [!warning] Никогда не передавайте свой приватный ключ третим лицам