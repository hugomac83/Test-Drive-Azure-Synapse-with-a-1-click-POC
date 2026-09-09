---
name: dashboards-bi
description: Workflow para desenhar KPIs e construir dashboards executivos em Power BI (DAX) e SQL, incluindo modelagem de dados para redes de múltiplas unidades. Use sempre que o usuário mencionar dashboard, Power BI, DAX, KPI executivo, modelagem de dados para BI, star schema, ou pedir para transformar uma base de dados em painel de decisão — mesmo que a palavra "dashboard" não apareça explicitamente (ex.: "preciso acompanhar isso por unidade e por mês").
---

# Dashboards Executivos: Power BI, DAX e SQL

Skill para ir da pergunta de negócio até o dashboard publicado, cobrindo definição de KPI, modelagem de dados e implementação técnica.

## Passo 1: Definir o KPI antes de abrir o Power BI
Erro mais comum: começar pela ferramenta antes de fechar a definição do indicador. Para cada KPI, feche por escrito:
- **Fórmula exata** (numerador/denominador, unidade)
- **Granularidade** (por unidade? por período? por dia/mês/ano?)
- **Meta ou benchmark** de comparação
- **Direção desejada** (subir é bom ou é ruim?)
- **Dono do indicador** (quem age quando ele sai da meta)

Sem isso fechado, qualquer modelo DAX construído em cima vai precisar ser refeito.

## Passo 2: Modelar os dados (star schema)
Para redes de múltiplas unidades, a modelagem canônica é **esquema estrela**:
- **Tabela fato**: uma linha por evento/transação (ex. atendimento, matrícula, ocorrência), com chaves estrangeiras para as dimensões e as métricas numéricas
- **Tabelas dimensão**: Unidade, Tempo (calendário), e quaisquer categorias de corte (região, tipo de programa, faixa etária)

Regras práticas:
- Sempre tenha uma tabela **Calendário** dedicada, marcada como tabela de datas no modelo — funções de time intelligence do DAX (YTD, MoM, YoY) dependem disso
- Evite floco de neve (snowflake) desnecessário — achata a performance e a legibilidade
- Relacionamentos devem ser 1-para-muitos partindo da dimensão para a fato; evite relações bidirecionais a menos que haja necessidade explícita de filtro cruzado

## Passo 3: Padrões de DAX mais usados
- **Medida básica de agregação**: `Total := SUM(Fato[Valor])`
- **Comparação temporal**:
  ```
  YoY % := 
  VAR Atual = [Total]
  VAR Anterior = CALCULATE([Total], SAMEPERIODLASTYEAR('Calendário'[Data]))
  RETURN DIVIDE(Atual - Anterior, Anterior)
  ```
- **% do total** (útil para ranking de unidades):
  ```
  % do Total := DIVIDE([Total], CALCULATE([Total], ALL(Unidade)))
  ```
- **Meta vs. Realizado**: mantenha a meta em uma tabela separada (não hardcoded na medida) para permitir simulação e atualização sem reescrever DAX
- Prefira `DIVIDE()` a `/` sempre — evita erro de divisão por zero sem precisar de `IFERROR`

## Passo 4: SQL por trás do dashboard
Ao extrair/preparar dados na origem antes de carregar no Power BI:
- Empurre agregações e filtros para o SQL sempre que possível — reduz volume de dados carregado e acelera o refresh
- Use CTEs nomeadas para deixar a lógica de negócio legível para quem for auditar depois
- Para séries temporais, gere a dimensão de calendário via `GENERATE_SERIES` (Postgres/BigQuery) ou tabela numérica auxiliar, não depende de haver dado em todo dia
- Documente joins que fazem duplicação intencional (ex. fan-out entre fato e dimensão multivalorada) — é a causa mais comum de KPI "errado" que na verdade é problema de grão

## Passo 5: Design do dashboard executivo
- Regra dos 5 segundos: quem abre o painel deve entender o status geral sem precisar interagir
- Hierarquia visual: KPI(s) principais no topo com meta/tendência ao lado, detalhamento e cortes abaixo
- Use cor com significado consistente (ex. vermelho = abaixo da meta) e nunca só cor — sempre com rótulo, para acessibilidade
- Limite a 5–7 elementos visuais por página; se precisar de mais, crie páginas de detalhamento navegáveis a partir do resumo

## Passo 6: Antes de publicar
Checklist de validação:
- [ ] Os totais do dashboard batem com uma soma manual/SQL direta na fonte?
- [ ] Os filtros de contexto (slicers) afetam todos os visuais esperados?
- [ ] A medida de comparação temporal funciona no primeiro e no último período do calendário (casos de borda)?
- [ ] Existe algum "buraco" de granularidade (unidade sem dado em algum mês aparece como zero ou como ausente — e isso é o comportamento certo)?

Se o usuário pedir ajuda para construir o dashboard como artefato interativo (não Power BI), use as ferramentas de visualização deste ambiente em vez de tentar simular Power BI em HTML.
