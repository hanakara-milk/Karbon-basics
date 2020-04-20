# Kubernetes Basics training 101

### Kubernetes volume and Karbon CSI Volume Plugin feature basics.

---
## 45: Pre-Check storage resources on Karbon.
```shell
 1. Access Karbon UI.
 2. Select your kubernetes cluster
 3. Select volume
```
```shell
kubectl get pv
```
###### Quiz.1: What information do you see?
###### Quiz.2: Can you identify the persistent volume names like pvc-XXXXXXXXXX from the output of `kubectl get pv` command?
</br>
</br>



## 46: Pre-Check storage resources on Nutanix
```shell
 1. Access Prism.
 2. Select Storage dashboard
 3. Select Table
 4. Select Volume Group
```
###### Quiz.1: What information do you see?
###### Quiz.2: Can you find the persistent volumes created in your kubernetes cluster?
</br>
</br>



## 47: Set secrets for MySQL Pod
```shell
kubectl create secret generic mysql-pass --from-literal=password=nutanix
```
> You can set any password you like. If you want change your password, replace "nutanix" to your password.
###### Quiz.1: Did the command succeed?
</br>
</br>



## 48: Check secret
```shell
kubectl get secrets
kubectl describe secrets mysql-pass
```
###### Quiz.1: What information do you see?
###### Quiz.2: Was the password displayed?
```shell

```

after that, Try to Describe another secret that you found by `kubectl get secret`.
```shell
kubectl describe secrets default-token-[CHAR]
```
> Replace [CHAR] with the output result of your environment.
###### Quiz.3: What information do you see?
</br>
</br>



## 49 Deploy WordPress stack with persistent volumes - MySQL
```shell
kubectl apply -f ./09_mysql-deployment.yaml; watch -n 1 kubectl get po,pv,pvc
```
###### Quiz.1: What information do you see?
###### Quiz.2: What resources have been created?
###### Quiz.3: Can you identify the newly created persistent volume name like pvc-XXXXXXXXXX from the output of `kubectl get pv` command?
</br>
</br>



## 50: Check storage resources on Karbon after Step 49
```shell
 1. Access Karbon UI.
 2. Select your kubernetes cluster
 3. Select volume
```
###### Quiz.1: Have you found the Volume created by step 49?
</br>
</br>



## 51: Check storage resources on Nutanix after Step 49
```shell
 1. Access Prism.
 2. Select Storage dashboard
 3. Select Table
 4. Select Volume Group
```
###### Quiz.1: Have you found the Volume of Nutanix Volumes created by step 49?
###### Quiz.2: Can you find the newly created persistent volume in your kubernetes cluster?
> If it is difficult to find, use the search window to filter the Volume list.
</br>
</br>



## 52: Deploy WordPress stack with persistent volumes - WordPress
> Execute this step after confirming that MySQL deployment is completed.
```shell
kubectl apply -f ./10_wordpress-deployment.yaml; watch -n 1 kubectl get po,pv,pvc,svc
```
###### Quiz.1: What information do you see?
###### Quiz.2: What resources have been created?
###### Quiz.3: Have you found the Volume created by step 52 on Karbon UI?
###### Quiz.4: Have you found the Volume of Nutanix Volumes created by step 52 on Prism strorage dash board?
> If it is difficult to find, use the search window to filter the Volume list on Prism.
</br>
</br>



## 53: Access your WordPress apps page via NodePort
```shell
Access your Web-browser with master or worker nodes [IPAddress] + [NodePort]
```
> ( eg. `10.149.30.109:32114` ,This is sample URL. )
###### Quiz.1: Does the WordPress page been displayed successfully?
###### Quiz.2: Does the WordPress app work properly?
</br>
</br>



## 54: Delete persistent volume and deyployment
```shell
kubectl delete -f ./10_wordpress-deployment.yaml; kubectl delete -f ./09_mysql-deployment.yaml ; watch -n 1 kubectl get po,pv,pvc
```
###### Quiz.1: What information do you see?
###### Quiz.2: What resources have been deleted?
###### Quiz.3: Have you found the volume that your created on Karbon UI?
###### Quiz.4: Have you found the volume of Nutanix Volumes that your created  on Prism strorage dash board?
> If it is difficult to find, use the search window to filter the Volume list on Prism.
</br>
</br>



---
#### Congrats! Mission complete.
You learned the a part of basics that one of Kubernetes storage resoures (PV/PVC).
You have been successful deploy apps with persistent volume.

----> Proceed to [Section-6](https://github.com/hanakara-milk/Karbon-basics/blob/master/06-section-06.md)
</br>
</br>



