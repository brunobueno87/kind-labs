🧪 Kubernetes Labs
Este repositório tem como objetivo centralizar meus labs práticos de Kubernetes e do ecossistema cloud native, com foco em estudo, testes, POCs e boas práticas.
A ideia é organizar cada tecnologia em seus próprios diretórios, mantendo passo a passo claro, exemplos práticos e comandos reproduzíveis.

🎯 Objetivos do Repositório

Centralizar estudos e experimentações com Kubernetes
Servir como referência futura e material de consulta
Facilitar a reprodução dos labs em ambientes locais
Documentar aprendizados de forma simples e prática


🛠️ Pré-requisitos Gerais
A maioria dos labs deste repositório assume que você possui:

✅ Docker

✅ kubectl

✅ kind (Kubernetes in Docker)


🔎 Algumas pastas podem ter pré-requisitos específicos, descritos em seus próprios READMEs.


📁 Estrutura do Repositório
A estrutura segue o modelo tecnologia → subcomponentes → passo a passo.
(Ajustar esse ponto)


🔀 Organização dos Labs
🔹 kind
Labs relacionados à criação e gerenciamento de clusters Kubernetes locais usando Kind.
Exemplos:

Subir cluster limpo
Deploy básico para validação
Port-forward e acesso externo


🔹 argo
Diretório dedicado ao ecossistema Argo, com cada ferramenta separada em subdiretórios próprios:
📂 argo/argo-cd

Instalação do Argo CD
Acesso ao dashboard
Primeiro app GitOps
Sync manual e automático

📂 argo/argo-workflows

Conceitos básicos de workflows
Execução de pipelines
YAMLs de exemplo

📂 argo/argo-rollouts

Estratégias de deploy (Blue/Green, Canary)
Traffic shaping
Integração com ingress/service mesh (quando aplicável)

📂 argo/argo-events

Conceitos de event-driven
EventSources e Sensors
Integração com workflows

Cada subdiretório contém seu README.md próprio, com:

Objetivo do lab
Pré-requisitos específicos
Passo a passo
Comandos
Observações importantes

