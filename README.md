# odoo-k8s
learning k8s
work in progress 
using GCP kubernetes engine  (GKE)
using open source Odoo app image (https://github.com/odoo/odoo). 

login and auth to google cli 
commands : 
kubectl create namespace odoo
kubectl apply -f odoo-configmap.yml -n odoo
kubectl apply -f odoo-secret.yml -n odoo
kubectl apply -f odoo-deployment.yml -n odoo