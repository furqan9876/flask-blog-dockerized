# Using Docker Compose 
Run the app with just one command :)
```bash
docker compose up -d
```




# If you want to do it manually, these are the steps.
## db
```bash
docker run --name mysql-container \
            -v mysql_volume:/var/lib/mysql \
            -p 3306 -p 33060 \
            -e MYSQL_ROOT_PASSWORD=abc \
            -d mysql:8.0-debian

docker run -it --rm mysql:8.0-debian mysql -h 172.17.0.2 -u root -p

# add database from db.sql

```

## app
```bash
docker build -t blog_app:v1 .
docker run --name blog_app -p 5000:5000 -d blog_app:v1
```


## nginx
```bash
docker run -d --name nginx-container -p 8080:80 nginx:latest

docker cp config/flask.conf nginx-container:/etc/nginx/conf.d/default.conf

docker exec nginx-container nginx -t
docker exec nginx-container nginx -s reload
```

