# Install and Configure Minikube Kubernetes

## 1. On EC2 Instance

### Step-01: Create an AWS EC2 instance 
   - Create an EC2 instance with with amazon-linux-2 ami (you may choose other linux distros as well)
   - Instance Size: t2.medium with 2 CPUs (any instance type with atleast 2 CPU and 2 GB memory)
   - <b>*Note:*</b> This configuration will not be considered under free tier usage and you may get billed for it. Therefore, kindly make sure to shutdown the server instance, whenever not in use.

### Step-02: Install Docker (you may install any other container runtime)
   
   ```
    # Install Docker on Amazon Linux 2 AMI
    sudo amazon-linux-extras install -y docker
    
    # Start the docker service
    sudo systemctl start docker

    # Enable the docker service
    sudo systemctl enable docker

    # Add the ec2-user to docker group
    sudo gpasswd -a ec2-user docker
   ```
### Step-03: Install Kubectl (CLI) utility
   - Kubectl is a utility to manage a K8 cluster. 
   - Hence it is required to install it before you configure / install the K8 cluster

   ```
    # Download the kubectl binary
    sudo curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

    # Provide execute permission to kubectl
    sudo chmod +x kubectl

    # Move the kubectl program to /usr/local/bin in order to access it from anywhere
    sudo mv kubectl /usr/local/bin
   ```

### Step-04: Install Minikube
   - Once both Docker and Kubectl are installed, you may use following set of commands to install Minikube:
   
   ```
    # Download the minikube binary
    sudo curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    
    # Install the minikube in /usr/local/bin/ directory
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
   ```

## 2. On Azure Virtual Machine

### 