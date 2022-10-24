# Dockerfile and container image

Drupal can run on amd64 or arm64 hosting platforms. AWS ECS Fargate support both
platforms for linux. In this directory are the container files for building the
desired custom image. Alternatively, if no cusotmizations or updates are needed
you can supply the public image name for the target hosting platform.

Supported architectures images can be found on 
 - [Docker Hub](https://hub.docker.com/_/drupal)

## Build image, tag, and upload to AWS ECR

```bash
export AWS_ACCOUNT="123456789"
export AWS_REGION="us-east-1"

aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin "${AWS_ACCOUNT}".dkr.ecr."${AWS_REGION}".amazonaws.com
docker build -t drupal:v1 .
docker tag drupal:v1 "${AWS_ACCOUNT}".dkr.ecr."${AWS_REGION}".amazonaws.com/drupal:v1
docker push "${AWS_ACCOUNT}".dkr.ecr."${AWS_REGION}".amazonaws.com/drupal:v1
```

> **Note**
> Running Drupal requires a database such as mysql.

## Run locally

Refer to the section `"How to use this image"` on [drupal - Official image | Docker Hub](https://hub.docker.com/_/drupal)



