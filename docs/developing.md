# Developing

## Server

### Running

```
docker-compose \
    -f docker/docker-compose.yml \
    -f docker/docker-compose.dev.yml \
    --project-directory . \
    up --build
```
Runs the server with automatic reload enabled on http://0.0.0.0:80.

### Production

```
docker-compose \
    -f docker/docker-compose.prod.yml \
    --project-directory . \
    up --build 
```
Runs the server on http://0.0.0.0:80.

### Testing

1. Start the container.
    ```
    docker-compose -f docker/docker-compose.yml -f docker/docker-compose.test.yml --project-directory . 
        run --rm prototype sh
    ```
1. Test (e.g., `gradle test`) whenever you want. Test reports are saved to `build/reports/tests/test/`.
1. Run `exit` to shut down the environment.

## Spec

[`docs/openapi.yaml`](openapi.yaml) is the OpenAPI specification.

### Mock Server

```
npx @stoplightio/prism mock docs/openapi.yaml
```
The mock server will be running on http://localhost:4010.

### Testing

```
npx @stoplight/spectral lint docs/openapi.yaml
```

### Documentation

- Develop by serving and watching on http://127.0.0.1:8080: `npx redoc-cli serve docs/openapi.yaml -w`
- Build a production file named `redoc-static.html`: `npx redoc-cli bundle docs/openapi.yaml --title 'Backend Prototype'`