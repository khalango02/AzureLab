# cluster-k8s-terraform-ansible

PRÉ-REQUISITOS ==============================================================================================================================

.AZURE-CLI

.TERRAFORM

.SSH




TERRAFORM ===================================================================================================================================

.Localmente rodar o comando: terraform init

.Localmente rodar o comando: terraform plan

.Localmente rodar o comando: terraform apply




ANSIBLE =====================================================================================================================================

.Acessar todas as máquinas.

.sudo apt update

.sudo apt install ansible


.Subir os arquivos da master e seus workers em suas respectivas máquinas

.Rodar os arquivos da Master: ansible-playbook main-master.yml

.Rodar os arquivos dos Workers: ansible-playbook main-workers.yml


.Rodar o comando no master: kubeadm token generate

.Pegar o token gerado e incluir no comando, na master: kubeadm token create {TOKEN_GERADO} --print-join-command

.Rodar o comando gerado no worker: kubeadm join 192.168.56.110:6443 --token hp9b0k.1g9tqz8vkf78ucwf     --discovery-token-ca-cert-hash sha256:32eb67948d72ba99aac9b5bb0305d66a48f43b0798cb2df99c8b1c30708bdc2c


.Para validar o funcionamento, acessar a máquina master e rodar o comando: kubectl get nodes -o wide




SERVICE =====================================================================================================================================

.Subir o arquivo quickstart.yaml na máquina master

.Rodar o comando na master: kubectl apply -f quickstart.yaml

.Acompanhe o deploy: kubectl get pods -w

.Verifique se a aplicaçao já possui um IP publico(EXTERNAL-IP), de início estará como pendente: kubectl get service store-front --watch

.Acesse o IP publico

