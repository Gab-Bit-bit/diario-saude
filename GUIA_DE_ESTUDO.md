# Guia de Estudo — Diário de Saúde

Registro da continuidade do estudo. Visão do projeto: `README.md`. Regras de trabalho: `CLAUDE.md`.

## Ponto em que paramos

Etapa 3 concluída — `CLAUDE.md` e este guia revisados, versionados e enviados ao GitHub.
Próxima etapa ainda não definida. Nenhuma funcionalidade implementada.

## Etapas concluídas

| # | Etapa | Resultado |
|---|-------|-----------|
| 1 | Verificação do ambiente | Ferramentas abaixo confirmadas por comandos de consulta. Nada instalado. |
| 2 | Preparação do versionamento | Repositório local criado, conectado ao GitHub; commit `92cd6dc` enviado. |
| 3 | Instruções e continuidade | `CLAUDE.md` e `GUIA_DE_ESTUDO.md` criados, revisados e enviados. |

## Ambiente (confirmado em 2026-10-28)

| Ferramenta | Situação | Como foi verificado |
|---|---|---|
| .NET SDK | 10.0.402 | `dotnet --list-sdks` |
| Runtimes | Microsoft.NETCore.App e Microsoft.AspNetCore.App 10.0.13 | `dotnet --list-runtimes` |
| Git | 2.54.0.windows.1; identidade global configurada | `git --version`, `git config` |
| Servidor PostgreSQL | 18, serviço `postgresql-x64-18`, automático, rodando, porta 5432 | `Get-Service`, `Get-NetTCPConnection` |
| Cliente `psql` | 18.6, **fora do PATH** (`C:\Program Files\PostgreSQL\18\bin\psql.exe`) | execução de `psql --version` pelo caminho completo |
| Docker | não instalado (não necessário) | `Get-Command docker` |
| GitHub CLI (`gh`) | não instalado (não necessário até agora) | `Get-Command gh` |

## Git e GitHub (confirmado)

- Remoto `origin`: https://github.com/Gab-Bit-bit/diario-saude.git — estava vazio antes do primeiro push (`git ls-remote`).
- Autenticação: Git Credential Manager (`credential.helper = manager`) com a conta `Gab-Bit-bit` guardada.
- Branch `main` acompanhando `origin/main`; hash local e remoto conferidos como iguais após o push.
- Configurações herdadas do nível *system*: `init.defaultBranch = master` (contornado com `git init -b main`)
  e `core.autocrlf = true` (repositório guarda LF; a pasta de trabalho usa CRLF).

## Arquivos do projeto

| Arquivo | Responsabilidade | Situação |
|---|---|---|
| `README.md` | Visão, princípios e objetivo didático | no commit `92cd6dc` |
| `.gitignore` | Modelo oficial `dotnet new gitignore` + regra para `.claude/settings.local.json` | no commit `92cd6dc` |
| `CLAUDE.md` | Instruções carregadas pelo Claude Code em toda sessão | no commit da etapa 3 |
| `GUIA_DE_ESTUDO.md` | Este registro de continuidade | no commit da etapa 3 |

## Decisões

- Usar o branch `main` (padrão do GitHub) em vez do `master` configurado no sistema.
- Gerar o `.gitignore` com a ferramenta oficial do SDK em vez de escrevê-lo à mão.
- Adicionar arquivos ao commit pelo nome, nunca com `git add .`; nunca usar force push.
- `CLAUDE.md` curto e sem `@imports`: ele é carregado em toda sessão e cada linha custa contexto.
  O guia é lido sob demanda no início da sessão.

## Conceitos estudados

- **SDK × runtime**: o SDK constrói (compilador, `dotnet new/build`, NuGet) e inclui um runtime; o runtime só executa.
- **Cliente × servidor PostgreSQL**: o servidor guarda os dados e executa SQL (serviço na porta 5432);
  clientes (`psql`, pgAdmin, nosso backend) se conectam a ele.
- **Git**: repositório (`.git/`), staging area, commit e hash, remoto, push, upstream (`-u`),
  fast-forward e por que evitar force push; níveis de configuração (*system*, *global*, *local*).
- **`.gitignore`**: artefatos gerados, arquivos pessoais e, principalmente, segredos ficam fora do histórico.

## Recursos do Claude Code utilizados

| Recurso | Para quê | Observação |
|---|---|---|
| Plan mode | Sessão inicial somente leitura | Regra aplicada pela ferramenta, não pelo prompt |
| Ferramenta PowerShell | Comandos de consulta, Git | Cada execução passa pelas permissões |
| Write / Read / Edit | Criar e alterar arquivos | `Edit` substitui um trecho exato e único |
| Grep | Buscar trechos sem carregar arquivos inteiros | Economiza contexto |
| WebFetch | Consultar a documentação oficial do CLAUDE.md | Página grande salva em arquivo; lida com Grep |
| Prefixo `!` | Você rodar um comando nesta sessão | O resultado entra no contexto |
| Hook `SessionStart` (observado) | Plugin "Ponytail" injeta instruções ao abrir a sessão | Ainda não examinado |
| `CLAUDE.md` | Orientações persistentes entre sessões | Contexto, não regra imposta |

## Pendências

- [ ] Confirmar, em uma nova sessão, que o `CLAUDE.md` é carregado (`/context` → *Memory files*).
- [ ] Senha do usuário `postgres` (definida na instalação) — necessária ao conectar; nunca versionar.
- [ ] Não verificado: visibilidade do repositório no GitHub (público/privado), editor de código,
      pgAdmin, `pg_hba.conf`/firewall, se o .NET 10 é LTS (documentação oficial), se o Claude Code
      ignora `settings.local.json` automaticamente.
- [ ] Depois, quando necessário: `dotnet-ef` (migrações), GitHub CLI (pull requests), ferramenta de testes E2E.
