# K8s ReplicaSets

## Introduction to K8s ReplicaSets
   - A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. 
   - As such, it is often used to guarantee the availability of a specified number of identical Pods.
   - A *ReplicaSet* is defined with fields:
     - A *selector* that specifies how to identify Pods it can acquire
     - A number of *replicas* indicating how many Pods it should be maintaining, and 
     - A pod template specifying the data of new Pods it should create to meet the number of replicas criteria.
 
## ReplicaSet Manifest Structure

   ```
   apiVersion: apps/v1
   
   kind: ReplicaSet
   
   metadata:
      name: <name_of_replicaSet>
   
   spec:
      replicas: <no_of_replica_of_app>
      selector:
         matchLabels:
            <key>: <selector_label_of_rs>
      template:
         metadata:
            labels:
               <key>: <selector_label_of_rs>
         spec:
            containers:
            - name: <name_of_container>
              image: <container_img>
            ...
   ```


## Create a replicaSet
   Saving your manifest into `filename.yaml` and submit it to a Kubernetes cluster and it will create the defined ReplicaSet and the Pods that it manages.
   
   ```
    kubectl apply -f frontend.yaml

   ```

## Get the list of replicaSets
   
   ```
   kubectl get rs
   ```
   or 

   ```
   kubectl get replicasets
   ```
## Describe the replicaSet
   
   ```
   kubectl describe replicaset <name_of_replicaset>
   ```

## Update the replicaSet
   
   ```
   kubectl edit replicaset <name_of_replicaset>
   
   # and update the `replicas` value and save the file. Now list the pods to verify the pod count:

   kubectl get pods
   ```

   or you may run below command:
   ```
   kubectl scale replicaset <replicaset_name> --replicas=4
   
   # List the pods to verify the pod count:

   kubectl get pods
   ```

## Check the state of replicaSet

   ```
   kubectl describe rs/frontend
   ```
## Check the list of Pods got created those are asociated with a replicaSet

   ```
   kubectl get pods
   ```

## Check the `owner reference` of the pods associated with a replicaSet

   ```
   kubectl get pods <pod_name> -o yaml
   ```

## Non-template Pod aquisitions - Pods with same Labels as an existing replicaSet's selector

### Scenario-01: Create replicaSet with a particular `selector` and then Pods with the same `label` as selector
   - When you create bare Pods which match the selector of one of your ReplicaSets, the new Pods will be acquired by the ReplicaSet and then immediately terminated as the ReplicaSet would be over its desired count.
   - Hence it is strongly recommended to make sure that the bare Pods do not have labels which match the selector of one of your ReplicaSets

### Scenorio-02: Create a Pod with a particular `label` and then create a replicaSet with the same `selector`
   - If you create the Pods first and then create the ReplicaSet, then the ReplicaSet will acquire the existing Pods and will only create new ones according to its spec until the number of its new Pods and the original matches its desired count.

   ```
   kubectl get pods
   ```
   will give the below output:

   ```
   NAME                READY    STATUS    RESTARTS   AGE
   frontend-bin2x       1/1     Running   0          5s
   new-pod1             1/1     Running   0          48s
   new-pod2             1/1     Running   0          48s
   ```