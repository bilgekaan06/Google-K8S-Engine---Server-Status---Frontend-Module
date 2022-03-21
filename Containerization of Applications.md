# For the Vue Application

* All following commands were run on Ubuntu OS.
## Prerequisites
* Firstly, backup all project directory
```
zip -r frontend-app.zip frontend-app/
```
* Change the current working directory to frontend-app then create 2 new files named default.conf and Dockerfile. To access the files I used click [Dockerfile](https://github.com/bilgekaan06/Google-K8S-Engine-Server-Status-Frontend-Module/blob/main/Dockerfile), [default.conf](https://github.com/bilgekaan06/Google-K8S-Engine-Server-Status-Frontend-Module/blob/main/default.conf)

Let's take a closer look at default.conf 
```
server {
        listen 80;
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    location /
        {
        }
    location /serverinfo
        {
            proxy_pass http://backend:8080/serverinfo #For forwarding requests to backend application service
        }

}
```

* Before the building step, you must delete the node_modules directory.
* The frontend app must run on a web server that's why built a web server in the Dockerfile. [Reference](https://v2.vuejs.org/v2/cookbook/dockerize-vuejs-app.html)
## Build the Docker Image
* In the frontend-app directory, to build Dockerfile run the following command:
```
docker build -t apismellifica/vuejs-frontend:1.5 .
docker build -t europe-central2-docker.pkg.dev/cyangate/task-repo/vuejs-frontend:1.5 .
```
* Example: docker build -t myreponame:projectname:tag [docker build](https://docs.docker.com/engine/reference/commandline/build/)
## Push the Image to Docker Hub and Google Cloud Artifact Registry
```
docker push apismellifica/vuejs-frontend:1.5
docker push europe-central2-docker.pkg.dev/cyangate/task-repo/vuejs-frontend:1.5
```
* Example: docker push registryhost [docker push](https://docs.docker.com/engine/reference/commandline/push/)
