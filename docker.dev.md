#### To run docker image

```sh
docker run --name matomo-mysql -p 3306:3306 -p 33060:33060 -e MYSQL_ROOT_PASSWORD=my-secret-pw -e MYSQL_USER=mainuser -e MYSQL_PASSWORD=mainuser -d mysql
```
```sh
docker run --env-file "$(pwd)/.env.local" --restart=always --name weatherspork-matomo-dev --link matomo-mysql:db -p 80:80 -v "$(pwd)/data:/var/www/html" -d matomo:4.5.0-apache
```

#### To kill the containers

```sh
docker kill matomo-mysql
```
```sh
docker rm matomo-mysql
```
```sh
docker kill weatherspork-matomo-dev
```
```sh
docker rm weatherspork-matomo-dev
```
