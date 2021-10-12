# Deploy cusotmer container from ACR to Kubernetes 
In this lab you will deploy a custom container from ACR into AKS. In this scenario.  
## Deploy application 
 
To pull down credentials execute the following command 
```
az aks get-credentials --resource-group $RESOURCE_GROUP --name $AKS_CLUSTER
```
### Create an application in kubernetes 
The easiest way to deploy and application in kubernetes is to use the helper command "create". This command will generate a kubernetes manifest file and push the configuration to kubernetes api. https://kubernetes.io/docs/tutorials/kubernetes-basics/deploy-app/deploy-intro/

```
kubectl  create deployment myapp --image  $registry.azurecr.io/webimage:v2
```
Verify deployment running by calling ``kubectl get po`` 

``
ivan@Azure:~$ kubectl get po
NAME                     READY   STATUS    RESTARTS   AGE
myapp-84c499bdff-2xzw7   1/1     Running   0          10s
``
Alternatively another way to deploy is to fist generate the manifest file and then modify locally 
```
ivan@Azure:~$ kubectl  create deployment myapp --image  ivanacrdemo.azurecr.io/webimage:v2 --dry-run=client -o yaml 
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: myapp
  name: myapp
spec:
  replicas: 1
  selector:
    matchLabels:
      app: myapp
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: myapp
    spec:
      containers:
      - image: ivanacrdemo.azurecr.io/webimage:v2
        name: webimage
        resources: {}
status: {}
ivan@Azure:~$
```
The output can then be modified (changing names, adding labels ) and then pushed to kubernetes using the apply command ``kubectl apply -f deployment.yaml``

## Expose application 
Now that our application is running in kubernetes we want to make it accessible and consumable from outside the cluster. 
- Execute the following command to expose the application on a Azure public loadbalancer 

```
kubectl  expose deployment myapp --type=LoadBalancer --port 80
```
- The application will be available of a public Ip. To disocver the ip execute the ``kubectl get svc`` command. The app is now available under external IP 
```
ivan@Azure:~$ kubectl get svc
NAME         TYPE           CLUSTER-IP    EXTERNAL-IP    PORT(S)        AGE
kubernetes   ClusterIP      10.0.0.1      <none>         443/TCP        4d3h
myapp        LoadBalancer   10.0.24.225   20.82.81.137   80:30924/TCP   7m32s
ivan@Azure:~
```

## Extra: Expose the application on a ingress controller 
kubernetes as the concept of a exposing all ingress traffic within a central location. Instead of all applications exposing public ips instead applications are exposed on a single ingress ip and then routed to the back end application. In this extra task try deploy you application on an ingress controller 
### Hints
 - Deploy a ingress controller (nginx)
 - Create a Ingress manifest for your app
 - Deploy application under a unique path (routing rule) 

See 
 - https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/
 - https://kubernetes.io/docs/concepts/services-networking/ingress/

## Summary
In this lab we succesfully deployed our custom application and exposed it publically 

## References 
 - https://kubernetes.io/docs/concepts/services-networking/service/
 https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/
