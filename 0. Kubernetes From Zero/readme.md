# Kubernetes From Zero

This folder is your starting point if you want to learn Kubernetes from absolute zero and grow into someone who can use it with confidence.

The idea is simple:
- learn the core concepts in a clean order
- practice the commands
- understand why each thing exists
- repeat until the workflow feels natural

## What is inside this folder

| File | Purpose |
| :--- | :--- |
| `readme.md` | The main learning guide |
| `tasks.md` | A practical task list to follow step by step |

## How to use this roadmap

Read and practice in this order:

1. `1. Kubernetes-basics`
2. `2. Important Basic command Used`
3. `3. Deployment and Running of nginx`
4. `4. Rollout and Rollback`
5. `5. Self Healing and Scaling and Yamls`

If you follow that path, you will move from "I know nothing" to "I can explain and use Kubernetes" without jumping around.

## The big picture

Kubernetes is a system that helps you run containers in a reliable way.

Think of it like this:
- container = one running app
- pod = the smallest thing Kubernetes runs
- deployment = manages pods
- service = gives pods a stable way to be reached
- namespace = helps organize resources
- configmap and secret = store configuration
- ingress = controls external web access

## Your learning journey

### Stage 1: Basics
Learn the language of Kubernetes.

You should understand:
- cluster
- node
- pod
- deployment
- service

Goal:
- know what each one does in one simple sentence
- be able to explain the flow from user request to pod

### Stage 2: Commands
Learn the commands you will use again and again.

You should be comfortable with:
- `kubectl get pods`
- `kubectl get nodes`
- `kubectl describe pod <name>`
- `kubectl logs <pod-name>`
- `kubectl apply -f file.yaml`
- `kubectl delete pod <name>`

Goal:
- stop feeling nervous when you open the terminal
- know which command to use for inspection, debugging, and deployment

### Stage 3: First Deployment
Run a simple application like NGINX.

You should learn:
- how to create a deployment
- how to check pods
- how to expose the app with a service

Goal:
- get a working app running in Kubernetes
- understand how traffic reaches the container

### Stage 4: Updates and Safety
Learn rollout and rollback.

You should understand:
- how Kubernetes updates pods gradually
- how to check rollout status
- how to go back to a previous version

Goal:
- change versions without breaking the app
- understand version history and recovery

### Stage 5: Self-Healing and Scaling
Learn how Kubernetes keeps apps healthy and adjusts size.

You should understand:
- what happens when a pod is deleted
- how replicas keep apps available
- how manual scaling works
- how autoscaling works

Goal:
- see Kubernetes recover automatically
- know how to grow or shrink apps when needed

## Simple mental model

```text
User
  ->
Service
  ->
Deployment
  ->
ReplicaSet
  ->
Pod
  ->
Container
```

If this flow makes sense, Kubernetes becomes much easier.

## What "pro" means here

You do not need to memorize everything at once.

Being good at Kubernetes means you can:
- explain the basics clearly
- create and inspect resources
- debug with confidence
- update applications safely
- scale when traffic changes
- recover when something fails

## Best way to study

Use this pattern:

1. Read one topic
2. Run the commands yourself
3. Break something on purpose
4. Fix it
5. Repeat the same idea until it feels easy

That is how Kubernetes starts to feel natural.

## Mini project idea

After the basics, build this small flow:

1. Create an NGINX deployment
2. Expose it with a service
3. Update the image version
4. Roll back to the previous version
5. Scale the deployment up and down
6. Delete one pod and watch Kubernetes replace it

If you can do this without copying every line, you are already making real progress.

## Final note

This project is not about fancy words.
It is about making Kubernetes simple enough that you can actually use it.

Keep the learning small, practical, and repeated.
That is the fastest way to become strong from zero.
