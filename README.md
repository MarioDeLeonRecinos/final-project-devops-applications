# final-project-devops-applications

## Gcloud connect cluster

gcloud container clusters get-credentials my-gke-cluster

gcloud container clusters get-credentials my-gke-cluster --zone us-west1-c --project week9-356019  && kubectl get secret gcr-json-key --namespace my-website -o yaml

## Helm install nginx-controller and cert-manager

helm install my-nginx-ingress ingress-nginx/ingress-nginx -n nginx-cert-manager -f .\values\nginx-controller.yaml

 helm install my-cert-manager cert-manager/cert-manager -n nginx-cert-manager --set installCRDs=true

## Install cluster-issuer

kubectl apply -f cluster-issuer.yaml -n nginx-cert-manager

## Install argo-cd and recover password

helm install my-argo-cd argo/argo-cd --version 4.9.5 -n argocd -f .\values\argo-cd-values.yaml

helm install my-argo-rollouts argo/argo-rollouts --version 2.17.0

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

PQ5CLqhj4KSOKTns

## Install names

my-kube-prometheus-stack

my-prometheus-blackbox-exporter
