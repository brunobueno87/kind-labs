Vamos falar sobre a opção ignore-differences dentro do application specification.

Vamos pegar como exemplo o auto scale. Onde você quer que sua app seja capaz de escalar a quantidade de replicas sem que o Self-heal sobreponha esse comportamento.

Boa pegando nossa ultim app de exemplos, vamos escalar ela para 10 replicas;

-> kubectl -n health-check scale deployment random-shapes --replicas 10

Vá até  UI que veja que até scala, mas automaticamente ela volta paa o desiredstate.

Para adicionar o ignore diferences, vá até a UI, em Details da application, vá até manifest. Clique em editar e adicione no final;

...
ignoreDifferences:
  - group: apps
    kind: Deployment
    name: random-shapes
    namespace: health-check
    jsonPointers:
      - /spec/replicas
...

Salve isso, vá até sync, e ative a opção;

RESPECT IGNORE DIFFERENCES

Faça o scale novamente e veja que agora ele mantem as replicas.

