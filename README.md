# ProfRamos.com

Landing page do Professor Gabriel Ramos - Direito Constitucional para Concursos.

## Estrutura

```
proframos/
├── index.html          # Página estática
├── Dockerfile          # Container nginx
├── docker-compose.yml  # Deploy com Traefik
└── README.md           # Este arquivo
```

## Deploy

### Pré-requisitos

- Docker + Docker Compose
- Traefik configurado em `/opt/traefik`
- Rede `proxy` criada: `docker network create proxy`
- DNS apontando para o servidor

### Subir o serviço

```bash
cd /opt/proframos
docker compose up -d --build
```

### Logs

```bash
docker compose logs -f
```

### Atualizar

```bash
git pull
docker compose up -d --build
```

## Traefik

O Traefik está em `/opt/traefik/` e gerencia:
- SSL automático via Let's Encrypt
- Redirect HTTP → HTTPS
- Redirect www → non-www
- Security headers

### Subir Traefik

```bash
cd /opt/traefik
docker compose up -d
```

## DNS

Certifique-se de que os registros DNS apontam para este servidor:

```
proframos.com      A     <IP_DO_SERVIDOR>
www.proframos.com  A     <IP_DO_SERVIDOR>
```

## Reverter / Diagnosticar

```bash
# Parar serviço
docker compose down

# Ver status
docker compose ps

# Ver logs do Traefik
docker logs traefik -f

# Verificar certificado SSL
curl -vI https://proframos.com 2>&1 | grep -E "SSL|cert|CN"
```

## Contato

- Instagram: https://instagram.com/proframos
- YouTube: https://youtube.com/@proframos
