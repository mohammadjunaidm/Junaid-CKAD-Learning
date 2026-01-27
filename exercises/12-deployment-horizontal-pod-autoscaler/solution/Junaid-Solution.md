Create a new deployment yaml as shown below 

    apiVersion: apps/v1
    kind: Deployment
    metadata:
     - name: nginx
    spec:
    replicas: 3
    selectors:
      matchlabels:
      apps: nginx
    template:
    metadata:
     labels:
     app: nginx
    containers:
     - name: nginx
       image: nginx-image
       resources:
        requests:
         cpu: 0.5
         memory: "450mi"
        limits:
         memory: "450mi"

  Once applied the above deployment yaml for creating 3 pods, create the horizontal pod auto scaler using the below yaml

    apiVersion: autoscaling/v2
    kind: horizontalpodautoscalar
    metadata:
     - name: nginx-hpa
    spec:
      scaleTargetRef:
        apiVersion: apps/v1
        kind: Deployment
        name: nginx
        maxreplicas: 8
        minreplicas: 3
        metrics:
        -Type: Resource
         resource:
         -name: CPU
         target:
           type: Utilization
         averageUtilization: 75
       -Type: Resource
         resource:
         -name: Memory
         target:
           type: Utilization
         averageUtilization: 60

  check the created HPA and the deployment pods.
  
     
