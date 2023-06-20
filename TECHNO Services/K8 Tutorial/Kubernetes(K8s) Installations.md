To install Kubernetes on an Ubuntu server and create a cluster, you can follow these general steps:

1. Set up the Ubuntu server:
    
    - Install Ubuntu Server on the machine or VM.
    - Ensure the server has sufficient resources, such as CPU, memory, and storage, to run Kubernetes.
2. Install Docker:
    
    - Update the package manager: `sudo apt update`
    - Install Docker using the package manager: `sudo apt install docker.io`
    - Start and enable Docker service: `sudo systemctl start docker` and `sudo systemctl enable docker`
    - Add your user to the `docker` group to run Docker commands without sudo: `sudo usermod -aG docker $USER`
    - Log out and log back in for the group changes to take effect.
3. Install kubeadm, kubelet, and kubectl:
    
    - Add the Kubernetes repository's GPG key: `curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -`
    - Add the Kubernetes repository: `sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"`
    - Install kubeadm, kubelet, and kubectl: `sudo apt install kubeadm kubelet kubectl`
    - Prevent the package manager from updating these packages automatically: `sudo apt-mark hold kubelet kubeadm kubectl`
4. Initialize the Kubernetes cluster:
    
    - Run the `kubeadm init` command with appropriate flags and options to initialize the cluster. For example: `sudo kubeadm init --pod-network-cidr=10.244.0.0/16`
    - Follow the instructions provided by `kubeadm` after the initialization process completes. It includes setting up the network and joining nodes to the cluster.
5. Configure kubectl:
    
    - Copy the admin kubeconfig file: `mkdir -p $HOME/.kube` and `sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config`
    - Set the correct permissions for the kubeconfig file: `sudo chown $(id -u):$(id -g) $HOME/.kube/config`
6. Install a network add-on:
    
    - Choose a network add-on for pod networking, such as Calico, Flannel, or Weave.
    - Follow the specific installation instructions for the chosen network add-on to install it on your cluster.
7. Join worker nodes (optional):
    
    - If you have additional Ubuntu servers that you want to join as worker nodes, run the `kubeadm join` command provided by the `kubeadm init` output on each worker node.

> That's a high-level overview of the installation process. Please note that the exact commands and steps may vary depending on your specific setup and the version of Kubernetes you are installing. It's always recommended to refer to the official Kubernetes documentation or installation guides for the most up-to-date and accurate instructions.