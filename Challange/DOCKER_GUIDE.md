Small docker guide
==================

## Network

### Docker network check

```bash
$ docker network ls
```

### Docker network creation(if not exists)

To create a docker network, you need to run the command below.

```bash
$ docker network create <name>
```

### Docker network - other commands

Consult using the help command

```bash
$ docker network --help
``` 

## Build image

To build an image, you need to run the command below.

```bash
$ docker build -t <name> <Dockerfile path>
``` 

## Run container

To run a container, you need to run the command below.

```bash
$ docker run --name <name> <image name>
```

You can also run the container in the background and other options. Use the help command to get more 
information related `docker run`.

```bash
$ docker run --help
```

