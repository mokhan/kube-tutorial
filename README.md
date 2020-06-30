```bash
モ kubectl create deployment webapp --image=amoran06/picardtips --dry-run=client -o yaml > webapp.yaml
モ kubectl apply -f webapp.yaml
```

```bash
モ kubectl get deployments
NAME     READY   UP-TO-DATE   AVAILABLE   AGE
webapp   1/1     1            1           21s
```

```bash
モ kubectl get pods
NAME                     READY   STATUS    RESTARTS   AGE
webapp-c7c56d6dc-l2lkn   1/1     Running   0          37s
```

```bash
モ kubectl expose deployment webapp --type=LoadBalancer --port=8080 --target-port=5000
service/webapp exposed
```

```bash
モ minikube service webapp
|-----------|--------|-------------|-----------------------------|
| NAMESPACE |  NAME  | TARGET PORT |             URL             |
|-----------|--------|-------------|-----------------------------|
| default   | webapp |        8080 | http://192.168.39.235:30420 |
|-----------|--------|-------------|-----------------------------|
🎉  Opening service default/webapp in default browser...
```

```bash
モ kubectl get pods,services
NAME                         READY   STATUS    RESTARTS   AGE
pod/webapp-c7c56d6dc-l2lkn   1/1     Running   0          6m16s

NAME                 TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
service/kubernetes   ClusterIP      10.96.0.1       <none>        443/TCP          13m
service/webapp       LoadBalancer   10.99.200.252   <pending>     8080:30420/TCP   4m14s

モ kubectl delete deploy webapp
deployment.apps "webapp" deleted
モ kubectl delete service webapp
service "webapp" deleted
モ kubectl apply -f webapp.yaml
deployment.apps/webapp created

モ virsh list --all

 Id   Name          State
 ------------------------------
  3    minikube      running
```
