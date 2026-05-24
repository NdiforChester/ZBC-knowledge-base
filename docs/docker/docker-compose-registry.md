## Presentation

# What is Docker Compose
Docker Compose is a tool that lets you define and run multiple containers together using a single configuration file.
Instead of running many docker run commands one by one, you describe everything in a file and start it all at once.
Docker Compose = “Run multi-container apps with one command”
Use docker compose when you have more than one container,when you building a real application and when you want easy setup and reapeatability.
Docker compose takes care of creating a common network for all the containers to communicate
These commands also known as configuration are written in a yaml file which is understood by the computer.

With docker compose, you use a single YAML file to configue and maiantain your applications services.With a single command,
With a single command, you creat and start all the services from your configuration.This will allow all the containers to communicate with each other and work together as a single applica>

# Simple idea

Think of it like this:
Docker = runs one container
Docker Compose = runs a full system (multiple containers)

For example:
Frontend (React)
Backend (Node.js / Python)
Database (MySQL / MongoDB)

All running together as one app.
# Differences between Docker and Docker-compose

| Docker              | Docker Compose           |
| ------------------- | ------------------------ |
| Runs one container  | Runs multiple containers |
| Manual commands     | One YAML file            |
| Hard to manage apps | Easy full-stack setup    |


# Format for docker compose file(docker-compose.yaml)
version: '3'                                   # latestversion of docker compose file format
services:                                      # services is a section where you define all the containers you want to run
  web-server:                               # name of the service(container), you can choose any name
    image: 'nginx'                               # the image to use for this service, in this case nginx
    ports:                                     # ports section is where you define the port mapping for this service
      - "80:80"
      environment:
                                    # maps port 80 of the container to port 80 of the host machine(host:container)
  db-server:                                          # another service named db
    image: "mysql"
    ports:                                     # ports section is where you define the port mapping for this service
      - "3306:3306"                            # maps port 3306 of the container to port 3306 of the host machine(host:container)
    environment:                               # environment variables for the db service
      MYSQL_ROOT_PASSWORD: example             # setting the root password for mysql

          MYSQL_DATABASE: mydb                   # creating a database named mydb
      MYSQL_USER: user                       # creating a user named user
      MYSQL_PASSWORD: password               # setting the password for the user

# NB: The above is a simple example of a docker compose file that defines two services: a web server using the nginx image and a database server using the mysql image. The web server is m>
 and the database server has environment variables set for the root password, database name, user, and user password.
.
# Example 2 of docker compose file where both services have different environment variables
version: '3'                                           latest version of docker compose file format
services:                                              services is a section where you define all the containers you want to run
  mongodb:                                             name of the service, you can choose any name(container name)
    image: mongo                                       the image to use for this service, in this case mongo
    ports:                                             ports section is where you define the port mapping for this service
      - "27017:27017"
    environment:                                       environment variables for the mongodb service
      MONGO_INITDB_ROOT_USERNAME: root                 setting the root username for mongodb
      MONGO_INITDB_ROOT_PASSWORD: example              setting the root password for mongodb
      MONGO_INITDB_DATABASE: mydb                      creating a database named mydb
  redis:                                               second service named redis(2nd container)
    image: redis                                       the image to use for this service, in this case redis
    ports:                                             ports section is where you define the port mapping for this service
      - "6379:6379"
    environment:                                       environment variables for the redis service
      REDIS_PASSWORD: example                          setting the password for redis

# NB: In this example, we have two services: mongodb and redis. The mongodb service uses the mongo image and is mapped to port 27017 on the host machine. It also has environment variables>
 the redis image and is mapped to port 6379 on the host machine. It has an environment variable set for the redis password.

 # when one service depends on another service, you can use the depends_on option to specify the dependency. For example, if the web-server service depends on the db-server service, you c>
depends_on:
  - db-server
  for example
version: '3'
services:
  web-server:
    image: 'nginx'
    ports:
      - "80:80"
    depends_on:
      - db-server
        db-server:
    image: "mysql"
    ports:
      - "3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: mydb
      MYSQL_USER: user
      MYSQL_PASSWORD: password
In this example, the web-server service depends on the db-server service. This means that when you run docker-compose up,
 it will start the db-server service first before starting the web-server service. This ensures that the database server is up and running before the web server tries to connect to it.
- Save the above content in a file named container.yaml in the same directory where you want to run the containers. Then, you can use the following commands to manage your containers:

