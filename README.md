# Docker for pt

## Include

1. Transmission with TWC

1. Flexget for RSS

1. nginx for proxy TR

1. emby for play video

## How to use

### Clone to your directory

- Transmission will download to 

```bash
{YOUR_DIR}/transmission/downloads
```

### Edit nginx config (optional)

- add your domain and setting ssl  

```bash
nginx/conf.d/transmission.conf
```

- add http record when you  want to add ssl

```bash
nginx/well-known
```

### Add rss info to flexget

- edit flexget/config.yml to add your rss

### Run docker-compose

```bash
cd {your dir}
docker-compose up -d
```

## Web

### Basic auth for nginx

To use basic auth , please uncomment config file

default:

- user: ptpt
- PW:  LovePT

or you can generate new one

```bash
# make sure openssl was installed
echo "{Username}:$(openssl passwd -apr1 {password})" > {Your dir}/nginx/conf.d/.htpasswd

#ex: username: user1, password: password1
echo "user1:$(openssl passwd -apr1 password1)" > {Your dir}/nginx/conf.d/.htpasswd
```

- Transmission:

```bash
http://{your ip}/tr
```

- Emby:

```bash
http://{your ip}/
```

## To Do

1. Add h5ai for searchand download

1. Get ssl on let's Encrypt automatic

1. Change button on TWC redicrect to emby/h5ai


