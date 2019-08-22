# Projeto para desenvolver técnicas com Docker
## O que aprendi durante o curso:
- Utilizar containers para simplificar seus processos.
- Criar imagens com seus produtos.
- Publicar suas imagens em ambientes na nuvem, seja para distribuição ou execução dos serviços.
- Gerenciar conjuntos de micro serviços.
- Utilizar ferramentas diversas de integração contínua baseado em containers.

## Como Usar:
1. Tenha o Docker e  Docker-Compose instalados.
2.  Baixe o projeto.
3.  Dentro de cada pasta execute os comando listados.
------------
### primeiro-build
```shell
docker image build -t ex-simple-build .
docker image ls
docker container run -p 80:80 ex-simple-build
```
**Serviço disponível em:** http://localhost

------------
### build-com-arg
```shell
docker image build -t ex-build-arg .
docker container run ex-build-arg bash -c 'echo $S3_BUCKET'
```
**Saída esperada:** files

```shell
docker image build --build-arg S3_BUCKET=myapp -t ex-build-arg .
docker container run ex-build-arg bash -c 'echo $S3_BUCKET'
```
**Saída esperada:** myapp

------------
### build-com-copy
```shell
docker image build -t ex-build-copy .
docker container run -p 80:80 ex-build-copy
```
**Serviço disponível em:** http://localhost

------------
### build-dev
```shell
docker build -t ex-build-dev .
docker run -it -v $(pwd):/app -p 80:8000 ex-build-dev
```
**Serviço disponível em:** http://localhost

------------
### ex-volume/html
```shell
docker container run -p 8080:80 -v $(pwd)/html:/usr/share/nginx/html nginx

```
**Serviço disponível em:** http://localhost:8080

------------
### node-mongo-compose
```shell
docker-compose up
```
**Serviço disponível em:** http://localhost

**Para finalizar o compose**
```shell
docker-compose down
```
------------
### email-worker-compose
```shell
docker-compose up -d
docker-compose scale worker=3
docker-compose logs -f -t worker

```
**Serviço disponível em:** http://localhost

**Para finalizar o compose**
```shell
docker-compose down
```
------------
Link do curso: https://www.udemy.com/curso-docker/
