# Kubernetes Basics training 101 extra

### Kubernetes basics extra section, Learning about Kubernetes/Karbon monitoring.
--- 

## 71: Check Nutanix Karbon minitoring component
```shell
kubectl get po -A | grep -e prom -e export
```
###### Quiz.1: What information do you see?
</br>
</br>



## 72: Check Nutanix Karbon minitoring component
```shell
kubectl describe -n ntnx-system services prometheus-k8s
```
###### Quiz.1: What information do you see?
###### Quiz.2: What port is available on ClusterIP
</br>
</br>



## 73: Deploy Grafana, a metric visualization tool
```shell
kubectl apply -f ./13_grafana-deployment.yaml
kubectl get all -A | grep grafana
```
###### Quiz.1: What information do you see?



## 74: Access your Grafana app page via NodePort
```shell
Access your Web-browser with master or worker nodes [IPAddress] + [NodePort]
```
> ( eg. `10.149.30.109:32114`)  
###### Quiz.1: Does the Grafana page been displayed successfully?
After that
```shell
Login to Grafana (Grafana login credential provide by trainer)
```
</br>
</br>



## 75: Confirm Data Source
```shell
 1. Click gear icon on left side vane menu.
 2. Configuration > Data Sources.
 3. Select Prometheus panel icon.
 4. Click "Save and Test"
```
###### Quiz.1: What was the result of clicking?
###### Quiz.2: What do you think is the cause of the error?
###### Quiz.3: Where should we fix it?
</br>
</br>



## 76: Fix Grafana Data Sources connection error
```shell
 1. Click gear icon on left side vane menu.
 2. Configuration > Data Sources.
 3. Select Prometheus panel icon.
 4. Replace URL (http://prometheus:9090) to http://prometheus-k8s.ntnx-system.svc.cluster.local:9090
 5. Click "Save and Test"
```
###### Quiz.1: What was the result of clicking?
###### Quiz.2: How was the error fixed?
> A records

>“Normal” (not headless) Services are assigned a DNS A record for a name of the form my-svc.my-namespace.svc.cluster-domain.example. This resolves to the cluster IP of the Service.

> https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/#a-records

Again, check name of service of built-in Prometheus on Karbon.
```shell
kubectl get service -n ntnx-system
```
</br>
</br>



## 77: Adding Grafana dashboard for monitoring Kubernetes
```shell
 1. Click plus icon on left side vane menu.
 2. Create  > Import.
 3. Input 10000 at "Grafana.com Dashboard"
 4. Click "Load" button
 5. Page is progress next page.
 6. Setting "Select a Prometheus data source" at "Options" (You can click the drop-down menu and select "Prometheus")
 7. Click "Import" button
```
> Also you can adding other dashboard ( eg. 6781 / Pod dashboard )
</br>
</br>




---
### Congrats! Mission complete.

You learned the a part of basics that one of How to monitoring a metric on visualize tool (Grafana + built-in Prometheus)
</br>
</br>

