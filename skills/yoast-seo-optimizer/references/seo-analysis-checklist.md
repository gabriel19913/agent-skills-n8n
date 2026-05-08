# Checklist de Análise SEO e Legibilidade — Limiares do Yoast

Este arquivo detalha cada verificação com os limiares exatos usados pelo Yoast SEO para classificar itens como 🟢 (bom), 🟠 (melhorar) ou 🔴 (ação necessária).

---

## Análise SEO

### 1. Keyphrase no título SEO (SEO Title)

| Status | Condição |
|--------|----------|
| 🟢 Bom | Keyphrase aparece no início do título SEO |
| 🟠 OK | Keyphrase aparece no título, mas não no início |
| 🔴 Ruim | Keyphrase não aparece no título SEO |

**Detalhes:** O Yoast usa correspondência de formas (stemming) — variações da keyphrase contam. O título deve ter entre 50-60 caracteres. O Google exibe ~600px de largura, o que equivale a aproximadamente 50-60 caracteres dependendo da fonte.

**Exemplo:**
- Keyphrase: "apostas esportivas online"
- 🟢 "Apostas Esportivas Online: Guia Completo 2025"
- 🟠 "Guia Completo sobre Apostas Esportivas Online"
- 🔴 "Como Ganhar Dinheiro com Jogos na Internet"

### 2. Keyphrase na meta description

| Status | Condição |
|--------|----------|
| 🟢 Bom | Keyphrase aparece pelo menos uma vez na meta description |
| 🔴 Ruim | Keyphrase não aparece na meta description |

**Detalhes:** A meta description deve ter entre 120-155 caracteres. Abaixo de 120, o Google pode substituí-la automaticamente. Acima de 155-160, será cortada nos resultados.

### 3. Keyphrase no slug/URL

| Status | Condição |
|--------|----------|
| 🟢 Bom | A keyphrase (ou parte significativa) está no slug |
| 🔴 Ruim | A keyphrase não aparece no slug |

**Boas práticas para slug:**
- Usar hifens como separadores
- Remover stopwords (de, a, o, para, em, que, com, etc.)
- Manter curto (3-5 palavras)
- Usar apenas letras minúsculas e números

**Exemplo:**
- Keyphrase: "melhores sites de apostas"
- 🟢 `/melhores-sites-apostas/`
- 🔴 `/artigo-sobre-como-encontrar-os-melhores-sites-para-apostar-online-no-brasil/`

### 4. Keyphrase na introdução

| Status | Condição |
|--------|----------|
| 🟢 Bom | Keyphrase aparece no primeiro parágrafo (primeiras ~100 palavras) |
| 🔴 Ruim | Keyphrase não aparece na introdução |

### 5. Densidade da keyphrase

| Status | Condição |
|--------|----------|
| 🟢 Bom | Densidade entre 0,5% e 3,0% |
| 🟠 Próximo | Densidade entre 0,3% e 0,5%, ou entre 3,0% e 3,5% |
| 🔴 Ruim | Densidade abaixo de 0,3% ou acima de 3,5% |

**Cálculo:** `(nº ocorrências da keyphrase / nº total de palavras) × 100`

Para keyphrases compostas (ex: "apostas esportivas"), contar ocorrências exatas e variações próximas (plural, singular, com/sem acento).

### 6. Keyphrase em subheadings (H2, H3)

| Status | Condição |
|--------|----------|
| 🟢 Bom | Keyphrase aparece em pelo menos 1 subheading H2/H3 |
| 🟠 Próximo | Keyphrase aparece em mais de 75% dos subheadings (sobreuso) |
| 🔴 Ruim | Keyphrase não aparece em nenhum subheading |

### 7. Keyphrase em alt text de imagens

| Status | Condição |
|--------|----------|
| 🟢 Bom | Keyphrase aparece no alt text de pelo menos 1 imagem |
| 🟠 Próximo | Mais de 75% das imagens têm a keyphrase no alt text (sobreuso) |
| 🔴 Ruim | Nenhuma imagem tem a keyphrase no alt text |

### 8. Comprimento do texto

| Status | Condição |
|--------|----------|
| 🟢 Bom | ≥ 300 palavras para conteúdo regular; ≥ 900 para cornerstone |
| 🟠 Próximo | 200-299 palavras |
| 🔴 Ruim | < 200 palavras |

### 9. Links internos

| Status | Condição |
|--------|----------|
| 🟢 Bom | ≥ 1 link interno (para outra página do mesmo domínio) |
| 🔴 Ruim | Nenhum link interno |

**Por que importa:** Links internos distribuem "link juice" e ajudam o Google a entender a estrutura do site.

### 10. Links externos (outbound)

| Status | Condição |
|--------|----------|
| 🟢 Bom | ≥ 1 link externo para domínio relevante e confiável |
| 🔴 Ruim | Nenhum link externo |

### 11. Comprimento do título SEO

| Status | Condição |
|--------|----------|
| 🟢 Bom | Entre 50 e 60 caracteres |
| 🟠 Próximo | Entre 40-49 ou 61-65 caracteres |
| 🔴 Ruim | < 40 ou > 65 caracteres |

### 12. Comprimento da meta description

| Status | Condição |
|--------|----------|
| 🟢 Bom | Entre 120 e 155 caracteres |
| 🟠 Próximo | Entre 100-119 ou 156-160 caracteres |
| 🔴 Ruim | < 100 ou > 160 caracteres |

