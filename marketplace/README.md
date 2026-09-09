# hugo-costa-data-toolkit

Marketplace de plugins para Claude Code com skills voltados a avaliação de impacto socioeconômico/ambiental, dashboards executivos de BI (Power BI/DAX/SQL), métodos de pesquisa social e demográfica, e diretrizes gerais de comportamento de codificação.

## Estrutura

```
.
├── .claude-plugin/
│   └── marketplace.json          # manifesto do marketplace
└── skills/
    ├── avaliacao-impacto/SKILL.md
    ├── dashboards-bi/SKILL.md
    ├── metodos-pesquisa/SKILL.md
    └── karpathy-guidelines/SKILL.md
```

Dois plugins compõem o marketplace:

- `avaliacao-e-dados-sociais` — agrupa os três skills de avaliação de impacto, BI e métodos de pesquisa.
- `andrej-karpathy-skills` — skill único (`karpathy-guidelines`) com diretrizes de comportamento de codificação (evitar suposições silenciosas, overengineering, mudanças fora do escopo), originalmente de [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills), licença MIT.

## Como publicar

1. Copie esta pasta para a raiz do seu repositório no GitHub (ou use este repositório inteiro, se for dedicado a isso).
2. Faça commit e push:
   ```bash
   git add .
   git commit -m "Adiciona marketplace de skills de avaliação de impacto e BI"
   git push
   ```

## Como instalar no Claude Code (você ou qualquer colega)

Dentro do Claude Code:

```
/plugin marketplace add <seu-usuario>/<seu-repo>
/plugin install avaliacao-e-dados-sociais@hugo-costa-data-toolkit
/plugin install andrej-karpathy-skills@hugo-costa-data-toolkit
```

Depois disso, os skills ficam disponíveis automaticamente sempre que a tarefa for relevante (avaliação de impacto, EIA/RIMA, dashboard/Power BI/SQL, desenho de pesquisa/amostragem, ou boas práticas de codificação).

## Como editar ou adicionar um skill

- Para editar um skill existente, abra o `SKILL.md` correspondente em `skills/<nome>/` e edite o corpo em Markdown; a seção YAML no topo (`name`, `description`) controla quando o skill é acionado — mantenha a descrição "convidativa" e específica, listando gatilhos concretos.
- Para adicionar um novo skill: crie `skills/<novo-nome>/SKILL.md` e adicione o caminho `./skills/<novo-nome>` ao array `skills` do plugin em `.claude-plugin/marketplace.json`.
- Para separar em um segundo plugin (ex. se um dia quiser vender/distribuir só a parte de BI), duplique o bloco em `plugins` no `marketplace.json` com um novo `name` e sua própria lista de `skills`.
