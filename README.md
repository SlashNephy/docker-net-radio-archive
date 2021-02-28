# docker-net-radio-archive
🐋 Docker image: SlashNephy/net-radio-archive (folked from yayugu/net-radio-archive)

[![Docker Image Size (tag)](https://img.shields.io/docker/image-size/slashnephy/net-radio-archive/latest)](https://hub.docker.com/r/slashnephy/net-radio-archive)

`docker-compose.yml`

```yml
version: '3.8'

services:
  mysql:
    container_name: net-radio-archive_MySQL
    image: mysql:5
    restart: always
    volumes:
      - /etc/localtime:/etc/localtime:ro
      - db:/var/lib/mysql
    environment:
      TZ: Asia/Tokyo
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: net-radio

  net-radio-archive:
    container_name: net-radio-archive
    image: slashnephy/net-radio-archive:latest
    restart: always
    volumes:
      - /etc/localtime:/etc/localtime:ro
      - ./database.yml:/myapp/config/database.yml:ro
      - ./settings.yml:/myapp/config/settings.yml:ro
      - logs:/myapp/log
      - /mnt/radio:/archive
      - tmp:/working
    environment:
      TZ: Asia/Tokyo

volumes:
  db:
    driver: local

  logs:
    driver: local

  tmp:
    driver: local
```
