# Install and Configure *minikube* Kubernetes
  - *minikube* is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.
  - What you’ll need:
    - 2 CPUs or more
    - 2GB of free memory
    - 20GB of free disk space
    - Internet connection
    - Container or virtual machine manager, such as: Docker, QEMU, Hyperkit, Hyper-V, KVM, Parallels, Podman, VirtualBox, or VMware Fusion/Workstation

## 1. On EC2 Instance

### Step-01: Create an AWS EC2 instance 
   - Create an EC2 instance with with amazon-linux-2 ami (you may choose other linux distros as well)
   - Instance Size: t2.medium with 2 CPUs (any instance type with atleast 2 CPU and 2 GB memory)
<b>*Note:*</b> This configuration will not be considered under free tier usage and you may get billed for it. Therefore, kindly make sure to shutdown the server instance, whenever not in use.

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
Once both Docker and Kubectl are installed, you may use following set of commands to install Minikube:
   
   ```
    # Download the minikube binary
    sudo curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    
    # Install the minikube in /usr/local/bin/ directory
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
   
    # Restart the VM
    shutdown -r now
   ```

### Step-05: Start the minikube
   
   ```
    # Start the minikube cluster
    minikube start
   
    If all goes well, you will see a set of messages appear on the console.
   ```

Finally you may check the status of the installation with the following command
   ```
   minikube status

   ```

## 2. On Azure Virtual Machine

### Step-01: Create an Azure Virtual Machine
   - Create an Azure VM with below specs:
     - 2 CPUs or more (Ex. Standard_D2s_V2, Standard_B2s)
     - 2GB of free memory
     - 20GB of free disk space

### Step-02: Install Docker (you may install any other container runtime)
Now, connect to the VM and install the Docker.
   
   ```
    # Download the docker installation convinience script
    curl -fsSL https://get.docker.com -o get-docker.sh
    
    # Execute downloaded script
    sudo sh get-docker.sh
    
    # Start the docker service
    sudo systemctl start docker

    # Enable the docker service
    sudo systemctl enable docker

    # Add the ec2-user to docker group
    sudo gpasswd -a <vm-username> docker
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
Once both Docker and Kubectl are installed, you may use following set of commands to install Minikube:
   
   ```
    # Download the minikube binary
    sudo curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    
    # Install the minikube in /usr/local/bin/ directory
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
   
    # Restart the VM
    shutdown -r now
   ```

### Step-05: Start the minikube
   
   ```
    # Start the minikube cluster
    minikube start
   
    If all goes well, you will see a set of messages appear on the console.
   ```
Finally you may check the status of the installation with the following command
   ```
   minikube status

   ```


## References
  - [Minikube Official Documentation](https://minikube.sigs.k8s.io/docs/)
  - [Install and Set Up kubectl on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
  - 