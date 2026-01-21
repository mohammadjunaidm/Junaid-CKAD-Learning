Wronte the below yaml to create 3 pods and edited each pod yaml and filtered the labels using selectors. Screenshot attached.
    
    
    apiVersion: v1
    kind: Pod
    metadata:
      name: frontend
      labels:
      env: prod
      team: shiny
      labels
    spec:
      container:
      name: nginx
      image: nginx-image
      restartPolicy: Never
    
    apiVersion: v1
    kind: Pod
    metadata:
      name: backend
      labels:
      env: prod
      team: legacy
      version: v1.2.3
    spec:
     container:
     -name: nginx
     image: nginx-image
     restartPolicy: Never
    
     apiVersion: v1
     kind: pod
     metadata:
       name: database
       labels:
       env: prod
       team: storage
     spec:
       containers:
         -name: nginx
         image: nginx-image
       restartPolicy: Never
    
       