### 13. Uso anterior da keyphrase

| Status | Condição |
|--------|----------|
| 🟢 Bom | Keyphrase não foi usada como foco em outro artigo publicado |
| 🔴 Ruim | Keyphrase já é a keyphrase foco de outro artigo (canibalização) |

**Nota:** Quando não é possível verificar o histórico do site, avisar o usuário para conferir no painel do Yoast.

### 14. Distribuição da keyphrase (Premium)

| Status | Condição |
|--------|----------|
| 🟢 Bom | Keyphrase distribuída uniformemente pelo texto |
| 🟠 Próximo | Algumas seções longas sem menção da keyphrase |
| 🔴 Ruim | Keyphrase concentrada em apenas uma parte do texto |

**Avaliação:** Dividir o texto em quartos (25% cada). A keyphrase deve aparecer em pelo menos 3 dos 4 quartos.

---

## Análise de Legibilidade

### 1. Comprimento das frases

| Status | Condição |
|--------|----------|
| 🟢 Bom | ≤ 25% das frases com mais de 20 palavras |
| 🟠 Próximo | 25-30% das frases com mais de 20 palavras |
| 🔴 Ruim | > 30% das frases com mais de 20 palavras |

### 2. Comprimento dos parágrafos

| Status | Condição |
|--------|----------|
| 🟢 Bom | Todos os parágrafos com ≤ 150 palavras |
| 🟠 Próximo | 1-2 parágrafos com 150-200 palavras |
| 🔴 Ruim | Parágrafos com > 200 palavras |

### 3. Distribuição de subheadings

| Status | Condição |
|--------|----------|
| 🟢 Bom | Não há blocos de texto > 300 palavras sem subheading |
| 🟠 Próximo | 1 bloco de 300-350 palavras sem subheading |
| 🔴 Ruim | Blocos > 350 palavras sem subheading |

### 4. Uso de voz passiva

| Status | Condição |
|--------|----------|
| 🟢 Bom | ≤ 10% das frases em voz passiva |
| 🟠 Próximo | 10-15% em voz passiva |
| 🔴 Ruim | > 15% em voz passiva |

**INSTRUÇÃO CRÍTICA PARA A IA:** O Yoast usa um parser NLP matemático rigoroso. Para emular isso corretamente, você **deve**:
1. Contar exatamente o número total de frases no texto (delimitadas por `.`, `!`, `?`).
2. Contar exatamente o número de frases que contêm a estrutura de voz passiva.
3. Calcular a porcentagem exata: `(Frases com voz passiva / Total de frases) * 100`.

**Indicadores exatos de voz passiva em pt-BR:**
A estrutura é: verbo auxiliar (`ser`, `estar`, `ficar`) + verbo principal no particípio passado (`-ado`, `-ada`, `-ido`, `-ida`, bem como irregulares como `feito`, `dito`, `visto`, `escrito`).
- **Verbo Ser:** `é`, `foi`, `será`, `sendo`, `sido`, `são`, `foram`, `serão`, `ser`, `seja` + particípio (ex: "é feito", "foi desenhado", "são distribuídas", "serem reconhecidos").
- **Verbo Estar:** `está`, `estava`, `esteve`, `estão`, `estiveram`, `estar`, `esteja` + particípio (ex: "está provado", "estão incluídos", "estão abertas").
- **Verbo Ficar:** `fica`, `ficou`, `ficam`, `ficarão`, `ficar`, `fique` + particípio (ex: "ficou decidido").

**Ação exigida:** Se a porcentagem calculada passar de 10% (ex: 11.7%), reescreva agressivamente as frases para a voz ativa convertendo o sujeito paciente em objeto direto, até que a conta caia para menos de 10%.

### 5. Palavras de transição

| Status | Condição |
|--------|----------|
| 🟢 Bom | ≥ 30% das frases contêm palavras de transição |
| 🟠 Próximo | 20-29% |
| 🔴 Ruim | < 20% |

Consulte `transition-words-pt-br.md` para a lista completa de palavras de transição em português.

### 6. Frases consecutivas com mesma palavra inicial

| Status | Condição |
|--------|----------|
| 🟢 Bom | Nenhuma sequência de 3+ frases começando com a mesma palavra |
| 🔴 Ruim | 3 ou mais frases seguidas começam com a mesma palavra |

### 7. Flesch Reading Ease

**Para textos em inglês (en-US):**

| Status | Pontuação |
|--------|-----------|
| 🟢 Bom | ≥ 60 (fácil de ler) |
| 🟠 OK | 30-59 (moderadamente difícil) |
| 🔴 Ruim | < 30 (muito difícil) |

**Para textos em português (pt-BR):**

O Yoast usa uma adaptação da fórmula Flesch para português:
```
Flesch-PT = 248.835 - (1.015 × ASL) - (84.6 × ASW)
```
Onde ASL = comprimento médio da frase (em palavras) e ASW = nº médio de sílabas por palavra.

| Status | Pontuação |
|--------|-----------|
| 🟢 Bom | ≥ 50 |
| 🟠 OK | 25-49 |
| 🔴 Ruim | < 25 |

**Nota:** Textos técnicos naturalmente terão pontuações mais baixas. Use bom senso — o objetivo é clareza, não simplificação forçada.
