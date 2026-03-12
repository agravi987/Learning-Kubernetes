# Kubernetes Rollout and Rollback

A step-by-step guide to deploying, updating, and rolling back a Kubernetes application using a React app as an example.

---

## 1️⃣ Create Kubernetes Deployment

Create a file named `deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: react-k8s-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: react-k8s
  template:
    metadata:
      labels:
        app: react-k8s
    spec:
      containers:
      - name: react-k8s-container
        image: ravi0706/react-k8s-app:v1
        ports:
        - containerPort: 80
```

Apply it:

```bash
kubectl apply -f deployment.yaml
```

---

## 2️⃣ Check Pods

```bash
kubectl get pods
```

**Example output:**

```
react-k8s-deployment-7b7d6c7c5f-abcde   1/1   Running   0   10s
react-k8s-deployment-7b7d6c7c5f-fghij   1/1   Running   0   10s
react-k8s-deployment-7b7d6c7c5f-klmno   1/1   Running   0   10s
```

Check deployment:

```bash
kubectl get deployments
```

---

## 3️⃣ Expose the Application

Create a service:

```bash
kubectl expose deployment react-k8s-deployment --type=NodePort --port=80
```

Check service:

```bash
kubectl get svc
```

Open in browser:

```
http://<NODE-IP>:<NodePort>
```

---

## 4️⃣ Check Rollout Status

```bash
kubectl rollout status deployment react-k8s-deployment
```

**Example output:**

```
deployment "react-k8s-deployment" successfully rolled out
```

> This confirms the deployment finished successfully.

---

## 5️⃣ Update Application Version (Rollout)

Upgrade from `v1` → `v2`:

```bash
kubectl set image deployment/react-k8s-deployment \
  react-k8s-container=ravi0706/react-k8s-app:v2
```

Check rollout:

```bash
kubectl rollout status deployment react-k8s-deployment
```

Check pods:

```bash
kubectl get pods
```

> You will see new pods gradually replacing old ones. This is called the **Rolling Update Strategy**.

---

## 6️⃣ Check Rollout History

```bash
kubectl rollout history deployment react-k8s-deployment
```

**Example output:**

```
REVISION   CHANGE-CAUSE
1          Initial deploy v1
2          Updated image v2
```

---

## 7️⃣ Update Again (v2 → v3)

```bash
kubectl set image deployment/react-k8s-deployment \
  react-k8s-container=ravi0706/react-k8s-app:v3
```

Check rollout status:

```bash
kubectl rollout status deployment react-k8s-deployment
```

View history again:

```bash
kubectl rollout history deployment react-k8s-deployment
```

**Example output:**

```
REVISION   CHANGE-CAUSE
1          v1
2          v2
3          v3
```

---

## 8️⃣ Rollback Deployment

Rollback from `v3` → `v2`:

```bash
kubectl rollout undo deployment react-k8s-deployment
```

Check status:

```bash
kubectl rollout status deployment react-k8s-deployment
```

> Pods will be replaced again as part of the rollback process.

---

## 9️⃣ Rollback to a Specific Version

To rollback to `v1`, first check the revision history:

```bash
kubectl rollout history deployment react-k8s-deployment
```

Then rollback to a specific revision:

```bash
kubectl rollout undo deployment react-k8s-deployment --to-revision=1
```

---

## 🔟 Watch Rolling Update Live

> 💡 **DevOps Engineer Trick** — Watch pod changes in real time!

Run the following in one terminal:

```bash
kubectl get pods -w
```

Then, in another terminal, trigger an image update. You will see pods transition through:

- **Old Pod** → `Terminating`
- **New Pod** → `ContainerCreating`
- **New Pod** → `Running`

This demonstrates **Zero Downtime Deployment**.

---

## ⭐ Most Important Rollout Commands (Interview Prep)

| Command | Purpose |
|---|---|
| `kubectl rollout status deployment <name>` | Check rollout progress |
| `kubectl rollout history deployment <name>` | View revision history |
| `kubectl rollout undo deployment <name>` | Rollback to previous version |
| `kubectl rollout undo deployment <name> --to-revision=n` | Rollback to a specific version |
| `kubectl set image deployment/<name> <container>=<image>:<tag>` | Update container image |