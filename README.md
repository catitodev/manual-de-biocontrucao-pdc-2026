# Manual de Bioconstrução

**Recurso didático compartilhado sobre bioconstrução, arquitetura bioclimática, biomimética e soluções baseadas na natureza — organizado por competências, inspirado na abordagem prática do *Manual do Arquiteto Descalço* (Johan van Lengen).**

> "Este manual não é um livro de regras, mas um caderno de campo vivo. É um convite para desaprender a construção industrializada e retomar o contato com a terra, a palha e o sol."

Este repositório contém o código-fonte de um site de página única (SPA) que reúne, em 12 capítulos navegáveis, conteúdo técnico sobre construção natural — da escolha do terreno ao pós-obra — com referências normativas brasileiras atualizadas e links para aprofundamento gratuito.

## Sumário

- [Capítulos](#capítulos)
- [Como rodar localmente](#como-rodar-localmente)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Como o conteúdo é organizado](#como-o-conteúdo-é-organizado)
- [Fontes e citações](#fontes-e-citações)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

## Capítulos

| # | Capítulo | Conteúdo |
|---|----------|----------|
| 01 | Fundamentos | Bioconstrução, arquitetura bioclimática, biomimética, soluções baseadas na natureza, geobiologia e Síndrome do Edifício Doente |
| 02 | Fundações | Avaliação do local, sondagem SPT, tipos de fundação por técnica construtiva |
| 03 | Técnicas e Materiais | Terra crua (taipa, adobe, superadobe/hiperadobe, tadelakt), madeira, palafitas, pedra, tetos verdes, earthships |
| 04 | Estruturas Autoportantes | Domos e cúpulas geodésicas, zomes, yurts, arcos e catenárias, treliças de bambu |
| 05 | Saneamento | Sanitários secos e com água, fossas e sumidouros, biodigestores, captação e purificação de água, cisternas |
| 06 | Planejamento e Projeto | Ciclo do projeto, desenho técnico, escalas e normas, softwares livres e pagos, BIM |
| 07 | Gestão da Bioconstrução | Cronograma físico-financeiro, orçamento, gestão de equipe e mutirão, segurança do trabalho |
| 08 | Segurança e Normas Técnicas | Panorama normativo, ART/RRT, aprovação municipal, licenciamento ambiental |
| 09 | Acabamentos | Rebocos de terra e cal, tadelakt, pinturas naturais, piso de terra batida |
| 10 | Entrega e Pós-obra | Comissionamento, Manual de Uso/Operação/Manutenção, Avaliação Pós-Ocupação |
| 11 | Situações Urbanas, Periurbanas e Rurais nos Biomas | Adaptação do manual ao contexto territorial e à paisagem |
| 12 | Repositório de Links | Consolidado de referências, cruzado por seção e competência |

## Como rodar localmente

Este site é uma aplicação de página única que carrega o conteúdo dinamicamente via
`import('./content-data.js')`. Por isso **não abra o arquivo `.dc.html` direto no
navegador (duplo clique)** — os navegadores bloqueiam esse tipo de carregamento de
módulo sob o protocolo `file://`, e a página aparece incompleta (só o menu, sem
nenhum capítulo carregado).

Sirva a pasta por um servidor HTTP simples:

```bash
# Python (já vem instalado na maioria dos sistemas)
python3 -m http.server 8080

# ou, com Node.js instalado
npx serve .
```

Depois, abra `http://localhost:8080/Manual%20de%20Bioconstrução.dc.html` no navegador.

## Estrutura do projeto

```
.
├── Manual de Bioconstrução.dc.html   # shell da aplicação (layout, navegação, lógica de estado)
├── content-data.js                   # conteúdo de todos os 12 capítulos (fonte única de verdade)
├── support.js                        # runtime gerado pela plataforma (não editar manualmente)
├── image-slot.js                     # componente de imagem "drag-and-drop" (gerado pela plataforma)
├── assets/
│   ├── fontastique.ttf                # fonte usada em todo o site
│   ├── fundamentos/                   # ilustrações citadas do capítulo 01
│   └── saneamento/                    # ilustrações citadas do capítulo 05
├── uploads/                           # (fora do git) rascunhos originais em Markdown, um por capítulo
├── .gitignore
├── LICENSE.md
└── README.md
```

Os PDFs de origem (o próprio *Manual do Arquiteto Descalço* e outras fontes
acadêmicas de terceiros) **não são versionados neste repositório** — veja
[`.gitignore`](./.gitignore) e a seção [Fontes e citações](#fontes-e-citações)
abaixo.

## Como o conteúdo é organizado

Todo o conteúdo textual vive em `content-data.js`, como um array `CHAPTERS`. Cada
capítulo é um objeto com `num`, `title`, `subtitle`, `icon` e uma lista `blocks`,
onde cada bloco declara seu próprio tipo (`h2`, `h3`, `p`, `list`, `callout`,
`quote`, `table`, `img`, `links`, `video`, entre outros) e é renderizado pelo
template em `Manual de Bioconstrução.dc.html`. Isso mantém o conteúdo
completamente separado do layout — editar um capítulo nunca exige tocar em HTML.

Blocos de vídeo (`{k:'video', url:'...'}`) embutem um player do YouTube via
`iframe`, permitindo assistir sem sair da página.

## Fontes e citações

O conteúdo original deste manual foi escrito com inspiração explícita no
*Manual do Arquiteto Descalço* (Johan van Lengen, TIBÁ, 2004) e em normas
técnicas brasileiras vigentes (ABNT), sempre reescrito com voz própria e citado
como referência — nunca copiado literalmente. Em alguns capítulos, uma ou duas
ilustrações originais do livro são reproduzidas (recortes pequenos, sempre com
legenda de citação explícita da fonte e da edição) para ilustrar uma técnica
comentada diretamente no texto.

Os PDFs completos de origem (o livro, teses e artigos acadêmicos citados) ficam
fora deste repositório por padrão — consulte cada seção de "Fontes e para você
aprofundar" dentro do manual para o link oficial de cada documento.

## Contribuindo

Este é hoje um repositório privado de uso pessoal/didático. Se você tiver acesso
e quiser sugerir uma correção técnica, abra uma *issue* descrevendo a seção
afetada e a fonte da correção proposta.

## Licença

Conteúdo original sob **CC BY-NC-SA 4.0** — veja [`LICENSE.md`](./LICENSE.md)
para o texto completo e para o que fica de fora da licença (citações de
terceiros e o runtime gerado pela plataforma).
