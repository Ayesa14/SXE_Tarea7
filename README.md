# Tarea 7

## 1. Crear un archivo docker-compose.yml
```bash
mkdir joomla
cd joomla
nano docker-compose.yml
```

```bash
services:
    Joomla:
        image: joomla
        restart: always
        ports:
            - 8080:80
        environment:
            JOOMLA_DB_HOST: db
            JOOMLA_DB_USER: joomla
            JOOMLA_DB_PASSWORD: 1234
            JOOMLA_DB_NAME: joomla_db
            JOOMLA_SITE_NAME: Joomla
            JOOMLA_ADMIN_USER: Joomla
            JOOMLA_ADMIN_USERNAME: joomla
            JOOMLA_ADMIN_PASSWORD: joomla@secured
            JOOMLA_ADMIN_EMAIL: joomla@example.com
    
    db:
        image: mysql:8.0
        restart: always
        environment:
            MYSQL_DATABASE: joomla_db
            MYSQL_USER: joomla
            MYSQL_PASSWORD: 1234
            MYSQL_RANDOM_ROOT_PASSWORD: '1234'
        
    phpMyAdmin:
        image: phpmyadmin
        restart: always
        ports:
            - 8081:80
        environment:
            - PMA_ARBITRARY = 1
```
### 2. Iniciamos el docker compose
```bash
docker compose up -d
```
### 3. Comprobamos
```bash
docker ps
``` 
### 4. Accedemos
```bash
http://localhost:8080
```
```bash
http://localhost:8081
```
Accedemos como administradores con los credenciales del docker-compose.yml para comprobar que funciona
![Screenshot_20241111_103352.png](img/Screenshot_20241111_103352.png)
![Screenshot_20241111_103452.png](img/Screenshot_20241111_103452.png)
