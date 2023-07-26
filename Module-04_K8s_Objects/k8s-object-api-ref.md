# Which Kubernetes apiVersion should I use in my config file?
  - When we create Kubernetes resource manifests, one of the first important things that we need to specify for the resource is the apiVersion.
- An object definition in Kubernetes requires a *apiVersion* field. 
- When Kubernetes has a release that updates what is available for you to use, changes something in its API — a new apiVersion is created.

## *apiVersion* of various K8s Objects

   | Kind  | apiVersion |
   | ------------- | ------------- |
   | Pod     |  v1 |
   | Namespace     |  v1 |
   | Service     |  v1 |
   | PersistentVolumeClaim     |  v1 |
   | PersistentVolume     |  v1 | 
   | StatefulSet     |  apps/v1 |
   | Deployment     |  - |
   | ReplicaSet     |  - |  
   | HorizontalPodAutoscaler     |  - |
   | Ingress     |  - |
   | Secret     |  - |  
   | ResourceQuota     |  - |

## What does various *apiVersion* mean?
   - alpha
     - API versions with ‘alpha’ in their name are early candidates for new functionality coming into Kubernetes. 
     - This is not stable for use and may contain bugs.
     
   - beta
    *beta* in the API version name means that testing has progressed past alpha level and that the feature will eventually be included in Kubernetes. Although the way it works might change, and the way objects are defined may change completely, the feature itself is highly likely to make it into Kubernetes in some form.

   - stable
     - They are safe to use. These do not contain ‘alpha’ or ‘beta’ in their name.

   - v1
     - v1 version was the first stable version release of the Kubernetes API. 
     - It contains many core objects in Kubernetes.

   - apps/v1
     - apps is the most common API group in Kubernetes, with many core objects. 
     - It includes various functions like running applications on Kubernetes, like Deployments, RollingUpdates, and ReplicaSets.

   - autoscaling/v1
     - This API version autoscaling/v1 allows pods to be autoscaled based on different resource usage metrics. 
     - Kubernetes autoscaling helps optimize resource usage and costs by automatically scaling a cluster up and down. 
     - Autoscaling is totally dependent on demand.