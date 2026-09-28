# Barba & Ofício — Landing Page

[![CI](https://github.com/guiguiegui/landing-barbearia/actions/workflows/ci.yml/badge.svg)](https://github.com/guiguiegui/landing-barbearia/actions/workflows/ci.yml)

Peça de portfólio: landing page de uma barbearia fictícia, focada em conversão (agendamento via WhatsApp), SEO técnico e acessibilidade. **Nome, endereço, telefone e depoimentos são fictícios** — este não é um negócio real.

🔗 **Demo ao vivo:** https://guiguiegui.github.io/landing-barbearia/

## Stack

HTML, CSS e JavaScript "vanilla", sem framework, sem bundler, sem dependências de build. Todo o site vive em um único [`index.html`](index.html).

## Decisões técnicas

- **Single-file por opção, não por limitação.** Para uma landing page de uma seção só, um único arquivo elimina requests extras (sem CSS/JS separados) e simplifica o deploy — não há necessidade de bundler para este escopo. Se o site crescer para múltiplas páginas, esse é o primeiro ponto a reavaliar.
- **Design tokens via CSS custom properties** (`:root { --bg, --accent, ... }`), com suporte nativo a modo claro/escuro via `prefers-color-scheme` e um atributo `data-theme` para eventual toggle manual futuro.
- **Zero imagens raster no conteúdo**: os ícones são SVG inline, então não há peso de imagem a otimizar no carregamento da página em si.
- **Acessibilidade tratada como requisito, não extra**: skip link, `aria-expanded`/`aria-controls` no menu mobile, foco visível em todos os elementos interativos, respeito a `prefers-reduced-motion`.
- **SEO técnico completo para uma página só**: `meta description`, Open Graph/Twitter Card, `canonical`, dados estruturados (`schema.org` `HairSalon`), `robots.txt` e `sitemap.xml`.

## Rodando localmente

Não há passo de build. Basta servir a pasta como arquivos estáticos:

```bash
python3 -m http.server 8000
```

Depois acesse `http://localhost:8000`.

## Deploy

Publicado via GitHub Pages a partir da branch `main` (raiz do repositório). Qualquer merge em `main` atualiza o site automaticamente em alguns minutos.

## CI

Todo Pull Request roda, via GitHub Actions ([`.github/workflows/ci.yml`](.github/workflows/ci.yml)):

1. Validação estrutural de HTML (`html-validate`).
2. Auditoria Lighthouse (performance, acessibilidade, SEO e boas práticas) contra budgets mínimos definidos em [`lighthouserc.json`](lighthouserc.json).

## ⚠️ Antes de usar em um cliente real

Este projeto tem dados de exemplo que precisam ser trocados:

- **Número de WhatsApp/telefone**: hoje é o placeholder `5519999999999`, usado nos links `wa.me` e `tel:` em [`index.html`](index.html). Troque pelo número real do negócio.
- **Endereço, horário e depoimentos**: fictícios, usados só para preencher o layout — inclusive no bloco de dados estruturados (JSON-LD) e no mapa incorporado.
- **`og-image.png`** e **`apple-touch-icon.png`**: gerados programaticamente a partir da paleta da marca (ver histórico de commits). Se o negócio tiver identidade visual/fotos próprias, vale substituir por artes reais.

## Assets gerados

`favicon.svg`, `apple-touch-icon.png` e `og-image.png` reaproveitam o mesmo traço de tesoura usado na marca (nav/rodapé) e a paleta de cores do site, para manter consistência visual entre a aba do navegador, o ícone de tela inicial e o preview de compartilhamento em redes sociais.

---

Projeto conceito para portfólio, desenvolvido por Guilherme Sousa.
