# nuxt-ecs-sample

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

## Docker

```
$ docker pull nginx
$ docker build -t nuxt-ecs-sample:1.0.0 .
$ docker run -p 8080:80 nuxt-ecs-sample:1.0.0
# Open localhost:8080 in your browser
```
