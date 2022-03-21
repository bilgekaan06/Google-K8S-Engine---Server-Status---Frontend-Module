# Upload the Project Google Cloud
* To run all application and its replicas on Google Kubernetes Engine follow the instructions.
## Prerequisites
1. Create a Google Cloud project: [Creating by Google Console](https://cloud.google.com/resource-manager/docs/creating-managing-projects)
2. Create Kubernetes Cluster: [Creating by Google Console](https://cloud.google.com/kubernetes-engine/docs/deploy-app-cluster)
3. If you want to use your own machine cli, you should install gcloud cli and should bind your google account. [Installation steps for some distribution](https://cloud.google.com/sdk/docs/install#linux)
```
gcloud init
```
4. Install the kubectl your machine:
```
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

5. Creating Artifact Repository For Docker Images and Permission Settings
```
gcloud artifacts repositories create task-repo \
 --repository-format=docker \
 --location=europe-central2 \
 --description="Docker repository"
 
 gcloud auth configure-docker europe-central2-docker.pkg.dev
```
6. A kubernetes cluster is created using the gcloud-cli.
```
gcloud container clusters create cyangate-task \
    --release-channel regular \
    --zone  europe-central2-a \
    --node-locations  europe-central2-a
    --num-nodes 3
```
7.  To determine which pods will run on which nodes run the following commands:
```
node1=$(kubectl get no -o jsonpath="{.items[0].metadata.name}")
node2=$(kubectl get no -o jsonpath="{.items[1].metadata.name}")
node3=$(kubectl get no -o jsonpath="{.items[2].metadata.name}")

kubectl taint node $node1 tier=backend:NoSchedule
kubectl taint node $node2 tier=backend:NoSchedule
kubectl taint node $node3 tier=frontend:NoSchedule
```
## Run
Change the current working directory to "k8s-cluster-configuration" and run the following command:
```
kubectl apply -f .
```
