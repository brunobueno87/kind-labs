Nesta seção vamos criar um customo health check no ArgoCD para verificar nosso recurso ConfigMap.
Como já sabemos o ArgoCD já oferece vários health assessments nativos para diversos 
tipos padrão do Kubernetes.
Mas, além disso, se você quiser criar um novo healthcheck, podemos fazer isso com a 
ajuda de um Configmap.
Então o nome do ConfigMap é argocd-cm e é nele onde você consegue definir um custom 
health check.
No nosso exemplo, vamos criar uma nova ArgoCD Application e ver como ela funciona com
e sem o health check.
Sendo assim vamos criar uma nova application, vamos via cli dessa vez;

argocd app create health-checkapp 
--repo https://github.com/brunobueno87/kind-labs
--path ./health-check
--dest-server https://kubernetes.default.svc
--dest-namespace health-check
--project default
--revision HEAD
--sync-policy none
--sync-option CreatNamespace=true

Agora vá até a UI e veja o novo application, obviamente ele ainda não vai estar
sincronizado, faça o sync.
Faça um forward do service dessa nova app, e acesse via Browser.
Agora veja que existe entre as formas flutuando na pagina um triangulo em branco, que
é quase imperceptivel.
Bom então nós temos que editar o configmap para alterar isso,porém antes vamos 
configurar um healthcheck para esse recurso para simular que queremos acompanhar isso.
Vamos até o configmap argocd-cm;
-> kubectl -n argocd edit cm argocd-cm

E logo no começo do arquivo, em data: coloque o trecho de código abaixo;

...
  resource.customizations.health.ConfigMap: |
    hs = {}
    hs.status = "Healthy"
      if obj.data.TRIANGLE_COLOR == "white" then
         hs.status = "Degraded"
         hs.message = "Use any color other than white"
      end
    return hs
...

Salve e saia, vá até a UI e faça um refresh e veja que a app vai aparecer com status
"Degraded" 
Show agora pela UI mesmo, vá até o configmap degradada e edite de white para red o 
triangulo.

Veja que após essa alteração, o status de degraded sumiu do app. Faça um restart do 
deploy pela UI mesmo.
Vá até o browser onde esta aberto o service da app e veja a alteração.
É com base nesse exemplo você pode criar custom health check para verificar as 
configurações de kubernetes resources.
