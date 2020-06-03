# Start or Stop the Services

These commands you must know when you using the xwiki of Websoft9

## xwiki

```shell
sudo systemctl start xwiki-server
sudo systemctl stop xwiki-server
sudo systemctl restart xwiki-server
sudo systemctl status xwiki-server

# you can use this debug mode if xwiki service can't run
xwiki-server console
```

## xwiki

```shell
sudo systemctl start xwiki-server
sudo systemctl stop xwiki-server
sudo systemctl restart xwiki-server
sudo systemctl status xwiki-server

# you can use this debug mode if xwiki service can't run
xwiki-server console
```

### MySQL

```shell
sudo systemctl start mysql
sudo systemctl stop mysql
sudo systemctl restart mysql
sudo systemctl status mysql
```

### Redis

```shell
systemctl start redis
systemctl stop redis
systemctl restart redis
systemctl status redis
```