# Mapa da Gestão Financeira — Página de Vendas (Nova versão 1)

Landing page estática de vendas do **Mapa da Gestão Financeira** (produto low-ticket da P4 Gestão).
Layout e estrutura reaproveitados da página **GPR Financeiro**, com a copy da página atual do MGF.

## Estrutura

```
.
├── index.html          # Página servida na raiz do domínio
├── images/             # WebP (primário) + PNG (fallback) — PLACEHOLDERS, substituir
│   ├── hero-mockup.{webp,png}        1200 x 800   — mockup da planilha (hero)
│   ├── mockup-dashboard.{webp,png}   1600 x 1067  — dashboard da planilha
│   ├── autor-wesley.{webp,png}        900 x 1125  — foto do Wesley (seção escura)
│   └── custo.{webp,png}               800 x 1000  — imagem da seção "custo de continuar no escuro"
├── _headers            # Headers de cache e segurança do Cloudflare Pages
├── .gitignore
└── README.md
```

Site 100% estático (HTML + CSS inline, sem JS). Sem build, sem dependências.
Fontes via Google Fonts e ícones via Tabler (CDN jsdelivr).

## Imagens

Todas as imagens em `images/` são **placeholders** com as dimensões corretas marcadas.
Basta gerar as versões reais e sobrescrever os arquivos mantendo os mesmos nomes.
Para melhor performance, exporte em `.webp` (primário) e mantenha um `.png` de fallback.

## Pontos de atenção na copy

- **Links dos botões de compra** (`.pl-cta` e CTAs): ainda apontam para `#`. Troque pelo link do checkout.
- **FAQ:** no PDF original só a 1ª resposta ("Como vou acessar?") estava visível. As demais
  (forma de pagamento, segurança, "funciona pra mim?", garantia, Excel) foram redigidas com
  respostas padrão coerentes — **revise, principalmente a de garantia**, para bater com a sua política real.
- **Depoimentos:** a página GPR tinha uma seção de depoimentos. Como o PDF do MGF não trazia
  depoimentos, a seção foi omitida para não inventar provas sociais. Dá pra adicionar depois.

## Publicação (Cloudflare Pages + GitHub)

1. `git init && git add . && git commit -m "MGF nova versão 1"` e suba para um repositório novo no GitHub.
2. Cloudflare → Workers & Pages → Create → Pages → Connect to Git → selecione o repo.
   Framework preset: `None`; Build command: vazio; Output directory: `/`.
3. Custom domains → aponte o domínio desejado. SSL automático.

A cada `git push` para `main`, o deploy é automático.
