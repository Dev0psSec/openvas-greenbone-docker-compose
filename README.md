## Docker compose file for openvas greenbone with nginx providing tls layer



# generate the keys before 

`openssl req -x509 -newkey rsa:4096 -keyout serverkey.pem -out servercert.pem -nodes -subj '/CN=localhost' -addext 'subjectAltName = DNS:localhost' -days 31`

# up it

`docker compose -f $DOWNLOAD_DIR/docker-compose.yml -p greenbone-community-edition up -d`

# change the dir for your certs in the docker-compose file

`secrets:`

`  server-cert:`

`    file: /etc/greenbone/cert/servercert.pem`

`  server-key:`

`    file: /etc/greenbone/cert/serverkey.pem`

# restart

`docker compose -f docker-compose.yml -p greenbone-community-edition up -d`

# enjoy!
