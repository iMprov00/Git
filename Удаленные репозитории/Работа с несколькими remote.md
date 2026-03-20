
#### Fork workflow

При работе с форками open source проектов:

```shell
# origin - ваш форк
$ git remote add origin git@github.com:you/project.git

# upstream - оригинальный репозиторий
$ git remote add upstream git@github.com:original/project.git

# Получение изменений из оригинального репозитория
$ git fetch upstream
$ git checkout main
$ git merge upstream/main
```

#### Множественные хостинги

Синхронизация между разными платформами:

```ruby
# Основной репозиторий на GitHub
$ git remote add github git@github.com:user/project.git

# Зеркало на GitLab
$ git remote add gitlab git@gitlab.com:user/project.git

# Push во все репозитории
$ git push github main
$ git push gitlab main

# Или настройка множественных push URL для origin
$ git remote set-url --add --push origin git@gitlab.com:user/project.git
```

#### Резервные копии

```shell
# Добавление приватного сервера для резервных копий
$ git remote add backup ssh://git@backup.company.com/project.git

# Автоматическая синхронизация всех веток
$ git push backup --all
$ git push backup --tags
```

### Конфигурация remote

Git позволяет тонко настраивать поведение каждого remote:

```ruby
# Настройка refspec для выборочного получения веток
$ git config remote.origin.fetch '+refs/heads/main:refs/remotes/origin/main'

# Отключение автоматического fetch тегов
$ git config remote.origin.tagOpt --no-tags

# Настройка push по умолчанию
$ git config remote.origin.push 'refs/heads/main:refs/heads/main'

# Настройка URL для разных операций
$ git config remote.origin.pushurl git@github.com:user/project.git
```

### Диагностика проблем подключения

При проблемах с удалёнными репозиториями полезны следующие команды:

```shell
# Проверка сетевого подключения
$ git ls-remote origin

# Verbose режим для отладки
$ GIT_CURL_VERBOSE=1 git clone https://github.com/user/repo.git

# Для SSH проблем
$ ssh -vT git@github.com

# Проверка конфигурации
$ git config --list | grep remote
```