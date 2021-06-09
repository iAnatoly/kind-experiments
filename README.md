
* https://kind.sigs.k8s.io/docs/user/quick-start/
* https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-deploy-elasticsearch.html

```
kind create cluster --config threeworkers.yaml
k apply -f https://download.elastic.co/downloads/eck/1.6.0/all-in-one.yam
k -n elastic-system logs -f statefulset.apps/elastic-operator
k apply -f elasticsearch-cluster.yaml
k get pod -A -o wide
k get elasticsearch
```

On MacOS, you do not get access to kube ip address space. 
The easiest solutiuon is to use a shell container 

k exec --stdin --tty shell-demo -- /bin/bash
bash# curl -u "elastic:$PASSWORD" -k "https://10.96.25.226:9200"
