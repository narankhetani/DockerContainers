# Description
This image contains Ansible ARA (http://ara.readthedocs.io/en/latest/index.html) web application. The database should be installed out of this container. You can use the pg docker as db

# Tags
* nginx
run ARA on NGINX (https://nginx.org/en/). This image is based on the nginx official container:

# Build Docker
```
docker build --rm --tag ara_web:nginx .
```

## With MySQL Database
```
docker run --name ara_web -e "ARA_DATABASE=mysql+pymysql://ara:password@10.0.0.10/ara" ara_web:nginx
```
## With PG Database
```
docker run --name ara_web -e "ARA_DATABASE=postgresql+psycopg2://ara:password@172.17.0.1:5432/ara" ara_web:nginx
```

<!-- The directory ```<my_ssl_certificates_dir>``` should contains 2 files: ssl.crt and ssl.key*/ -->
