# Kubernetes Learning Tasks 📝

Use this as your practice checklist.

## 🌱 Beginner Tasks

- [ ] Read `1. Kubernetes-basics/readme.md`
- [ ] Explain cluster, node, pod, deployment, and service in your own words
- [ ] Draw the flow: user -> service -> deployment -> pod -> container
- [ ] Run `kubectl get nodes`
- [ ] Run `kubectl get pods`
- [ ] Run `kubectl get services`

## 🛠️ Command Practice

- [ ] Run `kubectl describe pod <pod-name>`
- [ ] Run `kubectl logs <pod-name>`
- [ ] Run `kubectl exec -it <pod-name> -- bash`
- [ ] Run `kubectl apply -f deployment.yaml`
- [ ] Run `kubectl delete pod <pod-name>`

## 🚀 First App Practice

- [ ] Create an NGINX deployment
- [ ] Check the deployment with `kubectl get deployments`
- [ ] Check the pods with `kubectl get pods`
- [ ] Expose the deployment with a service
- [ ] Open the app in the browser

## 🔄 Rollout Practice

- [ ] Update the image from v1 to v2
- [ ] Check rollout status
- [ ] View rollout history
- [ ] Roll back to the previous version
- [ ] Roll back to a specific revision

## 📈 Scaling Practice

- [ ] Delete one pod and watch it come back
- [ ] Scale the deployment up
- [ ] Scale the deployment down
- [ ] Enable autoscaling if your cluster supports metrics
- [ ] Observe how replicas change under load

## 🧾 YAML Practice

- [ ] Create a deployment YAML from scratch
- [ ] Create a service YAML from scratch
- [ ] Change `replicas` and apply again
- [ ] Change the container image and apply again
- [ ] Keep your YAML clean and readable

## 🏆 Pro-Level Check

- [ ] Can you explain why a pod is not the same as a container?
- [ ] Can you explain why a service is needed?
- [ ] Can you explain what happens during a rollout?
- [ ] Can you explain how self-healing works?
- [ ] Can you explain how scaling helps during traffic changes?
