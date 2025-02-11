# odoo-k8s
Oddo app runned with kubernetes using GCP kubernetes engine  (GKE) and GCP persistent disk

## How to run this project: 

- login and auth to google cli 
- connect to your gcp k8s cluster:
```
gcloud auth login
gcloud config set project <your_project_name>
gcloud container clusters get-credentials <your_cluster_name> --zone <your_zone_name> --project <your_project_name>

``` 

#### Then run commands :

```
kubectl create namespace odoo
kubectl apply -f odoo-configmap.yml -n odoo
kubectl apply -f odoo-secret.yml -n odoo
kubectl apply -f odoo-deployment.yml  
kubectl apply -f odoo-service.yml
kubectl apply -f odoo-pvc.yml 
kubectl apply -f postgres-deployment.yml 
kubectl apply -f postgres-service.yml 
```
#### Then install ingress nginx controller :
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.5.1/deploy/static/provider/cloud/deploy.yaml
```
#### Check nginx controller instalation:
```
kubectl get pods -n ingress-nginx -l name=ingress-nginx --watch
```

#### Then apply ingress resource 

``` 
kubectl apply -f ingress.yml 
```

#### Then type and select the value from ADDRESS and paste it in your browser 
```
kubectl get ingress -n odoo
``` 
![cli](images/ingress_04_cli.jpg)
![public ip](images/ingress_04_working_app.jpg)
#### Odoo app default credentials:
 - email: user@example.com
 - password: bitnami

## Dont forget to cleanup :

```
kubectl delete -f ingress.yml 
kubectl delete -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.5.1/deploy/static/provider/cloud/deploy.yaml
kubectl delete -f postgres-deployment.yml -f odoo-deployment.yml  
kubectl delete -f odoo-service.yml -f postgres-service.yml -f odoo-pvc.yml
```

#### Section Notes and Resources
This project contains open source Odoo app image (https://github.com/odoo/odoo). 