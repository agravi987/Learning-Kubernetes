# Minikube Installation on EC2 Ubuntu Instance ☁️

This guide sets up Minikube on an Ubuntu EC2 instance using Docker as the driver.

## What You Need 📋

- An Ubuntu EC2 instance
- SSH access to the instance
- A security group that allows SSH on port 22
- At least 2 vCPU and 4 GB RAM
- Internet access

## Step 1: Update the Server 🔄

Run:

```bash
sudo apt-get update
sudo apt-get upgrade -y
```

## Step 2: Install Docker Engine 🐳

Install Docker Engine on Ubuntu by following Docker's official Ubuntu installation guide.

After Docker is installed, verify it:

```bash
docker version
```

Then add your user to the docker group:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

Test Docker with:

```bash
docker run hello-world
```

If that works, Minikube can use the Docker driver.

## Step 3: Install `kubectl` 🛠️

Download and install `kubectl`:

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```

If your EC2 instance is ARM64, replace `amd64` with `arm64`.

## Step 4: Install Minikube 🚀

Download the Minikube binary and install it:

```bash
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
minikube version
```

If your EC2 instance is ARM64, replace `amd64` with `arm64`.

## Step 5: Start Minikube ▶️

Start the cluster with Docker:

```bash
minikube start --driver=docker
```

If you want Docker to be the default driver for future runs:

```bash
minikube config set driver docker
```

## Step 6: Verify the Cluster 🔍

Run:

```bash
kubectl get nodes
kubectl get pods -A
kubectl cluster-info
minikube status
```

## Step 7: Clean Up When Needed 🧹

If you want to stop or remove the cluster:

```bash
minikube stop
minikube delete
```

## Common Issues 🧯

- If `docker version` fails, Docker is not installed correctly or the service is not running.
- If `kubectl` is not found, check that `/usr/local/bin` is in your `PATH`.
- If Minikube cannot connect to Docker, make sure your shell session picked up the docker group change.
