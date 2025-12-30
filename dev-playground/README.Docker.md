# Docker para Dev-Playground

Este diretório contém os arquivos necessários para executar o dev-playground em um container Docker.

## Pré-requisitos

- Docker instalado
- Docker Compose (opcional, mas recomendado)

## Como usar

### Com Docker Compose (Recomendado)

1. Build e iniciar o container:
```bash
docker-compose up -d
```

2. Acessar o playground:
```
http://localhost:1234
```

3. Parar o container:
```bash
docker-compose down
```

### Com Docker

1. Build da imagem:
```bash
docker build -t pdfmake-dev-playground -f dev-playground/Dockerfile ..
```

2. Executar o container:
```bash
docker run -d -p 1234:1234 --name pdfmake-playground pdfmake-dev-playground
```

3. Acessar o playground:
```
http://localhost:1234
```

4. Parar o container:
```bash
docker stop pdfmake-playground
docker rm pdfmake-playground
```

## Desenvolvimento com Hot Reload

O docker-compose.yml está configurado com volumes para permitir desenvolvimento em tempo real:
- Alterações em `public/` são refletidas imediatamente
- Alterações em `server.js` requerem reiniciar o container:
  ```bash
  docker-compose restart
  ```

## Personalização

### Mudar a porta

Edite o `docker-compose.yml` ou use a variável de ambiente:
```bash
PORT=3000 docker-compose up
```

### Build para produção

Para um build otimizado sem volumes de desenvolvimento, edite o `docker-compose.yml` e remova a seção `volumes`.
