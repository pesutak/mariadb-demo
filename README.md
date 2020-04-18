# MariaDB deploy demo

this sample demostrates deploy MariaDB to Docker (standard and swarm mode) with configuration to support in-transit and at-rest encryption

```
git clone https://github.com/pesutak/mariadb-demo.git
```
## Docker

```
docker-compose up -d
```

## Swarm

initialize docker swarm mode if not yet initialized
```
docker swarm init
```

deploy the stack
```
docker stack deploy -c stack.yml demo
```

test connect and browse database from client container
```
docker container exec $(docker ps --filter name=demo_client -q) \
  mysql -hdb -usecuro -psecuro -Dtest -e "select * from hesla"
```
