# final-project-devops-applications

## Gcloud connect cluster

gcloud container clusters get-credentials my-gke-cluster

gcloud container clusters get-credentials my-gke-cluster --zone us-west1-c --project micro-flight-356719

gcloud container clusters get-credentials my-gke-cluster --zone us-west1-c --project smooth-obelisk-356719

### Optional

&& kubectl get secret gcr-json-key --namespace my-website -o yaml

## Helm install nginx-controller and cert-manager

helm install my-nginx-ingress ingress-nginx/ingress-nginx -n nginx-cert-manager -f .\values\nginx-controller.yaml

helm install my-cert-manager cert-manager/cert-manager -n nginx-cert-manager --set installCRDs=true

## Install cluster-issuer

kubectl apply -f cluster-issuer.yaml -n nginx-cert-manager

## Install argo-cd and recover password

helm install my-argo-cd argo/argo-cd --version 4.9.5 -n argocd -f .\values\argo-cd-values.yaml

helm install my-argo-rollouts argo/argo-rollouts --version 2.17.0

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

QPFMPGKvgdrcUMPP

hLwsbkqq2TNojlJ7

## Install names

my-kube-prometheus-stack

my-prometheus-blackbox-exporter

## Secret create in Linux base console

kubectl create secret docker-registry gcr-json-key \
--docker-server=us.gcr.io \
--docker-username=_json_key \
--docker-password="$(cat ~/corresponding-json-key.json)" \

### Project dependant

--docker-email=cloud-build@micro-flight-356719.iam.gserviceaccount.com -n minio

--docker-email=cloud-build@smooth-obelisk-356719.iam.gserviceaccount.com -n minio

### Recover generated secret

kubectl -n minio get secret gcr-json-key -o jsonpath="{.data.*}" | base64 -d
