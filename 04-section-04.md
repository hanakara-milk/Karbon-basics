# Kubernetes Basics training 101

### Kubernetes config map feature basics.

---
## 34: Create a configmap
```shell
kubectl apply -f 06_configmap-color-app-pink.yaml
```
###### Quiz.1: Did the command succeed?
</br>
</br>



## 35: Check the configmap
```shell
kubectl get cm appcolor

kubectl describe cm appcolor
```
###### Quiz.1: What information do you see?
> "cm" is short name of configmap resource. You can command `kubectl get configmap appcolor`. 
> You can find all Kubernetes api resources and short name by `kubectl api-resources`
</br>
</br>



## 36: Create a deployment
```shell
kubectl apply -f 07_deployment-color-app-latest.yaml
```
###### Quiz.1: What information do you see?
</br>
</br>



## 37: Check the deployment, rs, pods and services, pick up the name of the pod (like webapp-color-ABCDEFG)
```shell
kubectl get all
```
###### Quiz.1: What information do you see?
</br>
</br>



## 38: Check the environent variables from the Pod
```shell
kubectl exec -it [YOUR_POD_NAME] -- env
```
###### Quiz.1: Have you log into your container successfully?
###### Quiz.2: Did you find the value set in ConfigMap in the container?
###### Quiz.3: What color will be your webpage?
</br>
</br>



## 39: Access your webapp-color application via NodePort
```
Access your Web-browser with master or worker nodes [IPAddress] + [NodePort]
```
> ( eg. `10.149.30.109:32114`)  
###### Quiz.1: What color displayed on your webapp-color webpage?
</br>
</br>



## 40: Delete and recreate the configmap
```shell
kubectl delete -f 06_configmap-color-app-pink.yaml
kubectl apply -f 08_configmap-color-app-blue.yaml
```
###### Quiz.1: Did the command succeed?
</br>
</br>



## 41: Check the configmap
```shell
kubectl get cm appcolor

kubectl describe cm appcolor
```
###### Quiz.1: What information do you see?
</br>
</br>



## 42: Delete and recreate the deployment
```shell
kubectl delete -f 07_deployment-color-app-latest.yaml
kubectl apply -f 07_deployment-color-app-latest.yaml
```
> You can also reload Pod by modify Deployment (ex. adding annotations).
> But this method is bad know-how, be careful about how to use.
</br>
</br>



## 43: Check the deployment, rs, pods and services, pick up the name of the pod (like webapp-color-ABCDEFG)
```shell
kubectl get all
```
###### Quiz.1: Did the command succeed?
</br>
</br>



## 44: Check the environent variables from the Pod
```shell
kubectl exec -it [YOUR_POD_NAME] -- env
```
###### Quiz.1: What color will be your webpage?
</br>
</br>



## 45: Access your webapp-color application via NodePort
```
Access your Web-browser with master or worker nodes [IPAddress] + [NodePort]
```
> ( eg. `10.149.30.109:32114`)  
###### Quiz.1: What color displayed on your webapp-color page?
###### Quiz.2: Why is the webapp-color page color is changing?
</br>
</br>



## 46: Delete the configmap and deployment 
```shell
kubectl delete -f 07_deployment-color-app-latest.yaml
kubectl delete -f 08_configmap-color-app-blue.yaml
```
###### Quiz.1: Did the command succeed?
</br>
</br>



---
#### Congrats! Mission complete.
You learned the a part of basics that one of Kubernetes storage resoures (ConfigMap).

You have been successful in changing the application settings using ConfigMap.

----> Proceed to [Section-5](https://github.com/hanakara-milk/Karbon-basics/blob/master/05-section-05.md)
</br>
</br>
