# Kind Installation 🧩

`kind` stands for Kubernetes IN Docker.

It is a simple way to run local Kubernetes clusters using Docker container nodes.

What you will set up:
- `kubectl`
- `kind`
- Docker
- Docker Desktop on Windows

Choose one of the guides below:

1. Local Windows system
2. AWS EC2 Ubuntu instance

## Before You Start ✅

- `kind` needs Docker to be installed and running.
- On Windows, Docker Desktop must use Linux containers.
- `kind` does not require `kubectl`, but having `kubectl` makes the learning much easier.
- For Linux machines, Docker Engine is the easiest path.
- If you are on Windows, Docker Desktop is the recommended way to provide Docker for kind.

## Installation Paths 🛣️

- [kind on local Windows](./in_local_windows_system.md)
- [kind on EC2 Ubuntu](./in_ec2_instance.md)

## Basic Verification 🔎

After installation, these commands should work:

```bash
kind version
kind create cluster
kubectl cluster-info --context kind-kind
kubectl get nodes
```

## Notes 💬

- `kind` is excellent for learning, testing, and CI.
- If you want a named cluster, use `kind create cluster --name demo`.
- If you are learning both Minikube and kind, start with just one so the steps stay easy to follow.
