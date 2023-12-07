<h1 align="center">
  <img src="./../image/docker-logo.png" alt="Docker" width=180px height=120px >
  <br>
  Docker - Variáveis
</h1>

<div align="center">

[![Status](https://img.shields.io/badge/version-1.0-blue)]()
![Static Badge](https://img.shields.io/badge/status-desenvolvimento-deve)
</div>


# Construindo a Imagem
`Dockerfile`
```
FROM node:14
WORKDIR /app-node
COPY . .
RUN npm isntall
ENTRYPOINT npm start
```
Comando.
```
docker build -t faelk8/app-node:1.0 .
docker run -p 8080:3000 -d faelk8/app-node:1.0
```
* http://localhost:3000

# Variáveis
Utilizando variável para setar uma porta.
`Dockerfile`
```
FROM node:14
WORKDIR /app-node
ARG PORT_BUILD=6000
ENV PORT=${PORT_BUILD}
EXPOSE ${PORT_BUILD}
COPY . .
RUN npm isntall
ENTRYPOINT npm start
```
Comando.
```
docker build -t faelk8/app-node:1.1 .
docker run -p 9090:6000 -d faelk8/app-node:1.1
```
* http://localhost:6000
* ARG: Para construção da imagem
* ENV: Para dentro do cotainer
* EXPOSE: Porta onde o serviço está sendo exposto

# Subindo a Imagem para o Docker Hub
```
docker tag faelk8/app-node:1.0 faelk8/app-node:1.0 
```
* http://localhost:9090 

# Persistência
Mapeando um diretório host para dentro do container.
```
docker run -it -v /home/rafael/volume:/app ubuntu bash
```
Semântica
```
docker run -it --mount type=bind,source=/home/rafael/volume,target=/app ubuntu bash
```
## Produção
Criando volume gerenciado pelo Docker.
```
docker volume create volume1
```
Mapeando o volume para o Docke.
```
docker run -it -v volume1:/app ubuntu bash
```
O arquivos são salvos em `/var/lib/docker/volumes`

Semântica
```
docker run -it --mount source=volume1,target=/app ubuntu bash
```
* Caso o volume não exista o Docker vai criar o volume.

## tmpfs
Só funciona em ambiente Linux.
```
docker run -it --tmpfs=/app ubuntu bash
```
* Cria um pasta temporária.
* Usado para dados sensíveis.
```
docker run -it --mount type=tmpfs,destination=/app ubuntu bash
```

# Redes
* Rede padrão bridge.
* Criando uma rende dentro do container.
```
docker run -it --name ubuntu --network minha-rede ubuntu bash
```
* Rede criadas criadas pelo usuário provém de forma automática um DNS entre containers.

# Docker Compose
Orquestração de vários containers em um só lugar.

# Comandos
| **Comandos** | **Descrição** |
|----------|---------------|
| docker images | Listar as imagens |
| docker inspect < container > | Inpecionar o container |
| docker history < imagem > |
| docker ps | Cotainer em execução |
| docker stop $(docker catainer ls -q) | Para todos os cotainers em execução |
| docker rm $(docker container ls -aq) | Remove todos os containers |
| docker rmi (docker image  ls -aq) | Remove todas as imagens |
| docker volume ls | Lista os volumes |
| docker network creat --drive bridge minha-rede | Cria uma rede como o nome minha-rede |