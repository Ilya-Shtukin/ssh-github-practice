# Отчёт: Настройка SSH-доступа к GitHub

## 1. Генерация ключа
- SSH-клиент: OpenSSH в Git Bash
- Тип ключа: ed25519
- Приватный ключ защищён passphrase: да
- Публичный ключ: `~/.ssh/id_ed25519.pub`

![alt text](<Генерация ключа.png>)

## 2. Добавление ключа на GitHub
Ключ добавлен через Settings → SSH and GPG keys.

![alt text](<Генерация SSH-ключа и добавление на GitHub-1.jpg>)

## 3. Проверка подключения
```bash
ssh -T git@github.com

Результат: Hi Ilya-Shtukin! You've successfully authenticated...

![alt text](<image-2.png>)

## 4. Работа с репозиторием по SSH

Изначально репозиторий был склонирован по HTTPS для настройки окружения. После генерации и добавления SSH-ключа, удалённый репозиторий (remote) был переключён на SSH-URL:

bash
git remote set-url origin git@github.com:Ilya-Shtukin/ssh-github-practice.git
git remote -v
Затем был создан коммит и выполнен git push. Операция прошла успешно без запроса пароля GitHub, что подтверждает работу SSH-аутентификации (ключ был добавлен в ssh-agent):

bash
git add README.md
git commit -m "Step 4: first push over SSH without password"
git push origin main

![alt text](image-3.png)

Ссылка на репозиторий: https://github.com/Ilya-Shtukin/ssh-github-practice
SSH push test
