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

- Transmission:

```bash
http://{your ip}/tr
```

- Emby:

```bash
http://{your ip}/
```
s
## To Do

1. Add h5ai for searchand download

1. Get ssl on let's Encrypt automatic

1. Change button on TWC redicrect to emby/h5ai


