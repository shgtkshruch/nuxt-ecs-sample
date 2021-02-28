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

## Register task definition

```
$ aws ecs register-task-definition --cli-input-json file://deploy\/taskdef.json
```

## Creat ECS service

1. Create ECS Cluster in AWS console.（nuxt-ecs-sample-cluster）
2. Creat ECS sercice with AWS CLI
```
$ aws ecs create-service --service-name nuxt-service --cli-input-json file://deploy\/create-service.json

# Confirm
$ aws ecs describe-services --cluster nuxt-ecs-sample-cluster --services nuxt-service
```
