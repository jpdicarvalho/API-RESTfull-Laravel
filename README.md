## Preparação Inicial
Construir os containers:
docker-compose build

Subir os containers em segundo plano:
docker-compose up -d

Verificar o status dos containers:
docker-compose ps

## Gerenciar Containers
Acessar um container específico (exemplo: laravel-app):
docker exec -it laravel-app bash

Verificar logs de um container (exemplo: laravel-app):
docker logs laravel-app

Parar containers sem removê-los:
docker-compose stop
Encerrar e remover containers, redes e volumes temporários:

docker-compose down

## Manutenção
Recriar containers após alterações:
docker-compose up -d --build

Remover imagens e volumes não utilizados:
docker system prune -a -f --volumes

Listar volumes existentes:
docker volume ls