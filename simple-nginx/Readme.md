Very simple deploy of a docker container

```
$ kubectl create -f nginx-rc.yaml
$ kubectl get rc
$ kubectl create -f nginx-service.yaml
```

```
$ kubectl get services
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP      PORT(S)        AGE
frontend        LoadBalancer   10.35.240.33    35.194.236.160   80:31462/TCP   44m
kubernetes      ClusterIP      10.35.240.1     <none>           443/TCP        1h
nginx-service   LoadBalancer   10.35.253.97    35.201.230.18    80:31414/TCP   9m
redis-master    ClusterIP      10.35.251.167   <none>           6379/TCP       1h
redis-slave     ClusterIP      10.35.247.245   <none>           6379/TCP       54m
```

We can access nginx through the `EXTERNAL-IP`, the default "Welcome to nginx!" will come up at that address