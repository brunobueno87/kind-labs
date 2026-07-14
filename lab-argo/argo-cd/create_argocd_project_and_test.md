Nesta seção vamos criar um novo argo project. Recapitulando o que é um project. Nada mais 
é que um agrupamento lógico para applications, o que é util se você trabalha com multiplos 
times na sua organização.
É nele que restringimos que tipo de objetos podem ser criado no Kubernetes qual repo que 
pode ou não "fazer entregas" no cluster, você pode usar também sync windows a nível global.

Para criar seu project vá até, a UI, clique em Settings e depois em Projects e você verá o 
default projects, que tem acesso irrestrito a todos os sources repositories, todos os 
destinations, e também tem acesso à cluster resource allow list.

Você também pode criar uma deny list se necessário.
Bom, clique em "New Project" > vamos colocar o nome de Deny List.
No nosso caso, vamos apenas restringir a criação de recurso via cluster, então clique em 
"Custer resource allow list" vá em editar > em add resource > cluster resource deny list > 
selecione a opção "cluster role", vá em destinations e add * nas opçoes, vá em source 
repositories e add *

Agora vamos para o terminal e vamos criar uma nova application apontando para esse novo project;
argocd app create testing-project 
--repo https://github.com/brunobueno87/kind-labs 
--path ./lab-argo/argo-cd/pod-metadata 
--dest-namespace default 
--project deny-list 
--dest-server https://kubernetes.default.svc

Agora vá até a UI e tente fazer um sync, você tem que receber uma falha para que o lab esteja com sucesso.
