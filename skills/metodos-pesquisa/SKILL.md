---
name: metodos-pesquisa
description: Guia de métodos quantitativos e qualitativos de pesquisa social e demográfica — desenho amostral, instrumentos de survey, análise longitudinal e de coorte, métodos demográficos (tábuas de vida, projeções populacionais) e escolha de teste estatístico. Use sempre que o usuário mencionar amostragem, survey, questionário, coorte, painel longitudinal, método demográfico, projeção populacional, ou pedir ajuda para desenhar um instrumento ou escolher um teste estatístico — mesmo em conversas técnicas de estatística aplicada.
---

# Métodos de Pesquisa Social e Demográfica

Skill de apoio metodológico para desenho amostral, instrumentos de coleta, análise longitudinal/coorte, métodos demográficos e seleção de testes estatísticos.

## 1. Desenho amostral

Decisão em cascata:
1. **Universo e unidade de análise**: pessoa, domicílio, unidade administrativa?
2. **Tipo de amostragem**:
   - Aleatória simples — só viável com cadastro completo do universo
   - Estratificada — quando há subgrupos com variância distinta ou que precisam de representatividade garantida (ex. por região, porte de unidade)
   - Por conglomerado (cluster) — quando o cadastro completo não existe mas há agrupamentos naturais (ex. escolas, depois alunos dentro delas); atenção ao efeito de desenho (design effect), que infla o erro padrão
   - Por cotas — não probabilística, use só quando amostragem probabilística for inviável, e declare a limitação
3. **Tamanho da amostra**: calcule a partir de nível de confiança, margem de erro tolerada e variância esperada (ou p=0,5 como cenário conservador para proporções). Para desenho por conglomerado, multiplique o n calculado pelo efeito de desenho estimado.
4. **Pesos amostrais**: se houver estratos com probabilidades de seleção diferentes, todo dado agregado precisa ser ponderado — sinalize isso antes de qualquer análise descritiva.

## 2. Instrumentos de survey

- **Ordem das perguntas**: geral → específico; sensíveis (renda, raça, violência) sempre por último, nunca na abertura
- **Escalas**: prefira número ímpar de pontos (permite ponto neutro) exceto quando o objetivo é forçar posicionamento; mantenha a mesma direção da escala em todo o instrumento (não alterne "concordo" e "discordo" como âncora positiva)
- **Piloto**: sempre rode um pré-teste com 15–30 respondentes antes do campo, revisando tempo de resposta e perguntas mal compreendidas
- **Vieses de resposta a mitigar**: desejabilidade social (pergunte de forma indireta ou use lista de itens quando o tema for sensível), aquiescência (varie a valência das afirmações), ordem (rotacione blocos quando possível)

## 3. Análise longitudinal e de coorte

- **Painel vs. coortes repetidas**: painel segue os mesmos indivíduos (permite ver mudança individual, mas sofre atrito/attrition); coortes repetidas amostram grupos novos a cada onda (não sofre atrito, mas não isola mudança individual)
- **Atrito (attrition)**: sempre compare o perfil de quem saiu do painel com quem ficou — atrito não aleatório vira viés de seleção na análise
- **Efeitos idade-período-coorte**: ao interpretar mudança ao longo do tempo, distinga o que é efeito de envelhecimento (idade), efeito de momento histórico (período) e efeito de geração (coorte) — os três são colineares por construção, então declare qual suposição de identificação está sendo usada
- **Métodos comuns**: modelos de efeitos fixos/aleatórios para dados em painel, modelos de crescimento latente, análise de sobrevivência quando o desfecho é "tempo até evento" (ex. tempo até evasão)

## 4. Métodos demográficos

- **Tábua de vida (life table)**: use para estimar esperança de vida, probabilidade de sobrevivência por idade, ou — adaptado — "tempo até evento" em contextos não estritamente de mortalidade (ex. tempo até saída de um programa)
- **Projeção populacional**: método de componentes (coorte-componente) é o padrão — projeta separadamente natalidade, mortalidade e migração por coorte etária; mais robusto que extrapolação de tendência simples quando o horizonte é maior que poucos anos
- **Padronização de taxas**: ao comparar taxas entre territórios com estrutura etária distinta (ex. taxa de mortalidade entre municípios), sempre padronize por idade (direta ou indireta) antes de comparar — taxa bruta sem padronização é um erro comum e materialmente distorce comparações

## 5. Escolha de teste estatístico

Fluxo rápido de decisão:
- **Comparar médias entre 2 grupos**: teste t (dados aproximadamente normais, variâncias) ou Mann-Whitney (não paramétrico)
- **Comparar médias entre 3+ grupos**: ANOVA (paramétrico) ou Kruskal-Wallis (não paramétrico)
- **Associação entre categóricas**: qui-quadrado (amostra grande) ou teste exato de Fisher (amostra pequena/células esparsas)
- **Relação entre variável contínua e binária**: regressão logística
- **Efeito causal com desenho quase-experimental**: ver skill `avaliacao-impacto` para desenho (DiD, RDD, PSM) — aqui trate apenas da mecânica do teste
- Sempre reporte tamanho de efeito junto com significância — p-valor sozinho não informa relevância prática, especialmente em amostras grandes onde tudo tende a "dar significativo"

## Saída esperada
Ao aplicar este skill, produza sempre: (1) a decisão metodológica tomada, (2) a alternativa descartada e por quê, e (3) a limitação que essa escolha implica — isso é o que diferencia um relatório metodologicamente defensável de um que só reporta números.
