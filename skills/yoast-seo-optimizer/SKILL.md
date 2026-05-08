---
name: yoast-seo-optimizer
description: Otimiza artigos de blog e páginas de sites seguindo as diretrizes de análise de conteúdo do Yoast SEO (análise SEO + análise de legibilidade). Usa a mesma lógica do plugin Yoast SEO para WordPress para avaliar e melhorar textos, meta tags, schema markup, slug, título SEO, meta description, densidade de keyphrase, legibilidade, links internos/externos e estrutura de headings. Use esta skill sempre que o usuário pedir para otimizar SEO de um artigo, revisar conteúdo para blog, melhorar pontuação do Yoast, preparar texto para publicação WordPress, verificar legibilidade, otimizar meta tags, gerar schema.org para artigo, ou mencionar 'Yoast', 'SEO do artigo', 'verde no Yoast', 'pontuação SEO', 'readability', 'keyphrase', 'meta description', 'focus keyword', 'SEO title', ou pedir análise de conteúdo antes de publicar. Também use quando o usuário mencionar campos como _yoast_wpseo_title, _yoast_wpseo_metadesc, _yoast_wpseo_focuskw, ou quiser atualizar metadados Yoast via REST API.
---

# Yoast SEO Optimizer

Skill para otimização de artigos de blog e páginas web seguindo as diretrizes de análise de conteúdo do Yoast SEO — o plugin de SEO mais popular para WordPress (~12M+ instalações ativas).

O Yoast avalia conteúdo em duas dimensões: **Análise de SEO** (otimização para buscadores) e **Análise de Legibilidade** (facilidade de leitura para humanos). Esta skill replica essa lógica para que o conteúdo alcance "verde" (boa prática atendida) em todas as verificações antes da publicação.

## Quando usar

- Otimizar ou revisar artigos de blog antes de publicar
- Atingir pontuação verde no Yoast SEO
- Gerar ou melhorar meta title, meta description, slug
- Verificar densidade de keyphrase e distribuição
- Avaliar legibilidade (frases curtas, voz ativa, palavras de transição)
- Gerar JSON-LD / schema.org para artigos
- Atualizar metadados Yoast via WordPress REST API
- Adaptar conteúdo para pt-BR ou en-US seguindo os critérios Yoast

## Workflow de otimização

### Passo 1: Coletar informações do usuário

Pergunte ao usuário (se não foi fornecido):

1. **Keyphrase foco** — A palavra-chave ou frase principal que o artigo deve ranquear
2. **Texto do artigo** — O conteúdo completo (pode ser Markdown, HTML ou texto puro)
3. **Idioma do artigo** — pt-BR ou en-US (afeta palavras de transição e legibilidade)
4. **URL/slug pretendido** — Para verificar se a keyphrase está no slug
5. **Meta title atual** (se existir) — Para avaliar e melhorar
6. **Meta description atual** (se existir) — Para avaliar e melhorar

### Passo 2: Executar análise de SEO

Avaliar cada item da checklist abaixo e classificar como 🟢 (bom), 🟠 (melhorar) ou 🔴 (ação necessária). Consulte `references/seo-analysis-checklist.md` para os limiares exatos de cada verificação.

**Checklist de análise SEO:**

1. **Keyphrase no título SEO** — A keyphrase deve aparecer no início do título SEO
2. **Keyphrase na meta description** — A keyphrase deve aparecer na meta description
3. **Keyphrase no slug/URL** — A keyphrase (ou parte dela) deve estar no slug
4. **Keyphrase na introdução** — A keyphrase deve aparecer no primeiro parágrafo
5. **Densidade da keyphrase** — Entre 0,5% e 3% do total de palavras
6. **Keyphrase em subheadings** — A keyphrase deve aparecer em pelo menos um H2 ou H3
7. **Keyphrase em alt text** — Pelo menos uma imagem com a keyphrase no atributo alt
8. **Comprimento do texto** — Mínimo de 300 palavras (ideal: 900+ para artigos cornerstone)
9. **Links internos** — Pelo menos um link para outra página do mesmo site
10. **Links externos** — Pelo menos um link para um site relevante e confiável
11. **Comprimento do título SEO** — Entre 50-60 caracteres (máx. 600px visíveis no Google)
12. **Comprimento da meta description** — Entre 120-155 caracteres
13. **Keyphrase já usada antes** — Verificar se a mesma keyphrase não foi usada em outro artigo
14. **Distribuição da keyphrase** — A keyphrase deve estar distribuída por todo o texto, não concentrada

