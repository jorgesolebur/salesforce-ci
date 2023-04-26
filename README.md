# salesforce-ci

Docker Images we use for different purposes

- salesforce-ci :
  This image is used for Salesforce Continuous Integration. It contains all CLI & plugins necessary to deploy and automate build.
  To build a new image, re-execute the dockerfile, or run the following command :

```
docker build --pull --rm -f "salesforce-ci/dockerfile" -t jorgesolebur/salesforce-ci:tagName "salesforce-ci"
```

where tagname is the name of the tag you want to assign to that image. Once this is done you will need to push the image to the registry:

```
docker push jorgesolebur/salesforce-ci:tagName
```

To create an interactive container that does not exit immediately, run the following

```
docker run -dit jorgesolebur/salesforce-ci:latest
```

To delete all cache use the following

```
docker system prune -a
```

- gh-runner-image: This image is used to be ran in a self-hosted github action runner

```
$ docker build --tag runner-image .
$ docker run \
  --detach \
  --env ORGANIZATION=<YOUR-GITHUB-ORGANIZATION> \
  --env ACCESS_TOKEN=<YOUR-GITHUB-ACCESS-TOKEN> \
  --name runner \
  runner-image`
```
