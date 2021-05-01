<!-- TOC -->

- [1. change directory](#1-change-directory)
- [2. Build Python Environtment at Once](#2-build-python-environtment-at-once)
    - [2.1. Install Python via pyenv](#21-install-python-via-pyenv)
    - [2.2. Install Ansible](#22-install-ansible)
- [3. build local dev server](#3-build-local-dev-server)
- [4. provision production server](#4-provision-production-server)

<!-- /TOC -->

# 1. change directory

```shell
$ cd wordpress-ansible
```

# 2. Build Python Environtment at Once

## 2.1. Install Python via pyenv

```shell
$ pyenv install 3.9.4
$ pyenv local 3.9.4
```

## 2.2. Install Ansible

```shell
$ pipenv install ansible --dev
```

# 3. build local dev server

```shell
$ htpasswd -b -B -c ansible/templates/local/lsws/admin/conf/htpasswd LSWS管理UIログイン名 LSWS管理UIログインパスワード
```

```shell
$ vi ansible/local/.env.j2

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
OPENLITESPEED_ADMIN="{管理UIログイン名}"
OPENLITESPEED_ADMIN_PASSWORD="{管理UIパスワード}"
```

```shell
$ pipenv shell
$ vagrant up --provision
```

# 4. provision production server

```shell
$ ansible-playbook -i hosts/lightsail provision.yaml
```

