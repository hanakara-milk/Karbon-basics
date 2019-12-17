# Kubernetes Basics training 001

kubectl basics and create first pod into your Kubernetes cluster.
---  
## 01: Confirm kubectl version
```kubernetes-kubectl
kubectl version
```
###### Quiz.1: What information do you see?
###### Quiz.2: Can you see both client and server?
</br>
</br>



## 02: Getting kubernetes nodes information.
```shell
kubectl get nodes
```
###### Quiz.1: How many nodes are there?
###### Quiz.2: What types of nodes are there?
</br>
</br>


## 03: Getting kubernetes pods information.
```shell
kubectl get pods
```
###### Quiz.1: How many pods do you see?
###### Quiz.2: Have you already placed a pod (container)?
</br>
</br>



## 04: Getting kubernetes pods information include system pods.
```shell
kubectl get pods --all-namespaces
```
###### Quiz.1: How many pods do you see?
###### Quiz.2: Have you already placed a pod (container)?
</br>
</br>


## 05: Getting kubernetes namespaces.
```shell
kubectl get ns
```
###### Quiz.1: What information do you see?
</br>
</br>


## 06: Creating your work namespaces.
```shell
kubectl create ns [YOUR_NAMESPACE_NAME]
```
> * insert unique your namespace name insted `[YOUR_NAMESPACE_NAME]`  
###### Quiz.1: Did the creation succeed?
</br>
</br>


## 07: Deploy sample pods into your namespaces.
```shell
kubectl apply -f 01_deployment-nginx.yaml -n [YOUR_NAMESPACE_NAME]
```
###### Quiz.1: Did the creation succeed?
</br>
</br>


## 08: Getting your pods information
```shell
kubectl get pods
```   
###### Quiz.1: How many pods do you see?
</br>
</br>


## 09: Getting your pods information with namespaces
```shell
kubectl get pods -n [YOUR_NAMESPACE_NAME]
```   
###### Quiz.1: How many pods do you see?
after that
```
kubectl config get-contexts
```
###### Quiz.2: What is displayed in the namespace?
</br>
</br>


## 10: Setting your dedicated namespaces contexts as default.
```shell
kubectl config set-context $(kubectl config current-context) --namespace=[YOUR_NAMESPACE_NAME]
```
###### Quiz.1: Did the command succeed?
after that
```
kubectl config get-contexts
```
###### Quiz.2: What is displayed in the namespace?
###### Quiz.3: What is different from step 09 result?
</br>
</br>


## 11: Getting your pods information with namespaces
```shell
kubectl get pods
```
###### Quiz.1: How many pods do you see?
###### Quiz.2: Can you view your deployed pods without namespace options?
</br>
</br>


## 12: Getting your pods detail information.
```shell
kubectl describe pod [YOUR_POD_NAME]
```
###### Quiz.1: What information do you see?
###### Quiz.2: What is the pod namespace name?
###### Quiz.3: On which node is the pod located?
###### Quiz.4: What is the image of Pod?
###### Quiz.5: What information does the event have?
</br>
</br>

---
### Congrats! Mission complete.
You learned the basics of kubectl.

You have successfully deployed your first pod.

Proceed to Section-2 to learn the basics of Kubernetes.
</br>
</br>
