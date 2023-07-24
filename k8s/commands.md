# Command Reference

1. get nodes
```
kubectl get nodes
```
2. get deployments
```
kubectl get deploy
```
3. get pods
```
kubectl get pods
```
4. get services
```
kubectl get svc
```
5. get configmaps
```
kubectl get cm
```
6. get namespaces
```
kubectl get ns
```
7. get custom resource definitions
```
kubectl get crd
```
8. get replication controllers
```
kubectl get rc
```
9. get replicasets
```
kubectl get rs
```
10. get daemonsets
```
kubectl get ds
```
11. get jobs (batch job;terminate once finished)
```
kubectl get jobs
```
12. get cron jobs (scheduled jobs)
```
kubectl get cronjob
```
13. get all resources
```
# In current namespace
kubectl get all
# all namespaces
kubectl get all --all-namespaces/ -A
```
14. Get Pods with labels/selectors
```
kubectl get pods --selector app=nginx, tier=front-end
```
15. Get network policies
```
kubectl get netpol
```
16. Expose Pod
```
# with proxy
kubectl proxy pod pod-id --port 8080
# with port-forwarding
kubectl port-forward pod-id 8080:80
```
17. Delete Deployment, Pod, Service
```
kubectl delete deploy some-deploy

kubectl delete pod samplepod

kubectl delete svc some-service
```
18. Pipe out the pod manifest into yaml/json file.
```
kubectl get pod pod-id -o yaml > pod-def.yaml

kubectl get pod pod-id -o json > pod-def.json

kubectl create deployment nginx --image=nginx -o yaml > nginx-deployment.yaml

```
19. Edit Pod manifest
```
kubectl edit pod pod-id
```
20. Scale replicasets, deployments
```
kubectl scale rs rep-set --replicas=2

kubectl scale  --replicas=1 -f rep-set.yml

kubectl scale --replicas=1 deploy my-deployment
```
21. Create/ Replace manifests - Imperative
```
kubectl create -f pod-def.yml
kubectl replace -f pod-def.yml

kubectl create deployment --image=nginx nginx
```
22. Create manifest - Declarative
```
kubectl apply -f some-yml
```
23. Quick Create Pod - Imperative
```
kubectl run nginx --image=nginx
```
24. Get all details in different formats
```
kubectl <command> -o yaml/json/wide/name
```
25. Kube config context commands
```
# Config view
kubectl config view

# Get current context
kubectl config current-context

# Set Current Context
kubectl config set-context $(kubectl config current-context) --namespace=abhilash   # set namespace

# Switch to specific context
kubectl config use-context demo

# Delete context
kubectl config delete-context demo
```
26. Create configmaps,secrets
```
kubectl create configmap <somecm-name> --from-literal=<key>=<value>

kubectl create secret <somesecret-name> --from-literal=<key>=<value>

kubectl create configmap <somecm-name> --from-file=file.properties

kubectl create secret <somesecret-name> --from-file=file.properties
```
27. Taint Node (Avoid scheduling of pods)
```
kubectl taint node <node-name> key=value:taint-effect(NoSchedule,PreferNoSchedule,NoExecute)

kubectl taint node master taint-effect-
```
28. Get Manifest details
```
kubectl explain pod --recursive | less

# For specific keyword
kubectl explain pod --recursive | grep -A5 restartPolicy
```
29. Label node, fetch details
```
kubectl label node node-name key=value # for nodeselector-nodeaffinity

kubectl get pods --selector key=value or kubectl get pods -l key=value

kubectl get pods --show-labels

kubectl get pods -l key=value --no-headers | wc -l
```
30. Rolling update, Rollback for deployment
```
kubectl rollout status deploy deployment

kubectl rollout history deploy deployment

kubectl rollout undo deploy deployment

kubectl set image deployment nginx=nginx:1.16

kubectl rollout history deployment nginx --revision=1

kubectl set image deployment nginx nginx=nginx:1.17 --record

```
31. Check logs
```
kubectl logs -f nginx     # live logs for pod with one container

kubectl logs -f nginx help-container  # live logs for pod with specific container running inside the pod

kubectl exec nginx -- tail -f /var/log/nginx/access.log  # checking logs within container
```
32. Base64 Encode/Decode
```
echo -n "sometext" | base64

echo cm9vdA== | base64 --decode      #base64 encode and decode for secrets
```
33. Create Secret for docker credentials
```
kubectl create secret docker-registry registrycreds --docker-server=https://index.docker.io/v1/ --docker-username=user --docker-password=password --docker-email=abc-xyz@gmail.com  
```
34. Create Kubernetes service account token
```
kubectl create token service-account-name  # with 1.24, service account doesnt get created with secret and non expiry token.
```
