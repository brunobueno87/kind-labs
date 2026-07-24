Vamos falar sobre sync hooks, sync phases e hooks são basicamente usados para definir 
como os resources são aplicados, como antes ou depois da operação principal de sync.
Nesta seção vamos fala especificamente sobre os tipos de hook.
Então temos os hooks de pré-sync, sync, skip, post-sync, sync-failure e post-delete.
E é assim que as phases funcionam, meio auto explicativo.
Então ele começa com pré sync, se for bem sucedido, ele segue para a synchronization.
Se falhar no sync stage, ele vai disparar a fase de sync-fail.
Se a sync phase tiver sucesso, então ele vai disparar a post-sync-phase.
E dentro da sincronização, também temos diferentes hook, life cycles e cleanups, que 
veremos na proxima demo.
Por enquanto vamos considear um cenário.
No nosso repo de trabalho temos o diretório (lab-argo/argo-cd/synchronization/hook/) 
dentro desse diretório existe 3 kubernetes resources.
Boa vamos criar uma nova application, com o nome sync-hooks-1, no project deault, a 
sync policy é Automatic, selecione o auto-create-namespace.
Passe o repo, e o path, coloque o cluster url, e o nome do name-space será (sync-hooks-0)
Veja na UI que 3 pods serão criados paralelamente, assim como o deployment. Vamos mudar
isso para que o migration-job seja o primeiro, e assim que for concluído com sucesso, 
queremos que o deployment do nginx seja feito, e se o deployment for bem sucedido, o 
job de cleanup deve ser criado.
Vamos então adicionar annotations nos respectivos ymls para garantir que siga uma 
sequencia lógica.
