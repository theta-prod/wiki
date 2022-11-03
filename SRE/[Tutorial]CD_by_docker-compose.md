# [Tutorial] CD by docker-compose.md

- **Metadata** : `type: Tutorial` `scope: SRE` 
- **Techs Need** : 
  - `Docker` `Docker-compose`
  - `Dockerhub`
- **Status** : `need-review`
<br/><br/>


## ✨ You should already know

> what's CD
> Why we need cd
> Docker & Docker-compose command
> git and git commond

👩‍💻 👨‍💻

<br/><br/>

## ✨ About the wiki

- `Situation:`  we have to build a pipeline of auto-deploy  
- `Target:` build a mock repo to depoly application by docker-compose

- `Index:`

| Sub title | decription | memo |
| ------ | ------ | ------ |
| Build a deployment Repo | Build deployment repo to depolyment | - |


<br/><br/>

## ✨ Section

> we will build a repo to deploy application, the deployment repo will independent to code/develop repo.
> the deployment repo only needs `pull & up` command and `config` of env.

---

### **Build a deployment Repo**

<br/>

####  📝 structure
> create a shell script named `main.sh`, env file `.env` and a `docker-compose.yaml` contain your application.
> We will use `main.sh` to up your server.
```
|- main.sh
|- .env
|- docker-compose.yaml
|- README.md
```



####  📝 `main.sh` & `.env`
- .env
```
MODE=DEBUG    # DEBUG | PROD
```

- main.sh
```
if [ -f .env ]
then
  export $(cat .env | xargs)
fi

if [ “$MODE” = “DEBUG” ];
then
  echo “MODE: $MODE”
  docker-compose pull
  docker-compose up
fi

if [ “$MODE” = “PROD” ];
then
  echo “MODE: $MODE”
  docker-compose pull
  docker-compose up -d
fi
```

---
####  📝 `README.md`

```
# Introduction 
TODO: Give a short introduction of your project. Let this section explain the objectives or the motivation behind this project. 

# Getting Started
TODO: Guide users through getting your code up and running on their own system. In this section you can talk about:
1.	Software dependencies
2.	API references
3.  Source code Repo

# Contribute
TODO: Explain how other users and developers can contribute to make your code better. 

If you want to learn more about creating good readme files then refer the following [guidelines](https://docs.microsoft.com/en-us/azure/devops/repos/git/create-a-readme?view=azure-devops). You can also seek inspiration from the below readme files:
- [ASP.NET Core](https://github.com/aspnet/Home)
- [Visual Studio Code](https://github.com/Microsoft/vscode)
- [Chakra Core](https://github.com/Microsoft/ChakraCore)
```



---
####  📝 `docker-compose.yaml`
> There is a mock docker-compose.yaml, make it be yours.
> **Don't forget! ALL IMAGE Should Pull from public paltform like `DockerHub`**
```
version: '2'

services:
  # phpmyadmin
  phpmyadmin:
    depends_on:
      - db
    image: phpmyadmin/phpmyadmin
    restart: always
    ports:
      - '8081:80'
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: password

  # Database
  db:
    image: mariadb:10.5.8
    volumes: ["./db_data:/var/lib/mysql"]
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress


  # Wordpress
  wordpress:
    image: wordpress:5-fpm-alpine
    depends_on:
      - db
    container_name: wordpress
    restart: always
    volumes:
      - wordpress:/var/www/html
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress

  nginx_server:
    depends_on:
      - wordpress
    image: nginx:1.15.12-alpine
    container_name: nginx_server
    restart: always
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - wordpress:/var/www/html
      - ./nginx-conf-http/:/etc/nginx/conf.d
      - ./wordpress.ini:/usr/local/etc/php/conf.d/wordpress.ini

networks:
  wpsite:

volumes:
  wordpress:
```