### Passo 3: Executar análise de legibilidade

**INSTRUÇÃO CRÍTICA (COMO EMULAR A API DO YOAST):** O Yoast usa parsers matemáticos rigorosos, não estimativas. Para garantir que seus resultados batam com a API, você deve **contar matematicamente**:
- O número total de palavras do texto.
- O número total de frases do texto (contando pontos finais, exclamações e interrogações).
- O número exato de frases que caem em cada regra (ex: frases com mais de 20 palavras, frases com voz passiva).
Calcule a porcentagem exata usando: `(Frases com a ocorrência / Total de frases) * 100`.

**Checklist de legibilidade:**

1. **Comprimento das frases** — Máx. 25% das frases com mais de 20 palavras (CONTE o número de palavras por frase).
2. **Comprimento dos parágrafos** — Máx. 150 palavras por parágrafo (CONTE as palavras dos parágrafos mais longos).
3. **Subheadings** — A cada ~300 palavras de texto corrido, deve haver um subheading.
4. **Voz passiva** — Máx. 10% das frases em voz passiva (Veja as regras de verbo + particípio na referência e CONTE EXATAMENTE as ocorrências).
5. **Palavras de transição** — Pelo menos 30% das frases devem conter palavras de transição.
6. **Frases consecutivas** — Não iniciar 3+ frases seguidas com a mesma palavra.
7. **Flesch Reading Ease** — Pontuação adequada ao idioma (ver referência).

### Passo 4: Gerar relatório

Apresente o relatório em formato de tabela com:

```
## 📊 Relatório de Análise Yoast SEO

### Análise SEO (Keyphrase: "[keyphrase]")
| # | Verificação | Status | Detalhe |
|---|-------------|--------|---------|
| 1 | Keyphrase no título SEO | 🟢/🟠/🔴 | ... |
| ... | ... | ... | ... |

### Análise de Legibilidade
| # | Verificação | Status | Detalhe |
|---|-------------|--------|---------|
| 1 | Comprimento das frases | 🟢/🟠/🔴 | X% acima de 20 palavras |
| ... | ... | ... | ... |

### Pontuação Geral
- SEO: X/14 verificações verdes
- Legibilidade: X/7 verificações verdes
- Status: 🟢 Pronto para publicar / 🟠 Melhorias recomendadas / 🔴 Necessita atenção
```

### Passo 5: Sugerir melhorias

Para cada item 🟠 ou 🔴, forneça uma sugestão de melhoria **concreta e acionável** — não apenas "melhore isso", mas sim "reescreva o primeiro parágrafo para incluir a keyphrase 'X' na primeira frase, por exemplo: '...'" .

### Passo 6: Gerar metadados otimizados

Se solicitado ou se os metadados precisarem de melhoria, gere:

1. **SEO Title** — Incluindo keyphrase, até 60 caracteres, atrativo para clique
2. **Meta Description** — Incluindo keyphrase, 120-155 caracteres, com call-to-action
3. **Slug sugerido** — Curto, com keyphrase, sem stopwords
4. **Schema JSON-LD** — Estrutura Article para o conteúdo (ver `references/schema-article.md`)

### Passo 7 (Opcional): Atualizar via WordPress REST API

Se o usuário quiser enviar as otimizações programaticamente, consulte `references/wordpress-rest-api.md` para o código de integração.

## Regras importantes

- O objetivo é conteúdo de qualidade para humanos — a pontuação Yoast é um guia, não uma regra rígida. Priorize sempre a naturalidade do texto.
- Nunca force a keyphrase de forma artificial. Uma leitura fluida vale mais que uma densidade perfeita.
- Adapte as verificações ao idioma — pt-BR tem palavras de transição diferentes de en-US.
- A meta description não é fator de ranking direto, mas impacta CTR (taxa de clique). Torne-a persuasiva.
- Schema.org aumenta chances de rich snippets no Google — sempre inclua quando aplicável.

## Arquivos de referência

Consulte estes arquivos para detalhes técnicos aprofundados:

- `references/seo-analysis-checklist.md` — Limiares exatos de cada verificação SEO e legibilidade, com exemplos
- `references/schema-article.md` — Template de JSON-LD Article/BlogPosting para artigos
- `references/wordpress-rest-api.md` — Como ler e atualizar metadados Yoast via WP REST API
- `references/transition-words-pt-br.md` — Lista de palavras de transição em português do Brasil
