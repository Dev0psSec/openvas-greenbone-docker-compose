![alt](https://linuxincluded.com/wp-content/uploads/openvas_setup.png)

# Docker compose file for openvas greenbone with nginx providing https connection



## generate the keys

`openssl req -x509 -newkey rsa:4096 -keyout serverkey.pem -out servercert.pem -nodes -subj '/CN=localhost' -addext 'subjectAltName = DNS:localhost' -days 31`

## change the dir for your certs in the docker-compose file

`secrets:`

`  server-cert:`

`    file: /etc/greenbone/cert/servercert.pem`

`  server-key:`

`    file: /etc/greenbone/cert/serverkey.pem`

## run it (on 9392 port)

`docker compose -f $docker-compose.yml -p greenbone-community-edition up -d`

## enjoy!
