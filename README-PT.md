# carlosrabelo.com

Portfólio de engenharia em inglês de Carlos Rabelo — software, arquitetura de sistemas, ferramentas de rede e open source.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Hugo](https://img.shields.io/badge/Hugo-0.164.0-blue.svg)](https://gohugo.io/)

## Destaques

- Site estático com Hugo Extended e tema mínimo customizado
- Conteúdo em inglês com feeds Atom e JSON
- Open Graph, JSON-LD e sitemap para SEO
- Deploy no GitHub Pages a cada push em `master`

## Pré-requisitos

- [Hugo Extended](https://gohugo.io/installation/) **0.164.0** (ou compatível)
- Dart Sass (necessário para os pipelines SCSS do Hugo)

## Instalação

```bash
git clone https://github.com/carlosrabelo/carlosrabelo.com.git
cd carlosrabelo.com
```

Instale o Hugo Extended na versão indicada em `.github/workflows/hugo.yml`.

## Uso

Pré-visualização local:

```bash
hugo server -D
```

Build de produção:

```bash
hugo --minify --baseURL "https://carlosrabelo.com/"
```

A saída fica em `public/`.

### Opcional: comentários Utterances

1. Instale o app [Utterances](https://utteranc.es/) neste repositório.
2. Em `config.toml`, descomente `params.comments.githubRepo`.

## Estrutura do Projeto

```
content/           Conteúdo do site (projects, articles, about)
themes/maverick/   Tema Hugo customizado (layouts, SCSS, assets)
themes/nix/        Tema Hugo alternativo com estética de terminal
themes/book/       Tema Hugo Book (estilo documentação)
static/            Arquivos estáticos do site (CNAME)
archetypes/        Arquétipos de conteúdo
.github/workflows/ Deploy no GitHub Pages
```

## Desenvolvimento

- `hugo server -D` — live reload com rascunhos
- `hugo --minify` — build de produção
- `hugo --printPathWarnings` — alerta de caminhos (usado no deploy)

O deploy roda no push para `master`.

Nomes de arquivos markdown de conteúdo ficam em inglês.

Versão em português: [carlosrabelo.com.br](https://carlosrabelo.com.br/).

## Licença

Conteúdo do site e repositório: [MIT](LICENSE).

Tema (`themes/maverick`): MIT — baseado no [Maverick](https://github.com/canhtran/maverick) de Calvin Tran, com modificações de Carlos Rabelo. Veja [themes/maverick/LICENSE](themes/maverick/LICENSE).
