# Como contribuir nos repositórios da Nebula Systems

Este arquivo vale para todos os repositórios da organização. Ele vive no
repositório `.github`, que o GitHub usa como padrão para os demais — um
repositório só precisa do seu próprio `CONTRIBUTING.md` se quiser
sobrescrever o que está aqui.

## Mensagens de commit

Usamos [Conventional Commits](https://www.conventionalcommits.org/). O
formato é:

```
<tipo>(<escopo opcional>): <descrição no imperativo>

<corpo opcional, explicando o porquê>
```

| Tipo | Quando usar |
|---|---|
| `feat` | Funcionalidade nova |
| `fix` | Correção de defeito |
| `docs` | Só documentação |
| `ci` | Pipeline, workflows, automação de build |
| `chore` | Manutenção sem efeito em produção (dependências, limpeza) |
| `refactor` | Mudança de código sem alterar comportamento |
| `test` | Testes |
| `perf` | Melhoria de desempenho |

**Breaking change:** acrescente `!` antes dos dois-pontos — `feat!:` ou
`feat(api)!:` — e explique no corpo o que quebra e como migrar.

Alguns exemplos reais do histórico:

```
fix: make OIDC provider ARN dynamic and sync repo org in trust policies
ci: run plan on pull requests with a read-only role
chore(ui): adjust spacing on hero section
```

### Por que isso não é só estilo

No repositório do site, o `semantic-release` **lê estas mensagens** para
decidir a versão e gerar o release automaticamente: `fix` vira patch,
`feat` vira minor, `!` vira major. Uma mensagem fora do padrão não gera
release — ela é simplesmente ignorada, em silêncio.

## Mensagem do corpo

A descrição responde *o quê*. O corpo responde *por quê*. Prefira
registrar a restrição, o incidente ou a decisão que motivou a mudança —
o diff já mostra o que foi alterado, e é o porquê que se perde com o
tempo.

Não inclua atribuição a ferramentas de IA em commits ou descrições de PR.

## Pull requests

- O template de PR abre preenchido. Responda as seções; apague as que
  não se aplicarem, em vez de deixar em branco.
- **O título da PR segue a mesma convenção dos commits.** Em merge por
  squash, o título da PR vira a mensagem do commit na `main` — ou seja,
  é ele que o `semantic-release` vai ler. Há um check no CI validando
  isso.
- Em mudança de infraestrutura, cole o resumo do `terraform plan` na PR.
  O CI roda `plan` automaticamente em toda PR, com uma role de somente
  leitura; o `apply` só acontece no merge para a `main`.

## Branches

Nomeie pelo tipo do trabalho, no mesmo vocabulário dos commits:

```
feat/migrate-to-dedicated-account
chore/ci-guardrails
fix/cloudfront-origin-access
```
