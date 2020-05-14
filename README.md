# kubeflow-guide

[katacoda kubeflow](https://katacoda.com/embed/kubernetes-kubeflow)

[kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

Get the NodePort of Kubeflow Central Dashboard
```bash
kubectl get svc istio-ingressgateway -n istio-system \
  -o json | jq '.spec.ports[] | select(.port==80)'
```
> last I checked it was: 31380
---

list all profiles
```bash
kubectl get profiles
```

create new profile
```yaml
kubectl apply -f - << EOF
apiVersion: kubeflow.org/v1beta1
kind: Profile
metadata:
  name: shubham
spec:
  owner:
    kind: User
    name: shubhamtatvamasi@gmail.com
EOF
```
---

Things to know before you begin learning kubeflow

Names | Links
--- | ---
Istio | https://istio.io
OpenEBS | https://openebs.io
Knative | https://knative.dev
cert-manager | https://cert-manager.io

---

if you want to change the node ports
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
