# docker-images

### asop-dev environment
> you can replace the volumes options by yourself local mysql & redis  conf file and data file.

> 'docker-compose.yml'

```yml
services:
  MYSQL3306:
    image: mysql:5.7.25
    command: --default-authentication-plugin=mysql_native_password
    restart: "always"
    environment:
      - MYSQL_ROOT_PASSWORD=123456
      - MYSQL_USER=springuser
      - MYSQL_PASSWORD=ThePassword
      - MYSQL_DATABASE=db_example
    ports:
      - "3306:3306"
    volumes:
      - E:\docker-desktop\asop-dev\mysql3306\data:/var/lib/mysql
      - E:\docker-desktop\asop-dev\mysql3306\conf:/etc/mysql/conf.d
    expose: 
      - "3306"  
    
  Redis6379:
    image: redis
    restart: "always"
    volumes:
      - D:\Database\redis\redis.conf:/usr/local/etc/redis/redis.conf
      - E:\docker-desktop\asop-dev\redis\data:/data
    command: redis-server /usr/local/etc/redis/redis.conf
    ports:
      - "6379:6379"
    expose:
      - "6379"
```

> run command line and cd into docker-compose.yml file directory and run command:
```bash
docker-compose -f docker-compose.yml up -d
```


