# Google-K8S-Engine---Server-Status---Frontend-Module

# Introduction
The application shows some server information of the servers or containers it is running on.
# Description
The application consists of two modules, these are: 
Frontend Module and Backend Module
The frontend module was created using Vue. therefore all dependencies were added package.json file, the backend module was created using Java 11 and the backend module was built using Maven therefore all dependencies were added pom.xml file.

To establish communication between frontend and backend was used [Axios JavaScript library](https://axios-http.com/docs/intro). In the frontend side, this function was used:
```
import axios from "axios"
export default{
    
    data() {
        return{
            serverinfos : []
        }
    },
    mounted(){
        axios
        .get('http://localhost:8080/serverinfo')     
        .then(response => {
            this.serverinfos = response.data;
        })
            }
    
};
```
In Backend:
```

```
