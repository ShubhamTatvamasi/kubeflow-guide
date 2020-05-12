# kubeflow-guide

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


