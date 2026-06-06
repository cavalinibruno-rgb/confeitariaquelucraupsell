# Confeitaria que Lucra — Funil de Upsell

Páginas de **upsell** e **downsell** (1-clique) do ebook *Confeitaria que Lucra*, no padrão
visual da marca (Nunito · charcoal `#171e19` · vermelho `#ca0013` · sage `#b7c6c2`).

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | Oferta principal do upsell — **R$37** |
| `downsell.html` | Oferta de recuperação — **R$19** (para quem recusa o upsell) |
| `images/upsell.png` | Mockup 3D do ebook |
| `images/upsell_capa.png` | Capa do ebook (para anúncios/thumbnails) |

## O funil

```
Produto principal R$9,90
   └─ Order bumps no checkout
        └─ UPSELL R$37  → index.html
             ├─ Aceitou  → entrega
             └─ Recusou  → DOWNSELL R$19 → downsell.html
                                ├─ Aceitou → entrega
                                └─ Recusou → página de obrigado/acesso
```

## Configuração na Kiwify (4 links 1-clique)

Substitua os placeholders pelos links gerados na Kiwify ao configurar os upsells 1-clique:

| Página | Placeholder | Para onde aponta |
|---|---|---|
| `index.html` | `{{LINK_ACEITAR_KIWIFY}}` | aceite do upsell (R$37) |
| `index.html` | `{{LINK_RECUSAR_KIWIFY}}` | **recusa → leva ao `downsell.html`** |
| `downsell.html` | `{{LINK_ACEITAR_DOWNSELL_KIWIFY}}` | aceite do downsell (R$19) |
| `downsell.html` | `{{LINK_RECUSAR_DOWNSELL_KIWIFY}}` | recusa → página de obrigado/acesso |

> Importante: o **"recusar" do upsell** deve levar ao **downsell**, e o **"recusar" do downsell**
> deve levar à entrega/obrigado. Na Kiwify, ao encadear os upsells 1-clique, esse fluxo é montado
> automaticamente — basta apontar cada botão para o link correto.

## Deploy

Qualquer uma das opções abaixo publica o site em segundos. Como o arquivo principal é
`index.html`, a raiz do domínio já abre o upsell.

### GitHub Pages
1. **Settings → Pages**
2. Em *Source*, selecione a branch `main` e a pasta `/ (root)`
3. URL: `https://cavalinibruno-rgb.github.io/confeitariaquelucraupsell/`
   - Upsell: `…/` (raiz)
   - Downsell: `…/downsell.html`

### Vercel ou Netlify
1. *New Project* → importe este repositório
2. Sem build (site estático) → *Deploy*
3. A raiz serve o `index.html` (upsell); o downsell fica em `/downsell.html`

## Edições rápidas

- **Preços:** procure por `R$ 37` no `index.html` e `R$ 19` no `downsell.html`.
- **Mockup:** substitua `images/upsell.png` mantendo o nome do arquivo.
- **Copy:** os textos estão direto no HTML, em blocos comentados por seção.
