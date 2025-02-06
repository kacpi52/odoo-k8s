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
kubectl apply -f odoo-deployment.yml -n odoo .... dalsze deploymenty itd

install ingress nginx controller :
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.5.1/deploy/static/provider/cloud/deploy.yaml
to check nginx controller instalation:
kubectl get pods -n ingress-nginx -l name=ingress-nginx --watch

later after apply all yml 
kubectl apply -f ingress.yml 

then type 
kubectl get ingress 
and select the value from ADDRESS and paste it in your browser 

odoo app credentials:
 email: user@example.com
 password: bitnami