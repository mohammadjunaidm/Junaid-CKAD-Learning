Added the repo using 

    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

Updated the repo using 

    helm repo update prometheus-community

Searched the repo using 

    helm search hub prometheus-community

Installed the helm using

     helm install prometheus prometheus-community/kube-prometheus-stack

Viewed the available helm charts using 

    helm list

To view the installed prometheus using helm , we use port forwarding using 

    kubectl port-forward service/prometheus-operated 8080:9090

Uninstalled the helm chart for Prometheus using

    helm uninstall prometheus
    
