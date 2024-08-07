# Joomla

![joomla](https://raw.githubusercontent.com/zakery1369/pics/master/Joomla.png)

### Configure docker-compose.yml

```bash
version: '3.5'

services:
  joomla:
    image: joomla
    container_name: joomlaweb
    restart: unless-stopped
    links:
      - joomlamysql
    ports:
      - 80:80
    environment:
      JOOMLA_DB_HOST: joomlamysql
      JOOMLA_DB_NAME: joomladb
      JOOMLA_DB_USER: joomlauser
      JOOMLA_DB_PASSWORD: 147258369
    
    networks:
      - joomla

  joomlamysql:
    image: mysql:latest
    container_name: joomlamysql
    volumes:
        - ./mysql/mysql_data:/var/lib/mysql
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: RO0tP@sswd
      MYSQL_DATABASE: joomladb
      MYSQL_USER: joomlauser
      MYSQL_PASSWORD: 147258369

    networks:
      - joomla

networks:
  joomla:
    name: joomla-network
    driver: bridge

```

---

1. Run the command below :

```bash
docker-compose up -d
```

2. Direct your browser to http://localhost

Note that port 80 must be open and not in use
