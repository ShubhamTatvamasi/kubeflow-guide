# deploy kubeflow

build docker image
```bash
docker build -t shubhamtatvamasi/kubeflow .
```

start the server
```bash
docker run --name kubeflow -d -p 80:80 shubhamtatvamasi/kubeflow
```

stop the server
```bash
docker rm -f kubeflow
```

push to dockerhub
```bash
docker push shubhamtatvamasi/kubeflow
```
---

deploy on kubernetes
```bash
kubectl run kubeflow --image=shubhamtatvamasi/kubeflow --restart=Never --port=80 --expose

kubectl patch svc kubeflow \
  --patch='{"spec": {"type": "NodePort"}}'

kubectl patch svc kubeflow \
  --patch='{"spec": {"ports": [{"nodePort": 30000, "port": 80}]}}'
```

update the image
```bash
kubectl set image po kubeflow kubeflow=shubhamtatvamasi/kubeflow:1.0.0
```
