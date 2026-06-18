# Installation of Kubernetes ⚙️

This folder explains how to install the tools you need before you start learning Kubernetes with Minikube or kind.

What you will set up:
- `kubectl`
- `minikube`
- `kind`
- Docker as the container driver
- Docker Desktop on Windows

Use one of the following paths:

1. Local Windows system
2. AWS EC2 Ubuntu instance

## Before You Start ✅

- Use an administrator account on Windows.
- On EC2, prefer Ubuntu 22.04 or 24.04.
- Make sure the machine has internet access.
- For smoother local cluster usage, a system with at least 2 vCPU and 4 GB RAM is a good start.
- Keep `kubectl` close to the Kubernetes version running in your cluster.
- Choose either Minikube or kind for your practice cluster, depending on which guide you want to follow.
- If you are on Windows, Docker Desktop is the easiest way to provide Docker for these local cluster tools.

## Installation Paths 🛣️

- [Minikube on local Windows](./Minikube_installation/in_local_windows_system.md)
- [Minikube on EC2 Ubuntu](./Minikube_installation/in_ec2_instance.md)
- [kind on local Windows](./kind_installation/in_local_windows_system.md)
- [kind on EC2 Ubuntu](./kind_installation/in_ec2_instance.md)

## Basic Verification 🔎

After installation, these commands should work:

```bash
kubectl version --client
minikube version
minikube status
kubectl get nodes
```

## Notes 💬

- Minikube is for learning and local development, not production.
- If one install path fails, try the other one only after checking Docker is running and the PATH is correct.
