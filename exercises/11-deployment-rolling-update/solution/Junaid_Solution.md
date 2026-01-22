Created the yaml

    apiVersion: apps/v1
    kind: deployment
    metadata:
      name: junaid-deployment
      labels:
        type: backend
    spec:
        replicas: 4
        selectors: 
          matchlabels:
            app: v2
        templates:
           metadata:
            app: v3
        containers:
          -name: dummy-container
           image: nginx-image

Verified the deployment revisions using the below command:
 kubectl rollout history deployment junaid-deployment

 Described the particular revision using

 kubectl rollout history deployment junaid-deployment --revision=2

 rollbacked to previous revision

 kubectl rollout revision undo deployment/junaid-deployment --to-revision=1
