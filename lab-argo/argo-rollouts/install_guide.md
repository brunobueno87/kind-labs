Segue guia de instalação do argo-rollouts

Comece criando o namespace;
-> kubectl create namespace argo-rollouts

Agora instale o argo-rollouts;
-> kubectl apply --server-side -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml

Acompanhe o progresso;
-> kubectl -n argo-rollouts get all

Instale o cli;
-> wget https://github.com/argoproj/argo-rollouts/releases/download/v1.8.3/kubectl-argo-rollouts-linux-amd64

Modifique a permissão;
-> chmod +x ./kubectl-argo-rollouts-linux-amd64 

Mova para o /usr/local;
-> sudo mv kubectl-argo-rollouts-linux-amd64 /usr/local/bin/kubectl-argo-rollouts

Verifique a versão;
-> kubectl argo rollouts version

Suba a UI;
-> kubectl argo rollouts dashboard


