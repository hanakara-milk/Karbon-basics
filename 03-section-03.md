# Kubernetes Basics training 101

### kubectl basics about Kubernetes scall feature and Rolling Update and Rollback.
---  

## 23: Create a deployment and a service
```shell
kubectl apply -f 04_deployment-color-app.yaml
```
###### Quiz.1: Did the command succeed?
</br>
</br>



## 24: Check the deployment, rs, pods and services
```shell
kubectl get all
```
###### Quiz.1: What information do you see?
</br>
</br>


## 25: Access your webapp-color application via NodePort
```shell
Access your Web-browser with master or worker nodes [IPAddress] + [NodePort]
```
> ( eg. `10.149.30.109:32114` ,This is sample URL. )
###### Quiz.1: Does the webapp-color page been displayed successfully?

after that,
```shell
reload webapp-color app web page on your browser.
```
###### Quiz.2: Is there a change in the webapp-color page?
###### Quiz.3: Why is the webapp-color page information changing little by little?
</br>
</br>



## 26: Check the deployment and identify the version of the application
```shell
kubectl describe deployment webapp-color
```
###### Quiz.1: Quiz.1: What information do you see?
###### Quiz.1: What is the app version?
</br>
</br>



## 27: Update the version of the webapp-color application and check the status of the pod
```shell
kubectl apply -f 05_verup-color-app.yaml ; watch kubectl get pod
```
###### Quiz.1: How are the application pods updated?
also
```shell
reload webapp-color app web page on your browser.
```
###### Quiz.2: What does the webapp-color app web page look like?
###### Quiz.3: What is the display ratio of Version1 and Version2 pages?
###### Quiz.4: Why did this display behavior occur?
#### If you want to see the behavior of step 26 again, execute the `kubectl delete deyloyment [YOUR_WEB_COLOR_DEPLOYMENT]` command, then repeat step 27.
</br>
</br>

## 28: Check the deployment and identify the version of the application again
```shell
kubectl describe deployment webapp-color
```

###### Quiz.1: Quiz.1: What information do you see?
###### Quiz.1: What is the app version?
