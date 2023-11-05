# lab4-fullstack
Lab 4 cloud full-stack programming

This YAML file defines the configuration for resources in a Kubernetes cluster:

The first section defines a Namespace named "lab4" with an annotation "resourceQuota" set to "lab4-quota".

The second section defines a ResourceQuota named "lab4-quota" in the "lab4" namespace. Resource limits include a maximum of 5 pods and maximum resource requests of 1000 milicores CPU and 1GiB RAM.

The third section defines a Deployment named "restrictednginx" in the "lab4" namespace. This deployment has 3 replicas and uses a selector to choose pods with the label "app: restrictednginx". The containers in the pods use the nginx image and specify resource limits and requests for CPU and memory.

This YAML file creates a "lab4" namespace with a "lab4-quota" resource limit and a "restrictednginx" deployment with specific resource constraints and requirements for its containers.

After using this YAML file, you can validate the correctness of the deployment. Here's how to do it:

1. Apply the YAML file using:
- kubectl apply -f conf.yaml

2. To get information about namespace (CPU and RAM limits, max PODS):
- kubectl describe namespace lab4
   
3. To get information about the ResourceQuota and check if it has the expected limits (information included in prevoius command):
- kubectl describe resourcequota -n lab4 lab4-quota
  
4. To list the Deployments in the "lab4" namespace:
- kubectl get deployments -n lab4

5. To get information about deplyment (Pod template, conditions, etc.):
- kubectl describe deployment -n lab4 restrictednginx

6. To inspect the pods created by the Deployment to ensure they are running correctly:
- kubectl get pods -n lab4

7. To inspect each of the pods created by the Deployment (Conditions, events, etc.):
- kubectl describe pod -n lab4 "pod_name"

8. To get information about all items in namespace:
- kubectl get all -n lab4
