# k8aliases
Some helper functions and aliases for kubernetes

This is a collection of aliases and scripts to help lessen the amount of typing needed when working with Kubernetes.

The idea is to make some custom kubectl commands and set optional namespace and label variables to help filter output from the commands.

## Example Usage

First add come context information.
```
$> setnamespace default

Namespace set to:  default

$> setlabel app=nginx

Label set to:  app=nginx

$>shownamespace

default

$>showlabel

app=nginx
```

Now you can use the "ns" version of kubectl to see pods in the namespace.
```
$>kubectlns get pods
Namespace=default
NAME                     READY   STATUS    RESTARTS   AGE
nginx-569d8b957f-pnstb   1/1     Running   1          25h
nginx-569d8b957f-rr4wh   1/1     Running   1          25h
nginx-569d8b957f-szv9m   1/1     Running   1          25h
nginx-569d8b957f-zk8dg   1/1     Running   1          25h
```

Next you can use the describepod command to get quick pod information using the label and namespace filters.

```
$>describepod
Using namespace: default
Using Label: app=nginx
kubectl describe pod  -n default -l app=nginx
Name:         nginx-569d8b957f-pnstb
Namespace:    default
Priority:     0
Node:         docker-desktop/192.168.65.4
Start Time:   Mon, 08 Mar 2021 13:40:41 -0600
Labels:       app=nginx
              pod-template-hash=569d8b957f
Annotations:  <none>
Status:       Running
IP:           10.1.0.92
IPs:
  IP:           10.1.0.92
Controlled By:  ReplicaSet/nginx-569d8b957
<TRUNCATED>
```

Show the containers in the pods in a given namespace with a certain label.

```
$>showcontainers
Using namespace: default
Using Label: app=nginx

Pod ---> Containers
-------------------
nginx-569d8b957f-pnstb
--->  nginx


nginx-569d8b957f-rr4wh
--->  nginx


nginx-569d8b957f-szv9m
--->  nginx


nginx-569d8b957f-zk8dg
--->  nginx
```





