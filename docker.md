# Mysql
```
docker run -d --name mysql \ 
  -v /srv/docker/owncloud/mysql:/var/lib/mysql \ 
  -e MYSQL_ROOT_PASSWORD=test \
  -e MYSQL_DATABASE=owncloud \ 
  -e MYSQL_USER=owncloud \ 
  -e MYSQL_PASSWORD=owncloud \ 
  mysql:5
```



# Owncloud
```
docker run --name=owncloud -h owncloud.example.com \
  -p 80:80 \
  --link mysql:mysql \
  -v /srv/docker/owncloud/config:/var/www/html/config \
  -v /srv/docker/owncloud/apps:/var/www/html/apps \
  -v /srv/docker/owncloud/data:/var/www/html/data \
  owncloud:9
```

# Create self signed certificate
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mysitename.key -out mysitename.crt
