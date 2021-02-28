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

## ECR

```
# Create ECR repository
$ aws ecr create-repository --repository-name nuxt-ecs-sample

# Add a tag to docker image
$ docker tag nuxt-ecs-sample:1.0.0 <AWS_ACCOUNT_ID>.dkr.ecr.ap-northeast-1.amazonaws.com/nuxt-ecs-sample:1.0.0

# Login ECR
$ aws ecr get-login-password --region ap-northeast-1 | \
  docker login --username AWS --password-stdin <AWS_ACCOUNT_ID>.dkr.ecr.ap-northeast-1.amazonaws.com/nuxt-ecs-sample

# Push docker image to ECR
$ docker push <AWS_ACCOUNT_ID>.dkr.ecr.ap-northeast-1.amazonaws.com/nuxt-ecs-sample:1.0.0
```
