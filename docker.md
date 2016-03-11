# Postgresql
docker run --name postgres -e POSTGRES_USER=owncloud -e POSTGRES_PASSWORD=PassWord -e POSTGRES_DB=owncloud -d postgres

# Owncloud
docker run -d --name=owncloud -h owncloud.example.com -p 80:80 -p 443:443 --link postgres:db -e 'DB_NAME=owncloud' -e 'DB_USER=owncloud' -e 'DB_PASS=PassWord' -e 'ADMIN_USER=admin' -e 'ADMIN_PASS=admin' -e 'TIMEZONE=Europe/Berlin' pschmitt/owncloud

# Create self signed certificate
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mysitename.key -out mysitename.crt
