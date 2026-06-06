# Confeitaria que Lucra — Funil de Upsell

Páginas de **upsell** e **downsell** (1-clique) do ebook *Confeitaria que Lucra*, no padrão
visual da marca (Nunito · charcoal `#171e19` · vermelho `#ca0013` · sage `#b7c6c2`).

As duas páginas ficam em **pastas separadas e independentes**, cada uma com seu próprio
`index.html` na raiz — prontas para virar **dois projetos distintos no Vercel**.

## Estrutura

```
upsell/
  index.html              → oferta principal  (R$37)
  images/upsell.png        → mockup 3D do ebook
  images/upsell_capa.png   → capa (para anúncios/thumbnails)

downsell/
  index.html              → oferta de recuperação  (R$19)
  images/upsell.png        → mockup 3D do ebook
```

## O funil

```
Produto principal R$9,90
   └─ Order bumps no checkout
        └─ UPSELL R$37  → projeto "upsell"
             ├─ Aceitou  → entrega
             └─ Recusou  → DOWNSELL R$19 → projeto "downsell"
                                ├─ Aceitou → entrega
                                └─ Recusou → página de obrigado/acesso
```

## Deploy no Vercel (2 projetos, 1 repositório)

O Vercel permite criar vários projetos a partir do mesmo repositório, cada um apontando para
uma subpasta. Faça duas vezes:

### Projeto 1 — Upsell
1. **Add New → Project** → importe este repositório
2. Em **Root Directory**, selecione `upsell`
3. Framework: *Other* (site estático, sem build) → **Deploy**
4. Domínio sugerido: algo como `confeitaria-upsell.vercel.app`

### Projeto 2 — Downsell
1. **Add New → Project** → importe **o mesmo** repositório de novo
2. Em **Root Directory**, selecione `downsell`
3. Framework: *Other* → **Deploy**
4. Domínio sugerido: algo como `confeitaria-downsell.vercel.app`

Como cada pasta tem `index.html` na raiz, o domínio de cada projeto já abre a oferta direto.

## Configuração na Kiwify (4 links 1-clique)

Substitua os placeholders pelos links gerados na Kiwify ao configurar os upsells 1-clique:

| Página | Placeholder | Para onde aponta |
|---|---|---|
| `upsell/index.html` | `{{LINK_ACEITAR_KIWIFY}}` | aceite do upsell (R$37) |
| `upsell/index.html` | `{{LINK_RECUSAR_KIWIFY}}` | **recusa → URL do projeto downsell** |
| `downsell/index.html` | `{{LINK_ACEITAR_DOWNSELL_KIWIFY}}` | aceite do downsell (R$19) |
| `downsell/index.html` | `{{LINK_RECUSAR_DOWNSELL_KIWIFY}}` | recusa → página de obrigado/acesso |

> Importante: o **"recusar" do upsell** deve levar ao **domínio do downsell**, e o
> **"recusar" do downsell** à entrega/obrigado. Na Kiwify, ao encadear os upsells 1-clique,
> esse fluxo é montado automaticamente — basta apontar cada botão para o link correto.

## Edições rápidas

- **Preços:** procure por `R$ 37` em `upsell/index.html` e `R$ 19` em `downsell/index.html`.
- **Mockup:** substitua `images/upsell.png` (em cada pasta) mantendo o nome do arquivo.
- **Copy:** os textos estão direto no HTML, em blocos comentados por seção.
