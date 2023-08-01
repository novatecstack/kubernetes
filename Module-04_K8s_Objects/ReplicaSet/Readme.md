# ReplicaSets

## Introduction to ReplicaSets
   - A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. 
   - As such, it is often used to guarantee the availability of a specified number of identical Pods.
   - A *ReplicaSet* is defined with fields:
     - A *selector* that specifies how to identify Pods it can acquire
     - A number of *replicas* indicating how many Pods it should be maintaining, and 
     - A pod template specifying the data of new Pods it should create to meet the number of replicas criteria.
 
## replicaSet Examples

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

## Non-template Pod aquisitions (Pods with same Labels as an existing replicaSet's selector)

