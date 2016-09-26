# Sentry docker-compose.yml

Docker-compose file for sentry.
Just clone and run ```docker-compose up``` to start sentry.

## Generate secret-key
```
docker run --rm sentry config generate-secret-key
```

## Initialize tables

```
docker run -it --rm -e SENTRY_SECRET_KEY='<secret-key>' --link sentry-postgres:postgres --link sentry-redis:redis sentry upgrade
```

## Create the initial user
```
docker run -it --rm -e SENTRY_SECRET_KEY='<secret-key>' --link sentry-redis:redis --link sentry-postgres:postgres sentry createuser
```
