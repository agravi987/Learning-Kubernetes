# kind Installation on Local Windows System 🪟

This guide sets up a local Kubernetes cluster on Windows using Docker Desktop, `kubectl`, and `kind`.

## What You Need 📋

- Windows 10 or Windows 11
- Administrator access
- Virtualization enabled in BIOS or UEFI
- Docker Desktop installed
- Internet access

## Step 1: Install Docker Desktop 🐳

1. Download Docker Desktop from the official Docker website.
2. Install it with the default options.
3. Start Docker Desktop and wait until it is running.
4. Make sure Docker is using Linux containers.

`kind` uses Docker container nodes, so Docker must be ready first.

## Step 2: Install `kubectl` 🛠️

Open PowerShell and run:

```powershell
winget install -e --id Kubernetes.kubectl
kubectl version --client
```

If `kubectl` is already installed, check which copy is being used:

```powershell
where kubectl
```

## Step 3: Install `kind` 🚀

Install `kind` with Winget:

```powershell
winget install Kubernetes.kind
kind version
```

If you prefer the release binary, download `kind-windows-amd64.exe` from the official release assets, rename it to `kind.exe`, and place it in a folder on your `PATH`.

If Docker Desktop is already installed and running, you do not need any extra container runtime for kind.

## Step 4: Create the Cluster ▶️

Create a cluster:

```powershell
kind create cluster
```

If you want a custom name:

```powershell
kind create cluster --name learning-kind
```

## Step 5: Verify the Setup 🔍

Run:

```powershell
kind get clusters
kubectl cluster-info --context kind-kind
kubectl get nodes
kubectl get pods -A
```

## Step 6: Useful Practice Commands ✨

```powershell
kind delete cluster
kind delete cluster --name learning-kind
kubectl config get-contexts
```

## Common Issues 🧯

- If Docker is in Windows container mode, switch it to Linux containers.
- If `kind` is not found, check your `PATH`.
- If `kubectl` connects to the wrong cluster, confirm the current context with `kubectl config get-contexts`.
