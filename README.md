# Confeitaria que Lucra — Upsell

Página de **upsell** (1-clique) do ebook *Confeitaria que Lucra* — a oferta principal a
**R$37** exibida logo após a compra do produto principal.

Padrão visual da marca (Nunito · charcoal `#171e19` · vermelho `#ca0013` · sage `#b7c6c2`).
Integrada ao snippet oficial de upsell 1-clique da Kiwify.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | Página do upsell — **R$37** |
| `images/upsell.png` | Mockup 3D do ebook |
| `images/upsell_capa.png` | Capa do ebook (para anúncios/thumbnails) |

## Onde entra no funil

```
Produto principal R$9,90
   └─ Order bumps no checkout
        └─ UPSELL R$37  → este repositório
             ├─ Aceitou  → entrega
             └─ Recusou  → DOWNSELL R$19 (repo: confeitariaquelucradownsell)
```

## Deploy no Vercel
1. **Add New → Project** → importe este repositório
2. Framework: *Other* (site estático, sem build) → **Deploy**
3. O `index.html` está na **raiz**, então o domínio já abre a oferta direto — sem precisar
   configurar Root Directory.

## Integração Kiwify (já configurada)
O `index.html` já contém o snippet oficial de upsell 1-clique da Kiwify:

- **Botão de aceite** (`#kiwify-upsell-trigger-349Z1G7`): processa a compra com 1 clique.
- **Link de recusa** (`#kiwify-upsell-cancel-trigger-349Z1G7`): redireciona para o downsell.
- **Container** (`#kiwify-upsell-349Z1G7`): guarda `data-downsell-url` apontando para
  `https://confeitariaquelucradownsell.vercel.app/`.
- **Script**: `https://snippets.kiwify.com/upsell/upsell.min.js`.

## Edições rápidas
- **Preço:** procure por `R$ 37` no `index.html`.
- **Mockup:** substitua `images/upsell.png` mantendo o nome.
- **URL do downsell:** atributo `data-downsell-url` no `index.html`.
