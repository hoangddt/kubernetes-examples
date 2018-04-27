Very simple deploy of a docker container

## Deploy nginx
```
$ kubectl create -f nginx-rc.yaml
$ kubectl get rc
$ kubectl create -f nginx-service.yaml
```

## Access the website
```
$ kubectl get services
NAME            TYPE           CLUSTER-IP      EXTERNAL-IP      PORT(S)        AGE
frontend        LoadBalancer   10.35.240.33    35.194.236.160   80:31462/TCP   44m
kubernetes      ClusterIP      10.35.240.1     <none>           443/TCP        1h
nginx-service   LoadBalancer   10.35.253.97    35.201.230.18    80:31414/TCP   9m
redis-master    ClusterIP      10.35.251.167   <none>           6379/TCP       1h
redis-slave     ClusterIP      10.35.247.245   <none>           6379/TCP       54m
```

Find `EXTERNAL-IP` of nginx service. Copy the IP adress and load the page in your browser. You would see "Welcome to nginx!" message.

## Scale ReplicationController

```
$ kubectl scale rc nginx --replicas=4
```

## Clean up
Delete kubernetes rc and service
```
$ kubectl delete service nginx-service
$ kubectl delete rc nginx
```

Check Google Cloud exteral IP (if you are using GG Cloud)
```
$ gcloud compute forwarding-rules list
```