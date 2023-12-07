<h1 align="center">
  <img src="./../image/docker-logo.png" alt="Docker" width=180px height=120px >
  <br>
  Docker
</h1>

<div align="center">

[![Status](https://img.shields.io/badge/version-1.0-blue)]()
![Static Badge](https://img.shields.io/badge/status-desenvolvimento-deve)

</div>

# Primeiros Passos
## Ubuntu

Baixa a imagem e roda o Ubuntu no modo iterativo.
```
docker run -it ubuntu bash
```

## Nginx
Baixa a imagem e roda o nginx.
```
docker run nginx
```

Baixa a imagem e roda o nginx e libera a porta para acesso.
```
docker run -p 8080:80 nginx
```

Baixa a imagem e roda o nginx, libera a porta para acesso e o terminal.
```
docker run -d -p 8080:80 nginx
```
Coloca um nome no container
```
docker run -it --name nginx -d -p 8080:80 nginx
```
Modo iterativo.
```
docker exec nginx bash
```

# Imagem
Criando uma imagem dentro da pasta ubuntu.

Dockerfile
```
# baixa a imagem
FROM ubuntu:latest

# RUN apt-get update
# RUN apt-get install vim -y

ENTRYPOINT [ "echo", "Cante !!!\n" ]

# no terminal faz a impressão 
CMD ["Eu sei que vai dar merda\nMas faço mesmo assim\nEu sei como começa, mas ninguém sabe o fim\n..."]

```

Construindo a imagem
```
docker build -t faelk8/ubuntu-cante .
```
# Comandos

| **Comandos** | **Descrição** |
|----------|---------------|
| docker exec -it < nome > bash | Entra no container no modo iterativo quando o container está ativo |
| docker images | Mostras as imagens baixadas |
| docker volume prune -f | Remove todos os volumes |
| docker volume rm (docker volume ls -q) | Apaga todos os volumes |
| docker ps | Mostra  os container |
| docker ps -a  | Mostra  todos os container ativos e inativos |
| docker pull < imagem > | Baixa a imagem |
| docker rm < CONTAINER ID > | Deleta o container parado|
| docker rm < CONTAINER ID > -f | Força a deleção do container |
| docker rmi < imagem > | Apaga a imagem |
| docker run -d -p 8080:80 < imagem > | Executa na porta 80 e libera o terminal |
| docker run -d --name < nome > < imagem > | Executa o container com nome e libera o terminal |
| docker run -it < imagem > bash | Executa no mode iterativo |
| docker run -it --rm < imagem > bash | Executa no mode iterativo e quando sair é removido |
| docker start < CONTAINER ID > | Inica o container | 
| docker stop < CONTAINER ID > | Para o container | 
| docker volume ls | Mostra as pasta |