# Schema JSON-LD para Artigos — Padrão Yoast SEO

O Yoast gera schema.org em JSON-LD automaticamente. Use este template para gerar schema otimizado.

## Template: BlogPosting

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "BlogPosting",
      "@id": "https://seusite.com/slug/#article",
      "headline": "Título do Artigo (até 110 chars)",
      "datePublished": "2025-01-15T10:00:00-03:00",
      "dateModified": "2025-01-20T14:30:00-03:00",
      "author": {"name": "Autor", "@id": "https://seusite.com/#/schema/person/ID"},
      "publisher": {"@id": "https://seusite.com/#organization"},
      "image": {"@id": "https://seusite.com/slug/#primaryimage"},
      "wordCount": 1500,
      "keywords": ["keyword1", "keyword2"],
      "inLanguage": "pt-BR",
      "mainEntityOfPage": {"@id": "https://seusite.com/slug/"}
    },
    {
      "@type": "WebPage",
      "@id": "https://seusite.com/slug/",
      "url": "https://seusite.com/slug/",
      "name": "Título SEO",
      "description": "Meta description aqui",
      "datePublished": "2025-01-15T10:00:00-03:00",
      "inLanguage": "pt-BR",
      "isPartOf": {"@id": "https://seusite.com/#website"},
      "breadcrumb": {"@id": "https://seusite.com/slug/#breadcrumb"}
    },
    {
      "@type": "ImageObject",
      "@id": "https://seusite.com/slug/#primaryimage",
      "url": "https://seusite.com/uploads/imagem.jpg",
      "width": 1200, "height": 675
    },
    {
      "@type": "BreadcrumbList",
      "@id": "https://seusite.com/slug/#breadcrumb",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://seusite.com/"},
        {"@type": "ListItem", "position": 2, "name": "Blog", "item": "https://seusite.com/blog/"},
        {"@type": "ListItem", "position": 3, "name": "Título do Artigo"}
      ]
    },
    {
      "@type": "Organization",
      "@id": "https://seusite.com/#organization",
      "name": "Nome da Org",
      "url": "https://seusite.com/",
      "logo": {"@type": "ImageObject", "url": "https://seusite.com/uploads/logo.png", "width": 500, "height": 500}
    }
  ]
}
```

## Campos obrigatórios

| Campo | Status | Notas |
|-------|--------|-------|
| `@type` | Obrigatório | `Article`, `BlogPosting`, ou `NewsArticle` |
| `headline` | Obrigatório | Até 110 caracteres |
| `datePublished` | Obrigatório | ISO 8601 com timezone |
| `author` | Obrigatório | Person ou Organization |
| `publisher` | Obrigatório | Organization |
| `image` | Recomendado | Mínimo 1200px largura, 16:9 |

## Validação

- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)
