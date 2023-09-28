The challenge
=============

Get the [ze-delivery-challenge](https://github.com/merorafael/ze-delivery-challenge) project and follow the steps
below to reproduce all the steps learned in docker course.

## First step

Clone the project [ze-delivery-challenge](https://github.com/merorafael/ze-delivery-challenge) into your computer.
After that, copy `.env.local` file to `.env` file. This file will be used to configure the environment variables.

Example:

```bash
$ git clone git@github.com:merorafael/ze-delivery-challenge.git
$ cd ze-delivery-challenge
$ cp .env.local .env
```

## Second step

Create a docker network called `api-network`. This network will be used to connect the containers.
Check this [guide](DOCKER_GUIDE.md) to see how to create a docker network.

Docker network create an isolated network for containers used by an application.

<small>Answer: `docker network create api-network`</small>

## Third step

Create a `Dockerfile` in the root project directory. This Dockerfile must have the following instructions:

1. Use `node:lts-alpine`(`FROM` keyword) image;
2. Copy all project files on project root directory to container(`COPY` keyword);
3. Install all dependencies using the command `yarn install`(`RUN` keyword);
4. Expose the port `3000`(`EXPOSE` keyword);
5. Run the command `yarn start`(`CMD` keyword).

Docker build create an image used to start a container.

<small>
Answer: https://github.com/merorafael/ze-delivery-challenge/blob/main/Dockerfile
</small>

## Fourth step

Build an image using the command `docker build`. The image name must be `api:latest`. 

Check this [guide](DOCKER_GUIDE.md) to see how to do it.

<small>Answer: `docker build -t api:latest .`</small>

## Fifth step

Start a MongoDB container using the command `docker run` with the environment variable `MONGO_INITDB_DATABASE=challenge`.
The container name must be `database` and its must in the `api-network` network.

Check this [guide](DOCKER_GUIDE.md) to see how to do it.

<small>Answer: `docker run -d -p 27017:27017 --network api-network --name database -e "MONGO_INITDB_DATABASE=challenge" mongo`</small>

## Sixth step

Start the API container using the command `docker run`.
The container name must be `api` and its must in the `api-network` network.

<small>Answer: `docker run -d -p 3000:3000 --network api-network --name api api:latest`</small>
