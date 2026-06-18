# Minikube Installation on Local Windows System 🪟

This guide sets up a local Kubernetes cluster on Windows using Docker Desktop, `kubectl`, and Minikube.

## What You Need 📋

- Windows 10 or Windows 11
- Administrator access
- Virtualization enabled in BIOS or UEFI
- Internet access

## Step 1: Install Docker Desktop 🐳

1. Download Docker Desktop from the official Docker website.
2. Install it with the default options.
3. Restart your computer if the installer asks you to.
4. Open Docker Desktop and wait until it says Docker is running.

Minikube uses Docker as the driver in this guide, so Docker must be working first.

## Step 2: Install `kubectl` 🛠️

Open PowerShell and run:

```powershell
winget install -e --id Kubernetes.kubectl
kubectl version --client
```

If another tool already installed `kubectl`, check which one is being used:

```powershell
where kubectl
```

## Step 3: Install Minikube 🚀

Run:

```powershell
winget install Kubernetes.minikube
minikube version
```

## Step 4: Start the Cluster ▶️

Start Minikube with Docker as the driver:

```powershell
minikube start --driver=docker
```

If you want Docker to be the default driver for future starts:

```powershell
minikube config set driver docker
```

## Step 5: Verify the Setup 🔍

Check that the cluster is ready:

```powershell
minikube status
kubectl get nodes
kubectl get pods -A
kubectl cluster-info
```

If `kubectl cluster-info` returns URLs, your config is working.

## Step 6: Useful Practice Commands ✨

```powershell
minikube addons list
minikube dashboard
minikube stop
minikube delete
```

## Common Issues 🧯

- If `kubectl` is coming from Docker Desktop instead of your install, fix your `PATH`.
- If Minikube says Docker is unavailable, open Docker Desktop and wait for it to fully start.
- If the driver is wrong, rerun `minikube start --driver=docker`.
