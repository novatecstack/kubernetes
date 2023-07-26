# Kubernetes Objects

  - Kubernetes objects are persistent entities in the Kubernetes system. 
  - Kubernetes uses these entities to represent the state of your cluster. 
    - Specifically, they can describe:
    - What containerized applications are running (and on which nodes)
    - The resources available to those applications
    - The policies around how those applications behave, such as restart policies, upgrades, and fault-tolerance

## What K8s Objects are available?
   1) Pods
   2) Namespaces
   3) replicaSets
   4) deploymentController
   5) StatefulSet
   6) Service
   7) ConfigMaps
   8) Volumes

## Kubernetes Object Management: *Objects and APIs*
   - This section provides an overview of the different approaches to manage K8s objects.
   - K8s Object management techniques are:
     1) [<b>*Imperative commands*</b> - Commands](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/#imperative-commands)
     2) [<b>*Imperative object configuration*</b> - Individual files](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/#imperative-object-configuration)
     3) [<b>*Declarative object configuration*</b> - Directories of files](https://kubernetes.io/docs/concepts/overview/working-with-objects/object-management/#declarative-object-configuration)

### K8s Objects and IDs
   - Each object in your cluster has a Name that is unique for that type of resource. 
   - Every Kubernetes object also has a UID that is unique across your whole cluster.
   - For example, you can only have one Pod named *NOVA-WEBAPP-POD* within the same namespace, but you can have one *Pod* and one *Deployment* that are each named myapp-1234.  


### [What are *Labels* and *Selectors* in K8s?](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)
   - Labels are key-value pairs that are attached to objects such as Pods. 
   - Labels are intended to be used to specify identifying attributes of objects that are meaningful and relevant to users, but do not directly imply semantics to the core system. 
   - Labels can be used to organize and to select subsets of objects. 
   - Labels can be attached to objects at creation time and subsequently added and modified at any time. 
   - Each object can have a set of key/value labels defined. 
   - Each Key must be unique for a given object.
   
   ```
   "metadata": {
      "labels": {
        "key1" : "value1",
        "key2" : "value2"
      }
    }

   ```

Example labels:
  - "release" : "stable", "release" : "canary"
  - "environment" : "dev", "environment" : "qa", "environment" : "production"
  - "tier" : "frontend", "tier" : "backend", "tier" : "cache"
  - "partition" : "customerA", "partition" : "customerB"
  - "track" : "daily", "track" : "weekly"