docker-compose  -f container.yaml up # This command will start the containers defined in the container.yaml file. The -f flag is used to specify the file name. If you don't specify the fi>
docker-compose  -f container.yaml down # This command will stop and remove the containers defined in the container.yaml file. It will also remove the network created for the containers.
docker-compose  -f container.yaml ps # This command will show the status of the containers defined in the container.yaml file. It will display the container ID, name, status, and ports.
docker-compose  -f container.yaml logs # This command will show the logs of the containers defined in the container.yaml file. It will display the output of the containers in real-time. Y>
docker-compose  -f container.yaml exec web-server bash # This command will open a bash shell inside the web-server container. You can replace web-server with the name of any other service>
docker-compose  -f container.yaml build # This command will build the images for the services defined in the container.yaml file. It will look for a Dockerfile in the current directory fo>
docker-compose  -f container.yaml restart # This command will restart the containers defined in the container.yaml file. It will stop the containers and start them again.
docker-compose  -f container.yaml scale web-server=3 # This command will scale the web-server service to 3 instances. It will create 3 containers for the web-server service.
docker-compose  -f container.yaml stop # This command will stop the containers defined in the container.yaml file. It will not remove the containers, so you can start them again later.
docker-compose  -f container.yaml start # This command will start the containers that were stopped using the stop command. It will not create new containers, but will start the existing o>
docker-compose  -f container.yaml rm # This command will remove the containers defined in the container.yaml file. It will stop the containers if they are running and then remove them. Us>
docker-compose  -f container.yaml up -d # This command will start the containers defined in the container.yaml file in detached mode. The -d flag stands for detached, which means the cont>
docker images prune # This command will remove all unused images from your system. It will prompt you to confirm before deleting the images. Use this command with caution as it will delet>
docker container prune # This command will remove all stopped containers from your system. It will prompt you
Alternative, you can navigate to the directory where the container.yaml file is located and run the commands without the -f flag, as docker-compose will look for a file named docker-compo>
-when you run docker-compose up, it will create a network for the containers to communicate with each other. You can see the network by running docker network ls. The containers will be c>
This allows the containers to interact with each other without needing to know their IP addresses.
-when you run docker-compose down, it will stop the containers and remove the network created for them. This means that the containers will no longer be able to communicate with each othe>
please note that volume data will not be removed when you run docker-compose down, so any data stored in volumes will persist even after the containers are stopped and removed. If you wan>
which will stop the containers, remove them, and also remove any associated volumes.

# NB: Docker compose is part of application code meaning it can be pushed to a git repository and shared with other developers. However environment variables that contain sensitive inform>
Instead, you can use a .env file to store these variables and reference them in the docker-compose file. This way, you can keep sensitive information out of version control and share the >
now in the docker compose file, you can reference the environment variables from the .env file like this:
version: '3'
services:
  web-server:
    image: 'nginx'
    ports:
      - "80:80"
    environment:
      DB_HOST: ${DB_HOST} # referencing the DB_HOST variable from the .env file
      DB_USER: ${DB_USER} # referencing the DB_USER variable from the .env file
           DB_PASSWORD: ${DB_PASSWORD} # referencing the DB_PASSWORD variable from the .env file
Then go to CLI to set the variables and run
export DB_USER=user
export DB_PASSWORD=password
Now, when you run docker-compose up, it will use the values from the .env file for the environment variables in the docker-compose file. This allows you to keep sensitive information out >
control and share the docker-compose file without exposing secrets.


# Docker Registry
A Docker registry is a storage and distribution system for Docker images.It’s like a GitHub for Docker images.
- What it does

A Docker registry stores and lets you:

Upload (push) Docker images
Download (pull) Docker images
Share images with others or across servers


- Types of Docker registries
1. Public registry
Anyone can use it.

Example: Docker Hub
The default public registry
Stores millions of images like nginx, ubuntu, etc.

2. Private registry
Used by companies internally.

Hosted on AWS, Azure, GCP, or your own server
Keeps images secure and private

3. Self-hosted registry
You run your own registry server:

# What is ECR(Elastic container image)
ECR is a private registry for docker.You can creat a repository on aws .Note that only one image can be push to a particular
repository.
The steps are as follows
1. Login to aws account the search "ECR"
2. Click on creat ECR and specify the image name.Notice the domain name of the image or URL set by aws.
3. Click on the image to push then select "view push commands" to copy the first login command and paste in command line in order to authenticxate yourself into the preivate repo.click en>
is now link to your aws account
4. skip step 2 becasue you are already build an image and next go to step 3.copy it and paste in on CLI and the enter.
5. run docker images to check new image name and tag
6.Copy the last step 4 and the paste in CLI to push the image then execute the command and you should be abel to see the image in repository.
Demo
🏠 ~ ➜ aws configure
AWS Access Key ID [****************US4Z]: your access key
AWS Secret Access Key [****************ThhZ]: your secret key
Default region name [eu-north-1]: eu-north-1
Default output format [json]: json
🏠 ~ ➜ docker images
REPOSITORY                                            TAG       IMAGE ID       CREATED        SIZE
359373592373.dkr.ecr.eu-north-1.amazonaws.com/nginx   latest    6c3a6ea6608c   32 hours ago   161MB
nginx                                                 latest    6c3a6ea6608c   32 hours ago   161MB
🏠 ~ ➜ docker tag nginx:latest 359373592373.dkr.ecr.eu-north-1.amazonaws.com/nginx:latest
🏠 ~ ➜ docker push 359373592373.dkr.ecr.eu-north-1.amazonaws.com/nginx:latest
The push refers to repository [359373592373.dkr.ecr.eu-north-1.amazonaws.com/nginx]
7496ac117dcc: Pushed
01183ec0d67d: Pushed
0d3c8058c8ac: Pushed
213cb1eb41d9: Pushed
e1655f27a627: Pushed
e3c5bf51d825: Pushed
6d7c150df58d: Pushed
latest: digest: sha256:ced76dcf658ca09d00cf4f8966a38d556685159a023d3407a6371a7eb77a947f size: 1778
🏠 ~ ➜
Note that you can push several image version to a docker repository but you cannot push different images to same docker repository.
