Vamos começar instalando o argocli;
-> curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
-> sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
-> rm argocd-linux-amd64
-> argocd version

Agora rode o comando para listar as apps;
-> argocd app list
OBS; Aqui você vao receber um erro, isso ocorre porque você apenas instalou o cli não conectou ainda ao "argocd-server"

Para logar rode o comando;
-> argocd login 127.0.0.1:38080
Coloque o login e senha definidos no passo anterior
E agora sim rodo o comando app list;
-> argo app list

Agora que estamos com o cli instalado e plugado no server vamos criar uma app usando o cli;
-> argocd app create app-2 
--repo https://github.com/brunobueno87/kind-labs 
--path ./lab-argo/argo-cd/second-app 
--dest-namespace app-2 
--dest-server https://kubernetes.default.svc

Vamos agora criar o namespace onde queremos que essa app rode;
-> kubectl create ns app-2

OBS; Vá até a UI e veja o status que nova app criada via cli se encontra.

Agora faça o sync da app via cli;
-> argocd app sync app-2


