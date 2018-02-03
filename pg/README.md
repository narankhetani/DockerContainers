# Build Docker container
```docker build --rm --tag pg:1.0 .```

# Run
```
docker run --privileged --name pg -it -d -p 5432:5432 -e POSTGRES_PASSWORD="docker" pg:1.0
```
