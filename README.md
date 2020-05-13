# kubeflow-guide

[kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

```bash
kubectl patch svc centraldashboard -n kubeflow \
  --patch='{"spec": {"type": "NodePort"}}'

kubectl patch svc ml-pipeline-ui -n kubeflow \
  --patch='{"spec": {"type": "NodePort"}}'


kubectl patch svc centraldashboard -n kubeflow \
  --patch='{"spec": {"ports": [{"nodePort": 30000, "port": 80}]}}'

kubectl patch svc ml-pipeline-ui -n kubeflow \
  --patch='{"spec": {"ports": [{"nodePort": 30001, "port": 80}]}}'
```

list all namespaces
```bash
kubectl get ns 
```

```bash
kubectl patch svc kiali -n istio-system \
  --patch='{"spec": {"type": "NodePort"}}'

kubectl patch svc kiali -n istio-system \
  --patch='{"spec": {"ports": [{"nodePort": 30100, "port": 20001}]}}'
```
> add /kiali

```bash
kubectl get po --sort-by=.metadata.creationTimestamp
```

```bash
kubectl delete po --field-selector=status.phase!=Running
```
