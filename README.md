---
tags: Web Programming
---

# Docker Strapi

In this section I am going to try Strapi is the next-gen headless CMS, open-source, javascript, enabling content-rich experiences to be created, managed and exposed to any digital device.. Here is detail about Strapi.

[https://strapi.io/](https://)

Docker Strapi
---
docker-compose.yml
```
version: '3'

services:
  strapi:
    container_name: strapi
    image: strapi/strapi
    environment:
      - DATABASE_CLIENT=postgres
      - DATABASE_HOST=db
      - DATABASE_PORT=5432
      - DATABASE_NAME=strapi
      - DATABASE_USERNAME=strapi
      - DATABASE_PASSWORD=strapi
    ports:
      - 9001:1337
    volumes:
      - ./app:/srv/app
    depends_on:
      - db

  db:
    container_name: postgres
    image: postgres
    restart: always
    volumes:
       - postgres:/data/postgres
       - ./postgres:/temp
    environment:
      POSTGRES_USER: strapi
      POSTGRES_PASSWORD: strapi
      POSTGRES_DB: strapi
      PGDATA: /var/lib/postgresql/data

volumes:
    postgres:
    app:
    
```
Note : If you want to change IP make sure in windows the IP is not used 
```
c:\netsh interface ipv4 show excludedportrange protocol=tcp
Protocol tcp Port Exclusion Ranges

Start Port    End Port
----------    --------
      1035        1134
      1135        1234
      1235        1334
      1335        1434
      1622        1721
      1732        1831
      1842        1941
     50000       50059     *

```
default ip strapi 1337 is forbidden ranging from 1335 - 1434 so make sure the ip strapi is not between start port and end port.

go to the project
```
cd your-project
docker-compose up 
```

When creating docker strapi it will take time to initializing so be patient


![](https://i.imgur.com/JTipv7J.png)


Happy Learning !!!
