# Sentry docker-compose.yml

Docker-compose file for sentry.
Just clone and run ```docker-compose up``` to start sentry.

## Generate secret-key
```
docker run --rm sentry config generate-secret-key
```

## Initialize tables & create initial user

```
source .env
docker run -it --rm -e SENTRY_SECRET_KEY="$SECRET_KEY" -e SENTRY_REDIS_HOST=redis -e SENTRY_POSTGRES_HOST=postgres -e SENTRY_DB_USER=sentry -e SENTRY_DB_PASSWORD=secret --link sentrydocker_sentry-postgres_1:postgres --link sentrydocker_sentry-redis_1:redis --net sentrydocker_default sentry upgrade
```
