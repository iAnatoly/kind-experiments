kind create cluster --config threeworkers.yaml
k apply -f https://download.elastic.co/downloads/eck/1.6.0/all-in-one.yam
k -n elastic-system logs -f statefulset.apps/elastic-operator
k apply -f elasticsearch-cluster.yaml
k get pod -A -o wide
k get elasticsearch
