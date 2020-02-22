# docker-compose : Laravel + MySQL + nginx + Redis + PostgreSQL

Software Development Environment for using Laravel Application.

## Software Stack

![Software Stack](docs/resources/software-stack.png)


## Set Up

```bash
# clone & change directory
git clone https://github.com/anfangd/docker-compose-php-laravel.git dc-laravel && cd $(basename $_ .git)

# If you want to access ssh to php container
ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f ssh-access_key
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in ssh-access_key.
Your public key has been saved in ssh-access_key.pub.
The key fingerprint is:
SHA256:+3**************************************zQ your_email@example.com
The key's randomart image is:
+---[RSA 4096]----+
|             . . |
+----[SHA256]-----+

mv ssh-access_key.pub php/authorized_keys

# build & Start
mv authorized_keys.sample authorized_keys

docker-compose build
docker-compose up -d

```

### Create New Laravel Project

```bash
# Create New Project
docker-compose exec php laravel new laravel-src
docker-compose exec php chmod -R 777 ./laravel-src/storage

# change .env
vim src/laravel-src/.env
```

```bash:src/laravel-src/.env
# change parameters
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=root
DB_USERNAME=root
DB_PASSWORD=root
```

```bash
# Migratiojn
$ docker-compose exec php php ./laravel-src/artisan migrate
Migration table created successfully.
Migrating: 2014_10_12_000000_create_users_table
Migrated:  2014_10_12_000000_create_users_table
Migrating: 2014_10_12_100000_create_password_resets_table
Migrated:  2014_10_12_100000_create_password_resets_table
```

## How to access

### HTTP

- http://localhost:8080/

### SSH

```bash

ssh -i ssh-access_key root@localhost -p 10000
```

### Visual Studio Code

You can access via VSCode using Remote Development.
