Nessa seção vamos falar sobre as diferentes syncronization options que temos em ArgoCD 
Applications.

Vamos continuar usando o application do lab anterior (health-check-app).
Se você for em dateils, verá que não possui nenhuma sync poilcy no momento. Habilite 
o auto-sync. Isso vai detectar qualquer mudança no Git repository  fazer o pull 
automático se encontrar algum drift para aplica-las. Além disso você também pode 
habilitar o self-heal e o prune resources.

Então o self-heal basicamente vai detectar qualquer mudança que você tenha feito 
manualmnte no cluster Kubernetes e vai tentar sincronizar para corresponder ao desired 
state.

Ao mesmo tempo, se você quiser usar prune resources, se deletar um resource do seu 
repositório Git, este resource também será deletado no cluster Kubernetes.

Boa agora vá até o repo  aumente o número de replicas para 2 faça o commit dessa mudança.

Além disso delete o service da nossa app.

Veja que logo em seguida o resource é recriado, isso poque temos o Self-heal habilitado nesta application.

Bom vamos ver a config de "Prune Resources". Quando está opção esta ativada o que você 
delear no seu github é deletado igualmente no seu cluster. Bom então remova o arquivo o
service do seu repo. Commite essa mudança e veja acontecer na UI do Argo.
