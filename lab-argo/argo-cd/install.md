Guia de Instalação e Configuração do ArgoCD 

Este guia descreve os passos técnicos para implantar e configurar o ArgoCD em um 
cluster Kubernetes.

1. Preparação do Namespace - O primeiro passo é criar um namespace isolado. 
Isso garante que os componentes do ArgoCD fiquem separados de outras aplicações do 
cluster.
$ kubectl create namespace argocd

2. Instalação dos Componentes - A instalação utiliza o manifesto oficial. 
Este comando sobe o API Server, o Repository Server e o Application Controller.
$kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.14.9/manifests/install.yaml

3. Acesso à Interface Web (Port-Forward) Para acessar o dashboard gráfico a partir da 
sua máquina local, utilize o redirecionamento de porta. 
O comando abaixo mapeia a porta local 32766 para a porta 80 do serviço do ArgoCD.
$kubectl -n argocd port-forward svc/argocd-server 32766:80

Após rodar o comando, acesse no navegador: http://localhost:32766

4. Recuperação da Senha do Administrador - O ArgoCD gera uma senha inicial aleatória 
armazenada em um Secret. O comando abaixo extrai o valor, remove quebras de linha e 
decodifica o padrão Base64 para texto legível.
$kubectl -n argocd get secrets argocd-initial-admin-secret -o json | jq .data.password -r | tr -d '\n' | base64 -d

Usuário padrão: admin
Senha: O resultado do comando acima.

5. Instalação do ArgoCD CLI (Linux) - A CLI é essencial para gerenciar o GitOps via 
terminal. Os comandos abaixo baixam a versão estável correspondente e aplicam a 
permissão de execução.

# Download do binário
curl -sSL -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/download/v2.14.9/argocd-linux-amd64

# Permissão de execução
sudo chmod +x /usr/local/bin/argocd
