# gatsby-dockerfile

Us this if you want to have acccess to gatsby develop in a docker container. This can be used to get a fake graphql microservice, since gatsby develop exposes a graphql api.

## Example usage:
(inside your gatsby fake ms)
Dockerfile:
```Dockerfile
FROM jokesdockerid/gatsby

EXPOSE 8000

WORKDIR /app
COPY ./package.json .
RUN yarn install && yarn cache clean
COPY . .
CMD ["gatsby", "develop", "-H", "0.0.0.0" ]
```

### build the docker image

```bash
docker build -t fake-ms .
```

### run the docker container

```bash
docker run -d -p 8000:8000 --name fake-ms fake-ms
```


The graphql api can then be reached at [localhost:8000/\_\_\_graphql](localhost:8000/___graphql)
