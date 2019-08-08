## DOCKER run this project

build docker container

~~~
# for dev-env
# run in cli
docker build -f Dockerfile.dev -t "<images-name>/<container-name>:dev" .

docker run -p 3001:3000 -v /app/node_modules -v $(pwd):app/ <images-name>/<container-name>
~~~

## docker-compose run this project
~~~
# see in the root folder there's docker-compose.yml
# run cli
docker-compose up
~~~

~~~
# for prod-env
docker build .

# run nginx
docker run -p 8080:80 <container-id>
~~~

## ATTENTION

add this to your **.travis.yml** file
~~~

deploy:
  provider: elasticbeanstalk
  region: "us-west-2"                                             # the region you choose
  app: "docker"                                                   # a name that you setup in aws
  env: "Docker-env"                                               # a name that revere as the environment
  bucket_name: "elasticbeanstalk-us-west-2-<your-app-id>"         # << change this line
  bucket_path: "docker"                                           # the name same as app names
  on:
    branch: master
  access_key_id: $AWS_ACCESS_KEY
  secret_access_key:
    secure: "AWS_SECRET_KEY"                                    # make sure you put double quote
~~~
