Wrote this yaml on my own which met all the requirements.
    
    apiVersion: v1
    kind: Pod
    metadata:
      name: junaid-business
    spec:
      initContainers:
      - name: configurer
        image: busybox:1.36.1
        command: 
        - wget
        - "-O"
        - "/usr/shared/app/config.json"
        - "https://raw.githubusercontent.com/bmuschko/ckad-crash-course/master/exercises/07-init-container/app/config/config.json"
        volumeMounts:
        - name: config-volume
          mountPath: /usr/shared/app
    
      containers:
      - name: web
        image: bmuschko/nodejs-read-config:1.0.0
        ports:
        - containerPort: 8080
        volumeMounts:
        - name: config-volume
          mountPath: /usr/shared/app
    
      volumes:
      - name: config-volume
        emptyDir: {}
