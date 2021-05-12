# Atualização MySQL #

**Preparando cenário**
- Primeiro precisamos alterar os limites de arquivos abertos

```
    sudo vim /etc/security/limits.d/99-openfiles.conf
```
- Adicionar ao arquivo:

```
*              soft    nofile         8192
*              hard    nofile         8192
```

```
    systemctl edit mysql
```
- Adicionar ao arquivo:
```
    [Service]
    LimitNOFILE=8192
```
```
    systemctl daemon-reload
    service mysql restart
```

- Executar um backup dos dados antes:
```
    mysqldump -u dev -p --single-transaction --all-databases > backup_{data}.sql
```

- Baixar o instalador:
```
    wget https://dev.mysql.com/get/mysql-apt-config_0.8.9-1_all.deb
```

- Instalar o packet-manager
```
    sudo dpkg -i mysql-apt-config_0.8.9-1_all.deb -> selecionar a versao desejada para o server
```

```
    sudo apt-get update
    sudo apt-get install mysql-server
```

- Realizar upgrade
```
    sudo mysql_upgrade -u dev -p
```

- Alterar o `bind-address` para `0.0.0.0` para permitir conexões externas

```
    sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
```

```
    sudo service mysql restart
```


- Conferir a versão instalada
```
    mysql --version
```


- Referências:

1. [Aumentando limite de open_files MySQL](https://blog.werk21.de/en/2017/04/19/set-limit-open-files-mysql-ubuntu-1604-systemd)

1. [Upgrade MySQL](https://gist.github.com/cosmomathieu/826c6b29e122a856f2fbf22f7736f9c7)

1. [Export e Import de dump MySQL via terminal](https://www.digitalocean.com/community/questions/how-to-export-mysql-database-with-terminal)

1. [Ajustando conexão remota](https://serverfault.com/questions/586651/mysql-refuses-to-accept-remote-connections)