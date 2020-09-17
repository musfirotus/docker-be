# Backend Simple WMS ~ with Docker Compose

## Tutorial
- Download Docker Compose
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
- Grant executable permission :
```bash
sudo chmod +x /usr/local/bin/docker-compose
```
- Check if installed
```bash
docker-compose --version
```
- Create docker-compose.yml
```bash
version: "3.7"
# Version of docker compose
services:
    mysql:
        container_name: dbcompose2
        image: mysql:latest
        environment: 
            - MYSQL_ROOT_PASSWORD=fira1234
            - MYSQL_DATABASE=simple_wms
        ports:
            - 1122:3306
        networks:
            - network1
    simplewms:
        container_name: "simplewms"
        image: musfirotus/dockerbackend:1.0
        ports: 
            - 2211:3000
        depends_on: 
            - mysql
        # command: bash -c "npx sequelize-cli db:migrate"
        networks: 
            - network1
networks: 
    network1:
        name: network1
```
- Build using docker-compose
```bash
docker-compose up -d
```
- Container Access for Manual DB Migration
```bash
docker exec -it [container id] bash
```
- Manual DB Migration
```bash
npx sequelize-cli db:migrate
```

## Task
Docker Compose
- [x] membuat docker compose untuk project BE yang sudah ada (simple wms) dengan mysql dan reddis
- [x] buat link repo yang sudah includ denan dockerfile dan docker compose
- [x] dan buat tutorialnya menggunakan readme.md