# Virtunex — Site Institucional

Página "Em breve" temporária para [virtunex.com.br](https://virtunex.com.br).

## Estrutura

```
site-virtunex/
├── index.html    # Página principal (Coming Soon)
├── favicon.svg   # Favicon vetorial
└── README.md
```

## Deploy no Cloudflare Pages

### Opção 1 — Pelo painel web (recomendado)

1. Acesse [dash.cloudflare.com](https://dash.cloudflare.com) → **Pages**
2. Clique em **Create a project** → **Connect to Git**
3. Selecione o repositório `site-virtunex`
4. Configure o projeto:
   - **Project name:** `virtunex-site`
   - **Production branch:** `main`
   - **Build command:** *(deixe vazio)*
   - **Build output directory:** `/` *(raiz)*
5. Clique em **Save and Deploy**

O Cloudflare fará deploy automático a cada push na branch `main`.

### Opção 2 — Via Wrangler CLI

```bash
npm install -g wrangler
wrangler login
wrangler pages deploy . --project-name=virtunex-site
```

---

## Domínio Customizado — virtunex.com.br

Após o deploy no Cloudflare Pages:

1. No painel do projeto Pages → **Custom domains** → **Set up a custom domain**
2. Adicione `virtunex.com.br` e `www.virtunex.com.br`
3. O Cloudflare configurará os registros DNS automaticamente (se o domínio estiver na mesma conta Cloudflare)

### Configuração Manual de DNS

Se precisar ajustar manualmente no painel DNS do Cloudflare:

| Tipo | Nome | Conteúdo | Proxy |
|------|------|----------|-------|
| `CNAME` | `@` (raiz) | `virtunex-site.pages.dev` | Sim (laranja) |
| `CNAME` | `www` | `virtunex-site.pages.dev` | Sim (laranja) |

> O Cloudflare suporta CNAME Flattening no apex, então não é necessário registro `A`.

### Registros antigos da Hostgator que podem ser removidos

Após confirmar que o site está no ar pelo Cloudflare Pages:

| Tipo | Nome | Motivo |
|------|------|--------|
| `A` | `@` / `virtunex.com.br` | IP antigo Hostgator (69.6.213.237) — substituído |
| `A` | `www` | IP antigo Hostgator — substituído |
| `CNAME` | `cpanel` | Painel cPanel da Hostgator — não usamos mais |
| `CNAME` | `whm` | WHM da Hostgator — não usamos mais |
| `CNAME` | `webdisk` | WebDisk da Hostgator — não usamos mais |
| `CNAME` | `autodiscover` | Autodiscover de e-mail da Hostgator |
| `CNAME` | `autoconfig` | Autoconfig de e-mail da Hostgator |

> NÃO remova o registro `n8n.virtunex.com.br` — ele aponta para a VPS Hostinger e está em uso.

---

## Próximos passos previstos

- [ ] Página institucional completa (sobre, serviços, contato)
- [ ] Subdomínios por produto/serviço
- [ ] Backend para captação de e-mails do formulário "Avise-me"
