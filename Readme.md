# K8S YAML template 
Ref: https://kubernetes.io/docs/reference/kubernetes-api/
Ref: https://kubernetes.io/docs/concepts/workloads/pods/downward-api/

```
apiVersion: 
kind:
metadata:
spec:
```

## Alias 
alias k='kubectl'
alias kns='k config set-context --current --namespace'
alias kpa='k get pod -A'
alias kl='k logs'
alias kdp='k describe'
alias ksh='k exec -it -- /bin/sh'
alias kb='k exec -it -- /bash'

# Imperative command

## Get name of the resouces 
- awk
```
k get crds | awk '{print $1}' | grep 'verticalpodautoscaler' > /root/vpa-crds.txt
```
- json path
```
kubectl get crds -o jsonpath='{.items[*].metadata.name}' | tr ' ' '\n' | grep verticalpodautoscaler
```
- K8S 
```
kubectl get crds -o custom-columns=NAME:.metadata.name
```
- yq
```
kubectl get crds -o yaml | yq e '.items[].metadata.name' -
```