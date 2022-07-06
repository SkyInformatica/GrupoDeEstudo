# Docker 

## Material de apoio

* Descomplicando Docker: 
https://livro.descomplicandodocker.com.br/chapters/chapter_00.html

## Cronograma

O curso descomplicando Docker foi disponibilizado gratuitamente pela LinuxTips, assim seguem os links para acesso aos recursos:

### Dia 1

* [O que são containers?](https://www.youtube.com/watch?v=qZevFPMtQho&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=2)
* [O que é o copy on write?](https://www.youtube.com/watch?v=Hbb5zP-2vTU&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=3)
* [Namespace, cgroups e Netfilter](https://www.youtube.com/watch?v=V3ILFaE7q0o&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=4)
* [Praticando...](https://www.youtube.com/watch?v=r59eodKRwzk&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=5)
* [Instalando o Docker](https://www.youtube.com/watch?v=4XwzR9vXT5s&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=6)
* [Executando e administrando containers Docker (parte1)](https://www.youtube.com/watch?v=ms04rvuRyyI&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=7)
* [Executando e administrando containers Docker (parte2)](https://www.youtube.com/watch?v=HkFy7HRFkGo&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=8)
* [Configurando CPU e memória para os meus containers](https://www.youtube.com/watch?v=4vPmK9aEHug&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=9)
* [Dockerfile](https://www.youtube.com/watch?v=eXRlBgyQu6g&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=10)


### Dia 2 

* [Volumes - Tipo Bind](https://www.youtube.com/watch?v=5WPekl4XH2M&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=13)
* [Volumes - Tipo Volume](https://www.youtube.com/watch?v=TQmUeka6xzA&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=14)
* [Volumes - Data-Only e Prune](https://www.youtube.com/watch?v=O3fZbot5rtw&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=15)
* [Volumes - Desafio de pratica](https://www.youtube.com/watch?v=SJtpsE095LI&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=16)
* [Volumes - Resposta Desafio](https://www.youtube.com/watch?v=8sLRU6cVM3Q&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=17)
* [Volumes - Volumes e backup](https://www.youtube.com/watch?v=OhgQLTaI4es&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=18)

Códigos de exemplo Volumes:
``` 
# docker container run -ti --mount type=bind,src=/volume,dst=/volume ubuntu
# docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume ubuntu
# docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume,ro ubuntu
# docker volume create giropops
# docker volume rm giropops
# docker volume inspect giropops
# docker volume prune
# docker container run -d --mount type=volume,source=giropops,destination=/var/opa  nginx
# docker container create -v /data --name dbdados centos
# docker run -d -p 5432:5432 --name pgsql1 --volumes-from dbdados -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql
# docker run -d -p 5433:5432 --name pgsql2 --volumes-from dbdados -e  POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql
# docker run -ti --volumes-from dbdados -v $(pwd):/backup debian tar -cvf /backup/backup.tar /data
```
* [Dockerfile (parte 1)](https://www.youtube.com/watch?v=bJUccjvkPg4&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=19)
* [Dockerfile (parte 2)](https://www.youtube.com/watch?v=CSqY_Ofroxc&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=20)
* [Dockerfile (parte 3)](https://www.youtube.com/watch?v=RE6KoZlLvsI&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=21)
* [Dockerfile (parte 4)](https://www.youtube.com/watch?v=rlZzKlXRhOE&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=22)
* [Dockerfile multistage (parte 1)](https://www.youtube.com/watch?v=h3pTSW4p3OU&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=23)
* [Dockerfile multistage (parte 2)](https://www.youtube.com/watch?v=omptRNbu7cg&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=24)
* [Images e o commit](https://www.youtube.com/watch?v=DX8p6KZdorc&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=25)


Exemplo dockerfile 01:
```
FROM debian

RUN apt-get update && apt-get install -y apache2 && apt-get clean
ENV APACHE_LOCK_DIR="/var/lock"
ENV APACHE_PID_FILE="/var/run/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR="/var/log/apache2"

LABEL description="Webserver"

VOLUME /var/www/html/
EXPOSE 80
```

Exemplo dockerfile 02:
```
FROM debian

RUN apt-get update && apt-get install -y apache2 && apt-get clean
ENV APACHE_LOCK_DIR="/var/lock"
ENV APACHE_PID_FILE="/var/run/apache2/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_DIR="/var/run/apache2"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR="/var/log/apache2"

LABEL description="Webserver"

VOLUME /var/www/html/
EXPOSE 80

ENTRYPOINT ["/usr/sbin/apachectl"]
CMD ["-D", "FOREGROUND"]
```

Exemplo código:
```
package main
import "fmt"

func main() {
	fmt.Println("GIROPOPS STRIGUS GIRUS - LINUXTIPS")
}
```

Exemplo dockerfile 03:
```
FROM golang

WORKDIR /app
ADD . /app
RUN go build -o goapp
ENTRYPOINT ./goapp
```

Exemplo dockerfile 04:
```
FROM golang AS buildando

ADD . /src
WORKDIR /src
RUN go build -o goapp


FROM alpine:3.1

WORKDIR /app
COPY --from=buildando /src/goapp /app
ENTRYPOINT ./goapp
```

Comandos do dockerfile:
```
ADD => Copia novos arquivos, diretórios, arquivos TAR ou arquivos remotos e os adicionam ao filesystem do container;

CMD => Executa um comando, diferente do RUN que executa o comando no momento em que está "buildando" a imagem, o CMD executa no início da execução do container;

LABEL => Adiciona metadados a imagem como versão, descrição e fabricante;

COPY => Copia novos arquivos e diretórios e os adicionam ao filesystem do container;

ENTRYPOINT => Permite você configurar um container para rodar um executável, e quando esse executável for finalizado, o container também será;

ENV => Informa variáveis de ambiente ao container;

EXPOSE => Informa qual porta o container estará ouvindo;

FROM => Indica qual imagem será utilizada como base, ela precisa ser a primeira linha do Dockerfile;

MAINTAINER => Autor da imagem; 

RUN => Executa qualquer comando em uma nova camada no topo da imagem e "commita" as alterações. Essas alterações você poderá utilizar nas próximas instruções de seu Dockerfile;

USER => Determina qual o usuário será utilizado na imagem. Por default é o root;

VOLUME => Permite a criação de um ponto de montagem no container;

WORKDIR => Responsável por mudar do diretório / (raiz) para o especificado nele;
```

* [Dockerhub (parte 1)](https://www.youtube.com/watch?v=Uj9AgpxNS64&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=26)
* [Dockerhub (parte 2)](https://www.youtube.com/watch?v=D6rLGiR-luY&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=27)
* [Registry (parte 1)](https://www.youtube.com/watch?v=kyIDFEqf40o&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=28)
* [Registry (parte 2)](https://www.youtube.com/watch?v=0gzkfvjShJA&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=29)

### Dia 3

* [Docker Machine (parte 1) - obsoleto](https://www.youtube.com/watch?v=agpu1gtl7wk&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=31)
* [Docker Machine (parte 2) - obsoleto](https://www.youtube.com/watch?v=JcgJf6OFLvk&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=32)

Exemplo de comandos Docker Machine:
```
Para fazer a instalação do Docker Machine no Linux, faça:

# curl -L https://github.com/docker/machine/releases/download/v0.16.1
/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine
# chmod +x /tmp/docker-machine 
# sudo cp /tmp/docker-machine /usr/local/bin/docker-machine


Para seguir com a instalação no macOS:

# curl -L https://github.com/docker/machine/releases/download/v0.16.1
/docker-machine-`uname -s`-`uname -m` >/usr/local/bin/docker-machine 
# chmod +x /usr/local/bin/docker-machine

Para seguir com a instalação no Windows caso esteja usando o Git bash:

# if [[ ! -d "$HOME/bin" ]]; then mkdir -p "$HOME/bin"; fi
# curl -L https://github.com/docker/machine/releases/download/v0.16.1
/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe"
# chmod +x "$HOME/bin/docker-machine.exe"


Para verificar se ele foi instalado e qual a sua versão, faça:

# docker-machine version

# docker-machine create --driver virtualbox linuxtips

# docker-machine ls

# docker-machine env linuxtips

# eval "$(docker-machine env linuxtips)"

# docker container ls

# docker container run busybox echo "LINUXTIPS, VAIIII"

# docker-machine ip linuxtips

# docker-machine ssh linuxtips

# docker-machine inspect linuxtips

# docker-machine stop linuxtips

# docker-machine ls 

# docker-machine start linuxtips

# docker-machine rm linuxtips

# eval $(docker-machine env -u)
```

* [Docker Swarm (parte 1)](https://www.youtube.com/watch?v=ojQUXXea2Bk&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=33)
* [Docker Swarm (parte 2)](https://www.youtube.com/watch?v=aGif8R0BWHg&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=34)
* [Docker Nodes](https://www.youtube.com/watch?v=9aIYlRSC2Zs&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=35)
* [Docker Services](https://www.youtube.com/watch?v=oXvXwuAxa4I&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=36)
* [Docker Service Volumes](https://www.youtube.com/watch?v=p-JGKuFThcA&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=37)
* [Desenho Service Volumes](https://www.youtube.com/watch?v=Vwi6w4fKuyU&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=38)
* [Docker Service Network](https://www.youtube.com/watch?v=RX_3-aJAa0M&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=39)

Exemplos de comandos DOcker Swarm:

```
# docker swarm init

# docker swarm join --token \ SWMTKN-1-100_SEU_TOKEN SEU_IP_MASTER:2377

# docker node ls

# docker swarm join-token manager

# docker swarm join-token worker

# docker node inspect LINUXtips-02

# docker node promote LINUXtips-03

# docker node ls

# docker node demote LINUXtips-03

# docker swarm leave

# docker swarm leave --force

# docker node rm LINUXtips-03

# docker service create --name webserver --replicas 5 -p 8080:80  nginx

# curl QUALQUER_IP_NODES_CLUSTER:8080

# docker service ls

# docker service ps webserver

# docker service inspect webserver

# docker service logs -f webserver

# docker service rm webserver

# docker service create --name webserver --replicas 5 -p 8080:80 --mount type=volume,src=teste,dst=/app  nginx

# docker network create -d overlay giropops

# docker network ls

# docker network inspect giropops

# docker service scale giropops=5

# docker network rm giropops

# docker service create --name webserver --network giropops --replicas 5 -p 8080:80 --mount type=volume,src=teste,dst=/app  nginx

# docker service update <OPCOES> <Nome_Service> 
```

### Dia 4

* [Docker Secrets (parte 1)](https://www.youtube.com/watch?v=PDiNdjSa1KE&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=42)
* [Docker Secrets (parte 2)](https://www.youtube.com/watch?v=aG9H9L6Hbcg&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=43)

Exemplos de comandos secrets:

```
echo 'minha secret' | docker secret create 
docker secret create minha_secret minha_secret.txt
docker secret inspect minha_secret
docker secret ls
docker secret rm minha_secret
docker service create --name app --detach=false --secret db_pass  minha_app:1.0
docker service create --detach=false --name app --secret source=db_pass,target=password,uid=2000,gid=3000,mode=0400 minha_app:1.0
ls -lhart /run/secrets/
docker service update --secret-rm db_pass --detach=false --secret-add source=db_pass_1,target=password app
```

* [Docker Compose (parte 1)](https://www.youtube.com/watch?v=IhoNwQQnePk&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=45)
* [Docker Compose (parte 2)](https://www.youtube.com/watch?v=vz5oYhdA0EE&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=46)
* [Docker Compose (parte 3)](https://www.youtube.com/watch?v=h6uvOofo0Kg&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=47)
* [Docker Compose (parte 4)](https://www.youtube.com/watch?v=6X99ZZDXt5s&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=48)
* [Docker Compose (parte 5)](https://www.youtube.com/watch?v=QFHWJBdOgrE&list=PLf-O3X2-mxDn1VpyU2q3fuI6YYeIWp5rR&index=49)

Exemplo compose1:

```
# vim docker-compose.yml

version: "3"
services:
  web:
    image: nginx
    deploy:
      replicas: 5
      resources:
        limits:	
          cpus: "0.1"
          memory: 50M
      restart_policy:
        condition: on-failure
    ports:
    - "8080:80"
    networks:
    - webserver
networks:
  webserver:
```


Exemplo comandos compose1:

```
# docker stack deploy -c docker-compose.yml primeiro
# curl 0:8080
# docker service ls
# docker service ps primeiro_web
# docker stack ls
# docker stack services primeiro
# docker stack ps primeiro
# docker stack rm primeiro
```


Exemplo compose2:

```
# vim docker-compose.yml

version: '3'
services:
   db:
     image: mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
volumes:
  db_data:
```

Exemplo comandos compose2:

```
# docker stack deploy -c docker-compose.yml segundo
# docker stack ls
# docker stack services segundo
# docker service ls
# docker service ps segundo_db
# docker service ps segundo_wordpress
# docker service logs segundo_wordpress
```


Exemplo compose3:

```
# mkdir 3
# cd 3
# vim docker-compose.yml

version: "3"
services:
  web:
    image: nginx
    deploy:
      replicas: 5
      resources:
        limits:
          cpus: "0.1"
          memory: 50M
      restart_policy:
        condition: on-failure
    ports:
      - "8080:80"
    networks:
      - webserver

  visualizer:
    image: dockersamples/visualizer:stable
    ports:
      - "8888:8080"
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
    deploy:
      placement:
        constraints: [node.role == manager]
    networks:
      - webserver

networks:
  webserver:
```


Exemplo compose4:

```
# mkdir 4
# cd 4
# vim compose-file.yml

version: "3"
services:
  redis:
    image: redis:alpine
    ports:
      - "6379"
    networks:
      - frontend
    deploy:
      replicas: 2
      update_config:
        parallelism: 2
        delay: 10s
      restart_policy:
        condition: on-failure
  db:
    image: postgres:9.4
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - backend
    deploy:
      placement:
        constraints: [node.role == manager]
  vote:
    image: dockersamples/examplevotingapp_vote:before
    ports:
      - 5000:80
    networks:
      - frontend
    depends_on:
      - redis
    deploy:
      replicas: 2
      update_config:
        parallelism: 2
      restart_policy:
        condition: on-failure
  result:
    image: dockersamples/examplevotingapp_result:before
    ports:
      - 5001:80
    networks:
      - backend
    depends_on:
      - db
    deploy:
      replicas: 1
      update_config:
        parallelism: 2
        delay: 10s
      restart_policy:
        condition: on-failure
  worker:
    image: dockersamples/examplevotingapp_worker
    networks:
      - frontend
      - backend
    deploy:
      mode: replicated
      replicas: 1
      labels: [APP=VOTING]
      restart_policy:
        condition: on-failure
        delay: 10s
        max_attempts: 3
        window: 120s
      placement:
        constraints: [node.role == manager]
  visualizer:
    image: dockersamples/visualizer:stable
    ports:
      - "8080:8080"
    stop_grace_period: 1m30s
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
    deploy:
      placement:
        constraints: [node.role == manager]
networks:
  frontend:
  backend:
volumes:
  db-data:
```


Exemplo comandos compose4:

```
# docker stack deploy -c docker-compose.yml quarto
# docker service ls

Visualizar a página de votação:
http://IP_CLUSTER:5000/

Visualizar a página de resultados:
http://IP_CLUSTER:5001/

Visualizar a página de com os containers e seus nodes:
http://IP_CLUSTER:8080/
```
