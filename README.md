# referencia-fluxo-trabalho-git

Este documento descreve o fluxo de trabalho que costumo adotar em projetos para desenvolvimento e entrega de funcionalidades.

## Passos do Fluxo de Trabalho

1. Crie um novo projeto na branch `master` com um arquivo `README.md` inicial.

   - A branch `master` é utilizada para conter o código em produção.

2. Crie as branches adicionais: `develop` e `staging`.

   - A branch `develop` é utilizada para desenvolvimento e testes de funcionalidades.
   - A branch `staging` é utilizada para validação de funcionalidades antes da entrega ao cliente final (produção).

3. Crie uma nova _issue_ no GitHub descrevendo a tarefa ou história de usuário a ser implementada.

4. Inicie o desenvolvimento da funcionalidade criando uma nova branch a partir de `staging`. Utilize o seguinte padrão: `feature/i-<numero-issue>-<nome-descritivo>` ou `bugfix/i-<numero-issue>-<nome-descritivo>`.

5. Ao finalizar o desenvolvimento, crie três _merge requests (MRs)_ relacionados à issue:

   - Um MR para a branch `develop`
   - Um MR para a branch `staging`
   - Um MR para a branch `master`

   Certifique-se de adicionar um revisor (se aplicável) e vincular os MRs à issue correspondente. Isso permite um melhor controle das funcionalidades em cada ambiente.

6. O revisor revisa o código e, se aprovado, o MR é mesclado na branch `develop`.

7. O pipeline de `develop` é executado, atualizando todo o ambiente de desenvolvimento.

8. A equipe de QA valida o ambiente de desenvolvimento e, após aprovação, o MR para `staging` é aprovado.

9. O pipeline de `staging` é executado, atualizando todo o ambiente de staging.

10. A equipe de QA valida o ambiente de staging e, após aprovação, o MR para `master` pode ser aprovado.

11. O pipeline de `master` é executado, atualizando todo o ambiente de produção.

12. Após a aprovação do MR para `master`, a funcionalidade é entregue no ambiente de produção e ao cliente final.

13. Crie uma tag seguindo a versão semântica e atualize o CHANGELOG com informações relevantes sobre essa versão.

## Observações

- O processo de criação de três MRs pode parecer excessivo, mas isso permite um controle mais preciso das funcionalidades em cada ambiente, garantindo uma entrega segura e consistente. Ele pode ser simplificado utilizando somente um MR para `develop`, em seguida um MR da `develop` para `staging` e, por fim, um MR da `staging` para `master`.
