# Xpress IDE devfile registry

This repository holds Devfiles for Xpress.

## che-devfile-registry

This repository is a forked from che-devfile-registry repository in github.
Please refer to https://github.com/eclipse/che-devfile-registry.

## Changes in this repository

Refer to the source code folder `devfiles`.
All the devfiles needed for other languages have been removed.
A folder named xpress containing the devfile needed for Xpress IDE has been added.

# Devfile registry image

Reference : https://github.com/eclipse/che-devfile-registry#build-eclipse-che-devfile-registry-docker-image

## Create devfile registry image
* Clone the repository `che-devfile-registry` from bitbucket
* Build devfile registry image using the docker script under deploy folder:
```
docker build . -f Dockerfile --no-cache -t che-devfile-registry
```

## Push devfile registry image to Amazon ECR
* Open ECR service through AWS Console page.
* Create repository, provide the name as `che-devfile-registry`
* Click on the button "View push commands” for further instruction on pushing the image into the ECR (repository).

## Setup che to create devfile registry instance from the above image
* Edit the file `che/deploy/kubernetes/helm/che/custom-charts/che-devfile-registry/values.yaml`
* Modify `image:` parameter to point to the image stored in ECR. e.g.,
```
image: 055800582139.dkr.ecr.us-east-1.amazonaws.com/che-devfile-registry:latest
```
