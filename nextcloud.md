# Make letsencrypt certs
```
docker run -it --rm -p 443:443 -p 80:80 --name certbot \
            -v "/mnt/nextcloud/certs:/etc/letsencrypt" \
            -v "/var/lib/letsencrypt:/var/lib/letsencrypt" \
            quay.io/letsencrypt/letsencrypt:latest certonly \
			-d foo.bar.com -n -m foo@bar.com --standalone
```

# Or self signed certs
```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mysitename.key -out mysitename.crt
```

# Copy or link certs to default.[crt,key]
```
cd /mnt/nextcloud/certs
ln -sf mysitename.key default.key
ln -sf mysitename.crt default.crt
```

# Nextcloud
Modify domain and passwords in docker-compose.yml and
```
docker-compose up
```

