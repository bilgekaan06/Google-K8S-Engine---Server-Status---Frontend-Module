# Google-K8S-Engine-Server-Status-Frontend-Module

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
@RestController
public class ServerInfoController {
    private final AtomicLong counter = new AtomicLong();
    SimpleDateFormat formatter = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss");
    @GetMapping("/serverinfo")
    @CrossOrigin("*")
    public List<ServerInfo> status(){
        // obtain a hostname. First try to get the host name from docker container (from the "HOSTNAME" environment variable)
        String hostName = System.getenv("HOSTNAME");
        // get the os name
        String os = System.getProperty("os.name");
        //get the IP address
        String ipAddress = "127.0.0.1"; //dummy value
        InetAddress ipUtils = null;
        try {
            ipUtils = InetAddress.getLocalHost();
            ipAddress = ipUtils.getHostAddress();
        } catch (UnknownHostException e) {
            e.printStackTrace();
        }
        //get the access date
        Date date = new Date();
        if (hostName == null || hostName.isEmpty()) {
            try {
                ipUtils = InetAddress.getLocalHost();
                ipAddress = ipUtils.getHostAddress();
                hostName = ipUtils.getHostName();
            } catch (UnknownHostException e) {
                e.printStackTrace();
                hostName = "Unknown";
            }
        }
        List <ServerInfo> serverInfos = new ArrayList<>();
        serverInfos.add(new ServerInfo(counter.incrementAndGet(), "Google Kubernetes Engine", hostName, ipAddress, os, formatter.format(date)));
        return serverInfos;
    }
}
```
# Getting Started

1. Download the project using git:
```
git clone https://github.com/bilgekaan06/Google-K8S-Engine-Server-Status-Frontend-Module.git
```
2. Install npm packages
```
npm install
```
3. Compiles and hot-reloads for development
```
npm run serve
```
4. Compiles and minifies for production
```
npm run build
```
