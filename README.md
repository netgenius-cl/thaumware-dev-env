# Thaumware Dev Stack (ligero)

## Levantar (mínimo)

cp .env.example .env
docker compose up -d

Servicios:

- Postgres: 127.0.0.1:5433 (user: PG_USER, db: PG_DATABASE)
- Redis: 127.0.0.1:6379
- Mailpit UI: http://localhost:8025 (SMTP: 127.0.0.1:1025)
- Adminer: http://localhost:8081
- Dozzle logs: http://localhost:9999

### Extras

- MySQL: docker compose --profile mysql up -d (host 127.0.0.1:3307)
- Meilisearch: docker compose --profile search up -d (http://localhost:7700)
- MinIO: docker compose --profile storage up -d (http://localhost:9001)

## Seeds

Coloca SQL en `initdb/postgres` o `initdb/mysql` **antes del primer arranque**.

## Laravel .env ejemplo (Postgres)

DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5433
DB_DATABASE=thaum_dev
DB_USERNAME=thaum
DB_PASSWORD=thaum_secret

CACHE_DRIVER=redis
SESSION_DRIVER=redis
QUEUE_CONNECTION=redis
REDIS_HOST=127.0.0.1
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=127.0.0.1
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="dev@thaumware.local"
MAIL_FROM_NAME="Thaumware Dev"

# Meilisearch (opcional)

SCOUT_DRIVER=meilisearch
MEILISEARCH_HOST=http://127.0.0.1:7700
MEILISEARCH_KEY=dev_master_key_change_me

# MinIO/S3 (opcional)

FILESYSTEM_DISK=s3
AWS_ACCESS_KEY_ID=minioadmin
AWS_SECRET_ACCESS_KEY=minioadmin
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=thaum-dev
AWS_URL=http://127.0.0.1:9000
AWS_ENDPOINT=http://127.0.0.1:9000
