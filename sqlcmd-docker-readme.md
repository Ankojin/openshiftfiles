docker build -t ubuntu-sqlcmd .
docker run -it ubuntu-sqlcmd
docker tag ubuntu-sqlcmd myuser/ubuntu-sqlcmd:latest
docker push myuser/ubuntu-sqlcmd:latest
#############
kubectl apply -f ubuntu-sqlcmd-pod.yaml
kubectl get pods
kubectl exec -it ubuntu-sqlcmd-pod -- bash

