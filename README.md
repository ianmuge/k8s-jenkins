# Setup
The system is deployed on AKS with the jenkins data stored persistented across Deployments.
We install and configure a number of plugins in Jenkins:
- Kubernetes
- Blue Ocean
- Strict Crumb Issuer
# Deployment
We use the AKS HTTP routing ingress. It provides a FQDN we can use to expose and reach our service from outside the cluster. We configure the FQDN in `ingress.yml` by appending it to the defined jenkins host.
We install the manifests as shown below
```
kubectl apply -f setup.yml
kubectl apply -f jenkins.yml
kubectl apply -f ingress.yml
```
Jenkins would use the default storage class in the volume clasim to store the data, you can define and deploy a custom StorageClass.
