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
