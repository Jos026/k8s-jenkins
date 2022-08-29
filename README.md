# Clone repos

git clone https://github.com/Jos026/k8s-jenkins.git

# Create a Namespace for Jenkins. 

kubectl create namespace devops-tools

# Create the service account using kubectl (The serviceAccount.yaml creates a jenkins-admin clusterRole, jenkins-admin ServiceAccount and binds the clusterRole to the service account.The jenkins-admin cluster role has all the permissions to manage the cluster components. You can also restrict access by specifying individual resource actions.)

kubectl apply -f serviceAccount.yaml

# Modify volume.yaml replacing "docker-desktop" with any one of your cluster worker nodes hostname.

kubectl get nodes

# Create the volume using kubectl

kubectl create -f volume.yaml

# Create the deployment using kubectl.

kubectl apply -f deployment.yaml

# Create the Jenkins service using kubectl.

kubectl apply -f service.yaml

# Access jenkins with the following address:

http://<node-ip>:32000

# Get logs for jenkins admin password 

kubectl logs jenkins-fd5fdf49f-m4zd2 --namespace=devops-tools

# Start initial Jenkins config