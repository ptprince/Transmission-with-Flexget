# Docker for pt

## Include

1. qbittorrent for download

1. Flexget for RSS

1. nginx for proxy qbt

1. emby or jeffylin for play video

## How to use

### Clone to your directory

- qbittorrent will download to

```bash
{YOUR_DIR}/qbt/downloads
```

### Edit nginx config (optional)

- add your domain and setting ssl  

```bash
nginx/conf.d/app.conf
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

- qbittorrent:

```bash
http://{your ip}/qbt
```

set watch `/watch` for downloading

- Emby or Jeffylin:

```bash
http://{your ip}/
```

- acme.sh (image only for amd64)

add to nginx

```app.conf
    location ~ "^/\.well-known/acme-challenge/([-_a-zA-Z0-9]+)$" {
        default_type text/plain;
        proxy_read_timeout    60;
        proxy_connect_timeout 60;
        proxy_redirect        off;
        proxy_pass http://acme-sh;

        proxy_set_header      X-Real-IP $remote_addr;
        proxy_set_header      X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header      X-Forwarded-Proto $scheme;
        proxy_set_header      Host $host;
    }
```

```bash
docker-compose exec acme-sh acme.sh --issue -d `your domain` --standalone (--debug)
```
