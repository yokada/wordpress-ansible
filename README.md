<!-- TOC -->

- [1. change directory](#1-change-directory)
- [2. First at Once, Build Python Environtment on your Host Machine](#2-first-at-once-build-python-environtment-on-your-host-machine)
    - [2.1. Install Python via pyenv](#21-install-python-via-pyenv)
    - [2.2. Install Ansible](#22-install-ansible)
    - [2.3. create secret.yml and encrypt it](#23-create-secretyml-and-encrypt-it)
    - [2.4. create .vault_password file](#24-create-vault_password-file)
- [3. build local dev server](#3-build-local-dev-server)
- [4. provision production server](#4-provision-production-server)

<!-- /TOC -->

# 1. change directory

```shell
$ cd wordpress-ansible
```

# 2. First at Once, Build Python Environtment on your Host Machine

## 2.1. Install Python via pyenv

```shell
$ pyenv install 3.9.4
$ pyenv local 3.9.4
```

## 2.2. Install Ansible

```shell
$ pipenv install ansible --dev
```

## 2.3. create secret.yml and encrypt it

```shell
$ cp ansible/vars/local/secret.sample.yml ansible/vars/local/secret.yml
$ ansible-vault encrypt ansible/vars/local/secret.yml
```

Shell will asks you that enter a new password for secret.yml ecryption:

```shell
New Vault password:
Confirm New Vault password:
Encryption successful
```

## 2.4. create .vault_password file

```shell
$ vi ansible/.vault_password
```

Then, write out your vault password into the `ansible/.vault_password` it would be exact same you entered on the above step.

# 3. build local dev server

```shell
$ pipenv shell
$ vagrant up --provision
```

# 4. provision production server

```shell
$ ansible-playbook -i hosts/lightsail provision.yaml
```

