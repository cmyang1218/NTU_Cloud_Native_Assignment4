# NTU_Cloud_Native_Assignment4

## How to build the docker image

```shell
docker build -f ./Dockerfile.app1 -t cmyang1218/2025cloud:app1 .
docker build -f ./Dockerfile.app2 -t cmyang1218/2025cloud:app2 .
```

## How to run the docker container
```shell
docker run -it cmyang1218/2025cloud:app1 /bin/sh
docker run -it cmyang1218/2025cloud:app2 /bin/sh
```