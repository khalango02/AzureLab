# Provision an EKS Cluster

.Terraform init

.Terraform plan

.Terraform apply

.Rodar o comando na máquina local: aws eks --region $(terraform output -raw region) update-kubeconfig \
    --name $(terraform output -raw cluster_name)

.Validar as informaçoes do cluster: kubectl cluster-info

.Verificar os nodes: kubectl get nodes


SERVICE =====================================================================================================================================

kubectl run nginx-pod --image=nginx --restart=Never --port=80 -n default

kubectl expose pod nginx-pod --type=LoadBalancer --port=80 --name=nginx-service

kubectl get svc

export loadbalancer=$(kubectl get svc nginx-service -o jsonpath='{.status.loadBalancer.ingress[*].hostname}')

echo ${loadbalancer}

curl -k -s http://${loadbalancer} | grep title

SERVICE + ====================================================================================================================================

.kubectl apply -f https://k8s.io/examples/service/load-balancer-example.yaml || kubectl apply -f SERVICE-KUBE.yaml

.kubectl expose deployment hello-world --type=LoadBalancer --name=my-service

.curl http://<external-ip>:8080



