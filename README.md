# ProfRamos.com

Landing page do Prof. Gabriel Ramos - Direito Constitucional para Concursos.

## Deploy

```bash
# Iniciar Traefik (primeira vez)
cd /opt/traefik && docker compose up -d

# Iniciar o site
cd /opt/proframos && docker compose up -d --build
```

## Estrutura

- `index.html` - Página estática
- `Dockerfile` - Container nginx
- `docker-compose.yml` - Configuração com Traefik labels

## DNS

- `proframos.com` → A → 84.247.186.181
- `www.proframos.com` → A → 84.247.186.181

## HTTPS

Certificados automáticos via Let's Encrypt (Traefik).
