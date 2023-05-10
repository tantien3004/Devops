#Command used
k create deployment nginx --image nginx --dry-run=client -o yaml > service.yaml

k apply -f deployment.yaml

k expose deployment nginx --port=80 --name=service-nginx --type=NodePort

curl 192.168.29.2:31394

