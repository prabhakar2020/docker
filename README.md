# Docker
Docker useful commands
-----

> **Execute docker**
>> docker pull busybox <br/>
>> docker run -it --name my_container /bin/sh<br/>
>> docker exec -it my_container /bin/sh<br/>

> **Running application as a container**
>> docker build -t "image_name" . <br/>
>> docker run --rm -p=5000:5000 -v `pwd`/data:/app/data image_name <br/>
>> docker run -it -p 9000:9000 --name sonar123 sonarqube<br/>
>> docker run -it -p 8000:8000 --name myjenkins jenkins<br/>
>> docker run -it --entrypoint=/bin/bash my-app<br/>
>> docker run -d -p 5000:5000 --name my-flask-application my-app<br/>
>> docker run -it -p 5000:5000 --name my-flask-application my-app<br/>
>> docker run --rm -p=6003:6003 -v `pwd`/my_data:/app/data image_name<br/>

> **Remove docker images**
>> docker rmi -f docker_imageID<br/>
>> docker rmi -f ec596bcaaddf<br/>

> **Remove all docker container**
>> docker rm -f $(docker ps -a -q)<br/>

> **Remove all docker running container**
>> docker rm -f $(docker ps -q)<br/>

> **Open container with interactive mode**
>> docker exec -it my-flask-application /bin/sh<br/>

> **Stop Container**
>> docker start container_ID<br/>
>> docker stop container_ID<br/>
>> docker stop $(docker ps -a -q)<br/>

> **Display logs**
>> docker container logs [OPTIONS] CONTAINER<br/>
>> docker container logs -f CONTAINER_ID<br/>

> **Building complete Application**
>> docker build -t my-flask-image .<br/>

>> docker build -t my-app .<br/>
>> docker run -it -p 6003:5000 --name my-flask-application image_name<br/>
>> docker run -it -p 6003:6003 --name my-flask-application image_name<br/>

> **Save Docker Image**
>> docker save py3alpine-image | gzip > py3alpine-image<br/>

> **Load Docker Image**
>> zcat image_name | docker load<br/>

> **Change Docker Image Name / tag**
>> docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]<br/>
>> docker tag 0e5574283393 fedora/httpd:version1.0<br/>


> **Select Environment**
>> eval $(minikube docker-env)<br/>


> **Reset Environment to docker**
>> eval $(minikube docker-env -u)<br/>

> **Docker Setup**
>> yum install docker<br/>
>> systemctl enable docker.service<br/>

> **Linux Operating system**
>> systemctl start docker.service ## <-- Start docker ##<br/>
>> systemctl stop docker.service ## <-- Stop docker ##<br/>
>> systemctl restart docker.service ## <-- Restart docker ##<br/>
>> systemctl status docker.service ## <-- Get status of docker ##<br/>

> **Windows Operating system**
>> Restart from Run -> services.msc -> choose **Docker Desktop Service**<br/>
>> Right click on **Docker Desktop Service** and choose restart/start/stop<br/>

> **Docker port forwarding**
>> ssh -i ~/.minikube/machines/minikube/id_rsa docker@$(minikube ip) -L \\*:30090:0.0.0.0:30090<br/>

> **Linking and working with multiple containers to perform single operation**
>> docker pull mysql<br/>
>> docker run --name easql -e MYSQL_ROOT_PASSWORD=abc123 -d mysql:latest<br/>
>> docker pull wordpress<br/>
>> docker run --name ealocal --link easql:mysql -p 8080:80 -d wordpress<br/>


> **Copy content from Docker container**
>> SYNTAX: docker cp SOURCE_PATH DESTINATION_PATH<br/>
>> docker cp CONTAINER_ID:FOLDER_PATH  LOCAL_DESTINATION_PATH<br/>
>> example: docker cp 07gsbsdh4563:/app/sample.txt  c:\\sample_data\\<br/>


> **Copy content from Local machine to Docker container**
>> SYNTAX: docker cp LOCAL_SOURCE_PATH DESTINATION_PATH<br/>
>> docker cp LOCAL_DESTINATION_PATH CONTAINER_ID:FOLDER_PATH  <br/>
>> example: docker cp sample.txt 07gsbsdh4563:/app/sample.txt<br/>

> **Execute command on docker container from your physical machine**
>> Syntax: docker exec -it container_id command<br/>
>> example: docker exec -it 07gsbsdh4563 ls <br/>
>> example: docker exec -it 07gsbsdh4563 cat sample.txt <br/>
>> Note: we can also use -d to run the command in ditached mode.

> **Docker inspect container**
>> docker inspect CONTAINER_ID<br/>

> **Docker create volume**
>> docker volume create my-vol<br/>

> **Docker list volumes**
>> docker volume ls<br/>

> **Docker inspect volume**
>> docker volume inspect VOLUME_NAME<br/>
>> docker volume inspect my-vol<br/>

> **Docker remove volume**
>> docker volume rm my-vol<br/>


> **Start a container with a volume**
>> docker run -d --name dev_testing -v my-vol:/app mysql:latest<br/>
>> docker run -d --name dev_testing --mount source=myvol2,target=/app mysql:latest<br/>
