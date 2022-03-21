# For the Vue Application

* All following commands were run on Ubuntu OS.
## Prerequisites
* Firstly, backup all project directory
```
zip -r frontend-app.zip frontend-app/
```
* Change the current working directory to frontend-app then create 2 new files named default.conf and Dockerfile. To access the files are I used [Dockerfile](http://test) [default.conf](https://test)
* Before building step, you must delete node_modules directory.

* The frontend app must run on a web server that's why built a web server in the Dockerfile. [Reference](https://v2.vuejs.org/v2/cookbook/dockerize-vuejs-app.html)
## Build the Docker Image
* In the frontend-app directory, to build Dockerfile run the following command:
```
docker build -t apismellifica/vuejs-frontend:1.0
```
* Example: docker build -t myreponame:projectname:tag [docker build](https://docs.docker.com/engine/reference/commandline/build/)
## Push the Image to Docker Hub
```
docker push apismellifica/vuejs-frontend:1.0
```
