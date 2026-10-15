# Avaliação: GitHub Actions com IA
Dupla: NOME 1 e NOME 2

## Tarefa 1
- Execução verde: (https://github.com/vitornasciment123-spec/Public/actions/runs/38315846458)
- Execução vermelha: (https://github.com/vitornasciment123-spec/Public/actions/runs/38315555923)
- Linha do erro: Parse error near line 1: near "TABL": syntax error
  CREATE TABL teste (id INTEGER);
- Por que testar no SQLite antes: o D1 é SQLite, então o CI acha erros de sintaxe antes de tocar o banco de produção.

## Tarefa 2
- PR bloqueado e liberado: LINK DO PR #1
- Saída do git push recusado: https://github.com/vitornasciment123-spec/Public/actions/runs/38315108534
  remote: error: GH013: Repository rule violations found for refs/heads/main.
  remote: - Changes must be made through a pull request.
  remote: - Required status check "verificar" is expected.
  ! [remote rejected] main -> main (push declined due to repository rule violations)

## Tarefa 3 (parcial)
- Workflow revisao-ia.yml criado e funcionando; a IA publicou comentário no PR: LINK DO PR #2
- PR com SQL vulnerável, teste de permissão e crítica à IA: não realizados por falta de tempo.
- Dificuldade encontrada: o segredo COPILOT_PAT estava vazio no GitHub (criado apenas na Cloudflare), o que fazia o Copilot CLI sair com código 1. A ação foi trocada de @v1 para @main.

## Tarefa 4
Não realizada por falta de tempo.

## Perguntas
1. O ci.yml tem os gatilhos push e pull_request, então roda uma vez para cada evento. O check obrigatório é identificado pelo nome (verificar), e os dois aparecem como Required no PR.
2. Fork não recebe segredos porque qualquer pessoa poderia abrir um PR que imprime ou envia os segredos do repositório de destino. A regra impede esse vazamento (exfiltração).
3. Declarar permissions aplica o menor privilégio: o token só lê o código e comenta em PR, limitando o dano se o workflow for abusado.
4. Não. A IA pode errar ou inventar problemas e não é determinística nem bloqueia o merge. O CI dá um resultado objetivo e repetível.
