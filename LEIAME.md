# Template de TCC — Graduação / FACOM / UFMS

Template LaTeX para Trabalho de Conclusão de Curso (monografia) dos cursos de
graduação da Faculdade de Computação da UFMS, baseado na classe **abnTeX2**,
com os elementos pré e pós-textuais exigidos pela ABNT já configurados.

## Estrutura de arquivos

```
tcc.tex                    Arquivo principal — preencha aqui os dados do trabalho
referencias.bib            Suas referências bibliográficas
cap1/introducao.tex        Introdução (problema, justificativa, objetivos)
cap2/fundamentacao.tex     Fundamentação teórica e trabalhos relacionados
cap3/desenvolvimento.tex   Desenvolvimento ou metodologia
cap4/resultados.tex        Resultados e discussão
cap5/conclusao.tex         Conclusão, limitações e trabalhos futuros
apendices/apendice-a.tex   Apêndice (opcional)
imagens/                   Coloque aqui as figuras
```

Os arquivos `abntex2.cls`, `abntex2cite.sty`, `abntex2abrev.sty` e os `.bst`
são a classe e os estilos da ABNT — **não edite**.

## Como começar

1. Em `tcc.tex`, preencha o bloco **DADOS DO TRABALHO**: curso, grau, título,
   autor, data e orientador(a). O nome do curso é usado automaticamente na
   folha de rosto.
   - Para orientadora, use `\orientador[Orientadora:]{Profa. Dra. ...}`.
   - Coorientação é opcional: descomente `\coorientador` ou `\coorientadora`.
2. Preencha a ficha catalográfica (palavras-chave e CDU), os agradecimentos,
   o resumo e a lista de siglas. Se a biblioteca fornecer a ficha em PDF,
   substitua o ambiente `fichacatalografica` por `\includepdf{...}`.
   Abstract, dedicatória e epígrafe são opcionais e estão comentados.
3. Escreva os capítulos nos arquivos `capN/*.tex`. Todos os marcadores no
   formato `<...>` são espaços a preencher.
4. O capítulo 3 traz dois roteiros: um para trabalhos de **desenvolvimento**
   (requisitos, arquitetura, implementação, testes) e outro, comentado, para
   trabalhos de **pesquisa** (metodologia, coleta, análise). Mantenha o que
   se aplica.
5. Ajuste a quantidade e a ordem dos capítulos nos `\include` do arquivo
   principal, conforme o seu trabalho.

## Compilação

```bash
pdflatex tcc
bibtex   tcc
pdflatex tcc
pdflatex tcc
```

Ou, mais simples:

```bash
latexmk -pdf tcc.tex
```

No Overleaf, basta definir `tcc.tex` como documento principal.

## Requisitos

Distribuição TeX com os pacotes `memoir`, `algorithmicx` (`algpseudocode`),
`tikz`, `listings`, `xcolor`, `xurl`, `hyperref`, `backref`, `pdfpages`, `lastpage` e
`lipsum`. Em TeX Live, o esquema `texlive-full` cobre tudo.

## Dicas

- Comente `\usepackage{lipsum}` quando não precisar mais de texto fictício.
- A opção `draft` na primeira linha do `\documentclass` acelera a compilação
  omitindo as figuras.
- Para citações numéricas, troque `\usepackage[alf]{abntex2cite}` por
  `\usepackage[num]{abntex2cite}`.
- Exemplos comentados de figura e tabela estão no capítulo 2; de código-fonte
  e algoritmo, no capítulo 3.
- Para impressão frente e verso, troque `oneside` por `twoside`.
