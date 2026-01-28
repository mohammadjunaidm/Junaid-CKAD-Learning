Create these yamls

blue-deployment.yaml - 
====================
          apiVersion: apps/v1
          kind: Deployment
          metadata:
           name: nginx-blue-deploy
          spec:
           replicas: 2
           selector: 
           matchLabels:
            app: blue
          
          template:
           metadata:
            labels:
            app: blue
          
          container:
           -name: nginx
            image: nginx-blue-image
            ports:
             ContainerPort: 80




================================================================================================================================

green-deployment.yaml - 
=======================

     apiVersion: apps/v1
     kind: Deployment
     metadata: 
      name: nginx-green-deploy
    
    spec: 
     replicas: 2
     selector:
      matchLabels:
       app: green
    
    template:
     metadata:
     labels:
      app: green
    
    containers:
      name: nginx-green-deploy
      image: nginx-green-image
      ports:
       ContainerPort: 80

================================================================================================================================

service yaml - 
==============

    apiVersion: v1
    kind: Service
    metadata:
     name : nginx
    
    spec:
      selector:
        version: blue
      port: 
        - protocol: TCP
          port: 80
          targetPort: 80
  
