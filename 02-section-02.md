# Kubernetes Basics training 101

Deployment and Service basics. Delpoy pod and access to your pod via Service.
---  

## 13: Deploy sample service into your namespaces.
```shell
kubectl apply -f ./02_service-nodeport-nginx.yaml
```
###### Quiz.1: Did the creation succeed?
</br>
</br>



## 14: Getting your service detail information.

```shell
kubectl describe service [YOUR_CREATED_SERVICE_NAME]
```
###### Quiz.1: What information do you see?
###### Quiz.2: What is the Service namespace name?
###### Quiz.3: What is the Service type?
###### Quiz.4: What is NodePort number?
###### Quiz.5: What is TargetPort number?
</br>
</br>


## 15: Getting a little detail your nodes, services.
Quiz.1: What information do you see?
```shell
kubectl get nodes,svc -o wide
```
or
```shell
Node IP address information can also be confirmed from the Karbon UI.
 1． Access the Karbon UI.
 2． Select your cluster.
 3． Select Nodes on the left vane.
 4. Select Master or Worker.
```
###### Quiz.1: What information do you see?
</br>
</br>


## 16: Access your nginx via NodePort
```
Access your Web-browser or curl command with master or worker nodes [IPAddress] + [NodePort]
```
> ( eg. `10.149.30.109:32114` ,This is sample URL. )

Note: Replace IP with the IP address of your Master node or Worker node confirmed in steps 14 and 15.

Note: Replace the port with the number of your NodePort confirmed in steps 14 and 15.

###### Quiz.1: Does the nginx default page been displayed successfully?
</br>
</br>


## 17: Getting logs from your pods.
```shell
kubectl logs [YOUR_POD_NAME]
```
###### Quiz.1: What information do you see?
</br>
</br>


## 18: Getting logs from your pods with tail mode.
```shell
kubectl logs -f [YOUR_POD_NAME]

Access your Web-browser or curl command with master or worker nodes [IPAddress] + [NodePort]
```
> ( eg. `10.149.30.109:32114` ,This is sample URL. )

after that
```shell
Access your Web-browser or curl command with master or worker nodes [IPAddress] + [NodePort]/aaaa

```
> ( eg. `10.149.30.109:32114/aaaa` ,This is sample URL. )

###### Quiz.1: Has the HTTP access log you accessed been displayed?
</br>
</br>


## 19: Scaling-out your sample app.
```shell
kubectl apply -f ./03_scaleup-nginx.yaml
```
after that
```shell
kubectl get pods
```
###### Quiz.1: Did the command succeed?
###### Quiz.2: Is the pod displayed?
</br>
</br>


## 20: Scaling-in your sample app.
```shell
kubectl scale deployment nginx --replicas=1
```
or
```shell
Modify "replicas: 4" to "replicas: 1" of 03_scaleup-nginx.yaml then apply it
```
after that
```shell
kubectl get pods
```
###### Quiz.1: Did the command succeed?
###### Quiz.2: Is the pod displayed?
</br>
</br>


## 21: Confirm Kubernetes self-healing system 
```shell
kubectl delete pod [YOUR_POD_NAME]
```
after that
```shell
kubectl get pods
```
###### Quiz.1: Did the command succeed?
###### Quiz.2: Is the pod displayed?
###### Quiz.3: If a pod is displayed, why isn't it deleted?
###### Quiz.4: Has the pod name changed? 
</br>
</br>


## 22: Delete your Pod, deployment, replicaset and Service
```shell
kubectl delete -f ./01_deployment-nginx.yaml
```
after that
```
kubectl get pods
```
###### Quiz.1: Did the command succeed?
###### Quiz.2: Is the pod displayed?
###### Quiz.3: What is different from Step19?

After checking, execute the following command.
```shell
kubectl delete -f ./02_service-nodeport-nginx.yaml
```
</br>
</br>
