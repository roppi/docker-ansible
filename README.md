# docker-ansible

## ディレクトリ構成

```
.
├── README.md
├── ansible
│   ├── hosts
│   └── sample-playbook.yml
├── docker
│   ├── ansible
│   │   └── Dockerfile
│   └── target
│       └── Dockerfile
└── docker-compose.yml
```

## 使い方

1. Dockerコンテナを起動します。

```
$ docker-compose up -d
```

2. Ansibleコンテナに接続します。

```
$ docker exec -it ansible /bin/bash
```

3. Playbookを実行します

```
# ansible-playbook -i hosts sample-playbook.yml
```

4. 以下ように表示されれば、成功です。

```
# ansible-playbook -i hosts sample-playbook.yml 

PLAY [localhost] ***********************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [localhost]

TASK [hello world] *********************************************************************************************************************
ok: [localhost] => {
    "msg": "Hello World!"
}

PLAY [all] *****************************************************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************************
ok: [target]

TASK [yum update] **********************************************************************************************************************
ok: [target]

PLAY RECAP *****************************************************************************************************************************
localhost                  : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
target                     : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```