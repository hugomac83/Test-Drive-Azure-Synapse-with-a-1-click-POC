---
name: avaliacao-impacto
description: Guia metodológico para desenhar, conduzir e revisar avaliações de impacto socioeconômico e ambiental — inclui EIA/RIMA, diagnóstico de populações em zonas de risco (ex. barragens, grandes empreendimentos), avaliação de programas públicos e sociais, desenho quase-experimental, definição de indicadores e checagem de validade das conclusões. Use sempre que o usuário mencionar avaliação de impacto, EIA/RIMA, licenciamento ambiental/ESG, diagnóstico de população afetada, área de influência de empreendimento, ou desenho de pesquisa para política pública — mesmo que não peça explicitamente por "metodologia".
---

# Avaliação de Impacto Socioeconômico e Ambiental

Skill para estruturar avaliações de impacto com rigor metodológico, cobrindo tanto avaliação de programas públicos/sociais quanto estudos de impacto ambiental (EIA/RIMA) e diagnósticos de populações afetadas por grandes empreendimentos.

## Quando usar cada trilha

- **Programas públicos e sociais** (educação, assistência social, transferência de renda, segurança pública) → trilha "Avaliação de Programa"
- **Empreendimentos e licenciamento** (hidrelétricas, mineração, infraestrutura) → trilha "EIA/RIMA e Diagnóstico de População Afetada"

As duas trilhas compartilham a base metodológica (desenho, indicadores, validade), mas divergem em enquadramento legal e público-alvo do relatório.

## Trilha 1 — Avaliação de Programa

### Passo 1: Definir a pergunta de avaliação
Distinga três tipos de pergunta, porque cada uma pede um desenho diferente:
- **Implementação**: o programa está sendo executado como planejado? (fidelidade, cobertura, dosagem)
- **Impacto/efetividade**: o programa causou a mudança observada? (exige contrafactual)
- **Eficiência**: o resultado justifica o custo? (custo-efetividade, custo-benefício)

Perguntar isso primeiro evita o erro mais comum: desenhar uma avaliação de impacto quando na verdade a pergunta do cliente é de implementação (ou vice-versa).

### Passo 2: Escolher o desenho e o contrafactual
Ordem de rigor (do mais forte ao mais fraco, e trade-off com viabilidade):
1. **RCT** (randomização) — raramente viável em política pública já em curso
2. **Quase-experimental**: diferenças-em-diferenças, descontinuidade de regressão (corte de elegibilidade), pareamento por escore de propensão (PSM)
3. **Antes-depois com grupo de comparação** — mais fraco, mas comum quando não há baseline randomizado
4. **Antes-depois simples** — só serve para descrever tendência, não para atribuir causalidade; sinalize isso explicitamente no relatório

Regra prática: se o programa tem critério de elegibilidade com corte numérico (nota de corte, renda, idade), verifique descontinuidade de regressão antes de qualquer outra coisa — costuma ser o desenho mais forte disponível sem precisar de randomização.

### Passo 3: Amostragem
- Defina a unidade de análise (indivíduo, família, escola, unidade administrativa)
- Calcule tamanho de amostra a partir de: efeito mínimo detectável, variância esperada, poder estatístico (0,8 é o padrão), nível de significância
- Para amostras em múltiplos estados/territórios, use amostragem estratificada (por região, porte, tipo de gestão) e documente os pesos amostrais

### Passo 4: Indicadores
Separe sempre:
- **Indicadores de processo/implementação** (leading): cobertura, tempo de resposta, adesão
- **Indicadores de resultado** (lagging): o que muda na vida da população-alvo
- **Indicadores de impacto**: atribuíveis ao programa via o desenho escolhido no Passo 2

Evite indicador "vaidade" — algo fácil de medir mas que não informa decisão.

### Passo 5: Checar ameaças à validade
Antes de apresentar conclusões, percorra este checklist:
- **Validade interna**: seleção, atrito diferencial entre grupos, regressão à média, história (evento externo concomitante)
- **Validade externa**: os resultados generalizam para outros territórios/públicos?
- **Viés de confundimento**: existe variável não observada correlacionada com tratamento e resultado?

Se qualquer item falhar, declare isso explicitamente no relatório como limitação — não omita.

## Trilha 2 — EIA/RIMA e Diagnóstico de População Afetada

### Passo 1: Delimitar áreas de influência
- **Área Diretamente Afetada (ADA)**: onde há intervenção física direta
- **Área de Influência Direta (AID)**: sofre efeitos diretos do empreendimento
- **Área de Influência Indireta (AII)**: efeitos indiretos/regionais

Cada uma pede um nível diferente de detalhamento no diagnóstico socioeconômico.

### Passo 2: Diagnóstico da população afetada
Estrutura mínima:
- Perfil sociodemográfico (idade, renda, ocupação, escolaridade)
- Vínculos territoriais (tempo de residência, dependência de recursos naturais locais, redes de sociabilidade)
- Grupos vulneráveis específicos (populações tradicionais, comunidades ribeirinhas, zonas de risco de rompimento de barragem)
- Mapeamento de ativos que serão impactados (moradia, atividade produtiva, patrimônio cultural)

### Passo 3: Classificar impactos
Para cada impacto identificado, registre: natureza (direto/indireto), fase (planejamento/obras/operação), magnitude, reversibilidade, duração (temporário/permanente) e abrangência (ADA/AID/AII).

### Passo 4: Medidas mitigadoras e compensatórias
Vincule cada impacto negativo relevante a uma medida concreta, com responsável e indicador de monitoramento — relatórios sem essa amarração são recorrentemente questionados por órgãos licenciadores.

## Saída esperada
Ao final de qualquer avaliação conduzida com este skill, produza:
1. Sumário executivo (1 página, linguagem para tomador de decisão não técnico)
2. Metodologia (desenho, amostra, fonte de dados)
3. Resultados por indicador
4. Limitações e ameaças à validade
5. Recomendações acionáveis

Se o usuário pedir para "estressar" ou testar o desenho antes de rodar, conduza uma bateria de perguntas críticas cobrindo os pontos dos Passos 2 e 5 (contrafactual, viés, validade externa) antes de prosseguir.
