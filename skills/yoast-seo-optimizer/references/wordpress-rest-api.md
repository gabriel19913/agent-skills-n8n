# Integração WordPress REST API — Metadados Yoast SEO

## Visão geral

A REST API do Yoast SEO é **somente leitura** (`GET`). Para **atualizar** metadados, você precisa escrever nos campos de post meta do WordPress (`_yoast_wpseo_*`) via WP REST API padrão.

## Leitura: Yoast REST API

### Método 1: Via WP REST API nativa

Os campos `yoast_head` e `yoast_head_json` são adicionados automaticamente às respostas:

```
GET /wp-json/wp/v2/posts/<id>
GET /wp-json/wp/v2/posts?slug=meu-artigo
```

Resposta inclui:
- `yoast_head` — HTML completo para o `<head>` (meta tags + schema)
- `yoast_head_json` — Dados raw em JSON (title, description, robots, og_*, twitter_*, schema)

### Método 2: Endpoint dedicado do Yoast

```
GET /wp-json/yoast/v1/get_head?url=https://seusite.com/meu-artigo/
```

Retorna `{ html, json, status }`.

## Escrita: Atualizar metadados via WP REST API

### Passo 1: Registrar campos meta para REST

Adicione ao `functions.php` ou um plugin customizado:

```php
add_action('init', 'register_yoast_meta_rest');
function register_yoast_meta_rest() {
    $fields = [
        '_yoast_wpseo_title',
        '_yoast_wpseo_metadesc',
        '_yoast_wpseo_focuskw',
        '_yoast_wpseo_canonical',
        '_yoast_wpseo_opengraph-title',
        '_yoast_wpseo_opengraph-description',
        '_yoast_wpseo_twitter-title',
        '_yoast_wpseo_twitter-description',
    ];

    foreach ($fields as $key) {
        register_post_meta('post', $key, [
            'show_in_rest' => true,
            'single'       => true,
            'type'         => 'string',
            'auth_callback' => function() {
                return current_user_can('edit_posts');
            }
        ]);
    }
}
```

### Passo 2: Atualizar via REST

```bash
curl -X POST "https://seusite.com/wp-json/wp/v2/posts/123" \
  -H "Authorization: Basic BASE64_USER:APP_PASSWORD" \
  -H "Content-Type: application/json" \
  -d '{
    "meta": {
      "_yoast_wpseo_title": "Novo Título SEO %%sep%% %%sitename%%",
      "_yoast_wpseo_metadesc": "Nova meta description otimizada",
      "_yoast_wpseo_focuskw": "keyphrase foco"
    }
  }'
```

### Variáveis de template do Yoast

O Yoast suporta variáveis nos campos de título:

| Variável | Descrição |
|----------|-----------|
| `%%title%%` | Título do post |
| `%%sitename%%` | Nome do site |
| `%%sep%%` | Separador configurado no Yoast |
| `%%primary_category%%` | Categoria principal |
| `%%excerpt%%` | Resumo do post |
| `%%date%%` | Data de publicação |

### Campos meta disponíveis

| Campo | Função |
|-------|--------|
| `_yoast_wpseo_title` | Título SEO customizado |
| `_yoast_wpseo_metadesc` | Meta description |
| `_yoast_wpseo_focuskw` | Keyphrase foco |
| `_yoast_wpseo_canonical` | URL canônica |
| `_yoast_wpseo_opengraph-title` | Título para Open Graph |
| `_yoast_wpseo_opengraph-description` | Descrição OG |
| `_yoast_wpseo_twitter-title` | Título para Twitter |
| `_yoast_wpseo_twitter-description` | Descrição Twitter |
| `_yoast_wpseo_meta-robots-noindex` | 1 = noindex |
| `_yoast_wpseo_meta-robots-nofollow` | 1 = nofollow |
| `_yoast_wpseo_is_cornerstone` | 1 = conteúdo cornerstone |

## Autenticação

Use **Application Passwords** (WordPress 5.6+):
1. Vá em Usuários → Seu Perfil → Application Passwords
2. Crie uma senha de aplicação
3. Use no header `Authorization: Basic base64(user:app_password)`

## Sincronização do Indexable

Após atualizar meta via REST, o Yoast pode não atualizar o `yoast_head` imediatamente.
Para forçar: use "Optimize SEO Data" no menu Tools do Yoast, ou re-salve o post.
