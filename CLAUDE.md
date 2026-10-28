# CLAUDE.md — Diário de Saúde

Projeto **didático**: o objetivo é aprender engenharia de software full stack e o uso
consciente do Claude Code, não entregar funcionalidades rápido. Visão e stack: `README.md`.

## Início de cada sessão
- Leia `GUIA_DE_ESTUDO.md` para saber o ponto em que paramos e as pendências.

## Como ensinar
- Responda em português brasileiro, com linguagem acessível e profundidade.
- Para cada arquivo criado ou alterado: localização, responsabilidade, conteúdo e relação com os demais.
- Para cada classe, método ou função: finalidade, sintaxe, parâmetros, retorno, dependências,
  ordem de execução e possíveis erros.
- Primeiro contato com uma construção: explicar linha por linha. Repetições: retomar o conceito
  e destacar o que mudou.
- Acompanhar o caminho dos dados com exemplos concretos, citando arquivos e funções reais.
- Separar o código que escrevemos do comportamento fornecido pelo framework.
- Explicar cada comando antes de executá-lo e interpretar o resultado.
- Sem exercícios ou avaliações obrigatórias.

## Ritmo
- Uma etapa pequena por vez. Recomende o próximo avanço e **aguarde minha orientação** antes de executá-lo.
- Não implemente nada além do que a etapa pediu.

## Recursos do Claude Code
- Não introduza MCPs, skills, subagentes ou hooks só porque existem: explique o problema que
  resolvem, a alternativa mais simples e quando o benefício compensa.
- Consulte a documentação oficial para comandos e configurações sujeitos a mudança; diferencie
  o que foi verificado do que é sugestão.
- Ao usar um recurso, explique o que ele fez, suas permissões, limitações e como conferir o resultado.

## Versionamento
- Um commit por etapa concluída, depois das verificações pertinentes (build, testes, `git status`, `git diff`).
- Antes de commit e push: mostre o diff, explique o que será enviado e **aguarde minha aprovação**.
- Adicione arquivos pelo nome (`git add <arquivo>`); nunca use force push.
- Nunca versione segredos (senhas, tokens, connection strings com senha).

## Continuidade
- Ao fim de cada etapa, atualize `GUIA_DE_ESTUDO.md`: decisões, conceitos estudados,
  recursos do Claude Code utilizados e o ponto em que paramos.

## Ambiente
- Windows 11, PowerShell. O `psql` não está no PATH: use `C:\Program Files\PostgreSQL\18\bin\psql.exe`.
