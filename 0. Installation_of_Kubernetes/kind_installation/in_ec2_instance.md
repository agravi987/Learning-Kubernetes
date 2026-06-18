# kind Installation on EC2 Ubuntu Instance ☁️

This guide sets up a `kind` cluster on an Ubuntu EC2 instance using Docker.

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

Install Docker Engine on Ubuntu using Docker’s official Ubuntu guide.

After installation, verify Docker:

```bash
docker version
```

Add your user to the docker group:

```bash
sudo usermod -aG docker $USER
newgrp docker
```

Test Docker with:

```bash
docker run hello-world
```

## Step 3: Install `kubectl` 🛠️

Download and install `kubectl`:

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```

If your instance is ARM64, replace `amd64` with `arm64`.

## Step 4: Install `kind` 🚀

Download the release binary and install it:

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.32.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
kind version
```

If your instance is ARM64, replace `amd64` with `arm64`.

## Step 5: Create the Cluster ▶️

Create a cluster:

```bash
kind create cluster
```

You can also name it:

```bash
kind create cluster --name learning-kind
```

## Step 6: Verify the Cluster 🔍

Run:

```bash
kind get clusters
kubectl cluster-info --context kind-kind
kubectl get nodes
kubectl get pods -A
```

## Step 7: Clean Up When Needed 🧹

If you want to remove the cluster:

```bash
kind delete cluster
kind delete cluster --name learning-kind
```

## Common Issues 🧯

- If Docker is not running, `kind` cannot create the cluster.
- If `kubectl` is not found, check that `/usr/local/bin` is in your `PATH`.
- If the cluster does not come up, check `docker ps -a` and make sure Docker has enough resources.
