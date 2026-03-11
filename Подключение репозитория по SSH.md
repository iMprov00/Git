# Проверить существующие ключи
ls -la ~/.ssh/

# Если нет ключа, создать новый
ssh-keygen -t ed25519 -C "your_email@example.com"
# Нажать Enter для всех вопросов (оставить пароль пустым)
# Показать публичный ключ
cat ~/.ssh/id_ed25519.pub

ssh -T git@github.com
Должно появиться: `Hi username! You've successfully authenticated...`


Далее добавить репозиторий git remote add origin git@github.com:username/repository-name.git

И проверить git remote -v

Будет что-то типо 
origin  git@github.com:username/repository-name.git (fetch)
origin  git@github.com:username/repository-name.git (push)