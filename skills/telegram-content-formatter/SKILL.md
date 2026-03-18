---
name: telegram-content-formatter
description: Formata textos e strings para HTML compatível com o Telegram conforme especificado em https://core.telegram.org/bots/api#html-style. Use sempre que o usuário pedir para formatar mensagens, converter Markdown para HTML do Telegram, preparar strings para envio via Bot API, ou garantir que caracteres especiais sejam escapados para evitar erros de parsing no Telegram.
---

# Telegram Content Formatter

Este skill orienta a formatação de mensagens de texto em HTML para uso nas APIs do Telegram. O Telegram suporta apenas um subconjunto limitado de tags HTML.

## Diretrizes de Formatação

### 1. Escapamento Obrigatório
Todos os caracteres `<`, `>`, e `&` que NÃO fazem parte de uma tag HTML suportada devem ser substituídos pelas suas respectivas entidades:
- `<` &rarr; `&lt;`
- `>` &rarr; `&gt;`
- `&` &rarr; `&amp;`

Se houver aspas dentro de um valor de atributo (como em um URL), use `&quot;`.

### 2. Tags Suportadas

| Estilo | Tags Aceitas | Exemplo |
| :--- | :--- | :--- |
| **Negrito** | `<b>`, `<strong>` | `<b>texto</b>` |
| *Itálico* | `<i>`, `<em>` | `<i>texto</i>` |
| <u>Sublinhado</u> | `<u>` | `<u>texto</u>` |
| <s>Riscado</s> | `<s>`, `<strike>`, `<del>` | `<s>texto</s>` |
| Spoiler | `<tg-spoiler>` | `<tg-spoiler>texto</tg-spoiler>` |
| Link | `<a href="URL">` | `<a href="https://example.com">texto</a>` |
| Menção (ID) | `<a href="tg://user?id=ID">` | `<a href="tg://user?id=12345678">Nome</a>` |
| Código Inline | `<code>` | `<code>código</code>` |
| Bloco de Código | `<pre>` | `<pre>bloco</pre>` |
| Bloco (Linguagem) | `<pre language="python">` | `<pre language="python">print("Hi")</pre>` |
| Citação | `<blockquote>` | `<blockquote>citação</blockquote>` |

### 3. Regras de Estrutura

- **Quebras de Linha**: Use apenas `\n`. O Telegram não reconhece `<br>`.
- **Listas**: Não existem tags `<ul>`, `<ol>` ou `<li>`. Formate listas manualmente usando hífens, números e quebras de linha.
- **Aninhamento**: Estilos básicos (`b`, `i`, `u`, `s`, `tg-spoiler`) podem ser aninhados entre si e dentro de `<a>` e `<blockquote>`. Eles NÃO podem ser usados dentro de `<code>` ou `<pre>`.
- **Entidades Numéricas**: Todas as entidades HTML numéricas são suportadas.

## Exemplos de Conversão

### Markdown para Telegram HTML
**Entrada:**
```markdown
Olá **Mundo**!
- Item 1
- Item 2 `v1.0`
[link](https://t.me)
```
**Saída:**
```html
Olá <b>Mundo</b>!
- Item 1
- Item 2 <code>v1.0</code>
<a href="https://t.me">link</a>
```

### Lidando com Caracteres Especiais
**Entrada:** `A > B & C < D`
**Saída:** `A &gt; B &amp; C &lt; D`

### Menção de Usuário
**Entrada:** Mencionar Gabriel com ID 12345
**Saída:** `<a href="tg://user?id=12345">Gabriel</a>`

## Boas Práticas
- Sempre valide se os links começam com `http://`, `https://` ou esquemas internos como `tg://`.
- Para blocos de código extensos, prefira sempre usar `<pre>` com o atributo `language` quando a linguagem for conhecida para garantir syntax highlighting.
- Ao converter tabelas, prefira usar o bloco `<pre>` para manter o alinhamento monoespaçado, já que tabelas HTML não são suportadas.
