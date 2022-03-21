<template>
    <div class= "container">
            <h1 class="text-center"> Server Info </h1>
            <table class="table table-striped">
                <thead>
                    <th> ID </th>
                    <th> AppName </th>
                    <th> Hostname </th>
                    <th> IP Address </th>
                    <th> Operating System </th>
                    <th> Access Date </th>
                </thead>
                <tbody>
                    <tr v-for = "serverinfo in serverinfos" v-bind:key="serverinfo.id">
                        <td> {{serverinfo.id}} </td>
                        <td> {{serverinfo.appName}} </td>
                        <td> {{serverinfo.hostName}} </td>
                        <td> {{serverinfo.ipAddress}} </td>
                        <td> {{serverinfo.os}} </td>
                        <td> {{serverinfo.date}} </td>
                    </tr>
                </tbody>                    
            </table>
    </div>
</template>

<script>
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
</script>

<style>

</style>