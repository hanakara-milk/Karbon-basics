# Kubernetes Basics training 101

### Kubernetes StatefulSet with persistent volume and DaemonSet feature basics.
---  


## 55: Deploy statefulset Pod
```shell
kubectl apply -f ./11_statefulset.yaml; watch -n 1 kubectl get po,pv,pvc
```
###### Quiz.1: What information do you see?
###### Quiz.2: How many pods have started up?
###### Quiz.3: How was the pod startup sequence?
###### Quiz.4: How was the pod launching behavior?
</br>
</br>



## 56: Check Pods "mountPath" on statefulset manifest.
```shell
cat ./11_statefulset.yaml
```
#### Quiz.1: Did you confirm the "mountPath" directory?
</br>
</br>



## 57: Log in to the container and check the "mountPath"
```shell
kubectl exec -it sample-statefuleset-0 -- df -h | grep /dev/sd
kubectl exec -it sample-statefuleset-0 -- ls /var/data
```
> The last number in the Pod of StatefulSet can be replaced with your favorite number from existing Pods.
###### Quiz.1: Was the statefulset manifest path mounted?
###### Quiz.2: Is the disk size of the mounted path correct?
###### Quiz.3: Is there a file in the mounted path?
</br>
</br>



## 58: Create ("touch") a file in the mounted path.
```shell
kubectl exec -it sample-statefuleset-0 -- touch /var/data/stateful-01.txt
kubectl exec -it sample-statefuleset-0 -- ls /var/data
```
> The last number in the Pod of StatefulSet can be replaced with your favorite number from existing Pods.
###### Quiz.1: Is there a file in the mounted path?
</br>
</br>




## 59: Delete StatefulSet Pod
```shell
kubectl delete pod sample-statefuleset-0; watch -n 1 kubectl get po,pv,pvc
> The last number in the Pod of StatefulSet can be replaced with your favorite number from existing Pods.
```
###### Quiz.1: What information do you see?
###### Quiz.2: Is there a change in the name of the pod?
</br>
</br>



## 60: Log in to the container and check the "mountPath" again.
```shell
kubectl exec -it sample-statefuleset-0 -- ls /var/data
```
###### Quiz.1: Was the statefulset manifest path mounted?
###### Quiz.2: Is there a file that your created in the mounted path?
</br>
</br>



## 61: Delete the Worker node which sample-statefuleset-0 is running
```shell
kubectl get pod -o wide
```
###### Quiz.1: Which pod is on which node?

#### Note which node the pod of sample-statefuleset-0 is running on.

after that
```
 1. Access Karbon UI.
 2. Select your kubernetes cluster
 3. Select Nodes
 4. Select Woker
 5. Check the node to be deleted and click "Delete Worker"
```
</br>
</br>



## 62: Behavior of StatefulSet at the node failure or deletion.
```shell
watch kubectl get pod -o wide
```
###### Quiz.1: What happened to the pod that was running on the deleted node?
###### Quiz.2: Did Pod come back with Kubernetes' self-healing feature?
> After this Worker node deletion, it takes up to 10 minutes for Pod to return.
</br>
</br>



## 63: Log in to the container and check the "mountPath" again.
```shell
kubectl exec -it sample-statefuleset-0 -- ls /var/data
```
###### Quiz.1: Was the statefulset manifest path mounted?
###### Quiz.2: Is there a file that your created in the mounted path?
</br>
</br>



## 64: Delete StatefulSet
```shell
kubectl delete -f ./11_statefulset.yaml; watch -n 1 kubectl get po,pv,pvc
```
###### Quiz.1: How was the pod delete sequence?
###### Quiz.2: How was the volume behavior?
</br>
</br>



## 65: Check storage resources on Karbon after Step 64
```shell
 1. Access Karbon UI.
 2. Select your kubernetes cluster
 3. Select volume
```
###### Quiz.1: Have you found the Volume created by step 64?
</br>
</br>


## 66: Check storage resources on Nutanix after Step 64
```shell
 1. Access Prism.
 2. Select Storage dashboard
 3. Select Table
 4. Select Volume Group
```
###### Quiz.1: Have you found the Volume of Nutanix Volumes created by step 64?
> If it is difficult to find, use the search window to filter the Volume list.
</br>
</br>



## 67: Deploy deamonset app
```shell
kubectl apply -f ./12_daemonset.yaml; watch -n 1 kubectl get po -o wide
```
###### Quiz.1: What information do you see?
###### Quiz.2: How many pods have started up?
###### Quiz.3: How was the pod startup sequence?
###### Quiz.4: How was the pod launching behavior?
</br>
</br>



## 68: Adding Worker node into your Kubernetes cluster
```shell
 1. Access Karbon UI.
 2. Select your kubernetes cluster
 3. Select Nodes
 4. Select Woker
 5. Click "+ Add Worker" button
```
> After this Worker node adding, it takes up to 5 minutes for Pod to startup.
###### Quiz.1: What information do you see? (Watch console execute at Step 67)
###### Quiz.2: How many pods have started up?
###### Quiz.3: How was the pod startup sequence?
###### Quiz.4: How was the pod launching behavior?
</br>
</br>



## 69: Delete few deamonset Pod
> Delete at least two arbitrarily selected pods from DeamonSet pods.
```shell
kubectl delete pod sample-ds-[CHAR_1]; kubectl delete pod sample-ds-[CHAR_2]; watch -n 1 kubectl get po -o wide
```
###### Quiz.1: What information do you see?
###### Quiz.2: How many pods have re-started up?
###### Quiz.3: How was the pod launching behavior?
</br>
</br>



## 70: Delete deamonset Pod
```shell
kubectl delete -f ./daemonset.yaml
```
</br>
</br>



---
#### Congrats! Mission complete.
You learned the a part of basics that one of Kubernetes Work-load resoures (StatefulSet and DaemonSet).
You have been successful deploy StatufulSet with persistent volume and DeamonSet apps.

----> Proceed to [Section-7 (Addtional)](https://github.com/hanakara-milk/Karbon-basics/blob/master/07-section-07.md)
</br>
</br>



