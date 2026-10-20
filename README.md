# Template de TCC — FACOM / UFMS

Template LaTeX para a monografia de Trabalho de Conclusão de Curso dos cursos
de graduação da Faculdade de Computação (FACOM) da UFMS. Ele usa a classe
**abnTeX2**, então capa, folha de rosto, ficha catalográfica, resumo, listas,
sumário e referências já saem formatados segundo as normas da ABNT. Seu
trabalho é **escrever o conteúdo**.

📄 Veja como fica o documento compilado: [`exemplo-compilado.pdf`](exemplo-compilado.pdf)

> As normas do seu curso e as orientações do(a) seu(sua) orientador(a) têm
> prioridade sobre este template. Na dúvida, consulte o regulamento de TCC do
> curso.

---

## 1. Escolha onde vai escrever

### Opção A — Overleaf da UFMS (recomendado)

A UFMS mantém sua própria instância do Overleaf em **<https://latex.ufms.br>**.
Você não precisa instalar nada nem criar conta: o acesso é feito com o
**Passaporte UFMS**.

1. Clique em **Code → Download ZIP** nesta página.
2. Entre em [latex.ufms.br](https://latex.ufms.br) com seu Passaporte UFMS.
3. Vá em **New Project → Upload Project** e envie o ZIP.
4. Abra **Menu** e confira: *Compiler* = `pdfLaTeX` e *Main document* = `tcc.tex`.
5. Clique em **Recompile**.

Para compartilhar o projeto com seu(sua) orientador(a), use o botão **Share**.

> O mesmo procedimento funciona no [overleaf.com](https://www.overleaf.com),
> caso você não tenha acesso ao Passaporte UFMS.

### Opção B — GitHub + computador (recomendado se você já usa Git)

1. Clique em **[Use this template](https://github.com/hsborges/template-facom-tcc/generate)**
   e crie um repositório **privado** na sua conta.
2. Clone o repositório e compile (veja a [seção 4](#4-compilando-no-seu-computador)).
3. Faça commits com frequência: você terá histórico e backup do texto.
   Dá para adicionar seu(sua) orientador(a) como colaborador(a).

---

## 2. Passo a passo para preencher

Todo texto entre `<` e `>` (por exemplo, `<Título do Trabalho>`) é um campo a
preencher. Siga esta ordem:

- [ ] **Dados do trabalho** — em `tcc.tex`, bloco `DADOS DO TRABALHO`: curso,
      grau, título, autor, data e orientador(a). Esses dados preenchem capa,
      folha de rosto e ficha automaticamente.
  - Orientadora: `\orientador[Orientadora:]{Profa. Dra. Fulana de Tal}`
  - Coorientação: descomente `\coorientador{...}` ou `\coorientadora{...}`
- [ ] **Ficha catalográfica** — palavras-chave e CDU. Se a biblioteca fornecer
      a ficha em PDF, troque o ambiente `fichacatalografica` por
      `\includepdf{ficha_catalografica.pdf}`.
- [ ] **Agradecimentos**, **resumo** (150 a 250 palavras, parágrafo único) e
      **palavras-chave**.
- [ ] **Opcionais** (já estão comentados em `tcc.tex`; descomente se quiser):
      dedicatória, epígrafe, abstract, lista de símbolos e anexos.
- [ ] **Lista de siglas** — mantenha só as siglas que aparecem no texto, em
      ordem alfabética.
- [ ] **Capítulos** — escreva em `capN/*.tex` (veja a [seção 3](#3-o-que-vai-em-cada-arquivo)).
- [ ] **Referências** — adicione em `referencias.bib`.

---

## 3. O que vai em cada arquivo

| Arquivo | Conteúdo |
|---|---|
| `tcc.tex` | Arquivo principal: dados do trabalho e elementos pré-textuais |
| `cap1/introducao.tex` | Contexto, problema, justificativa e objetivos |
| `cap2/fundamentacao.tex` | Fundamentação teórica e trabalhos relacionados |
| `cap3/desenvolvimento.tex` | Como o trabalho foi feito (veja abaixo) |
| `cap4/resultados.tex` | Resultados e discussão |
| `cap5/conclusao.tex` | Conclusão, limitações e trabalhos futuros |
| `apendices/apendice-a.tex` | Material produzido por você (opcional) |
| `referencias.bib` | Referências bibliográficas no formato BibTeX |
| `imagens/` | Figuras do trabalho |

O **capítulo 3** traz dois roteiros. Use o que se aplica e apague o outro:

- **Desenvolvimento** (sistema, aplicativo, ferramenta): requisitos,
  arquitetura, implementação e testes.
- **Pesquisa** (experimento, estudo empírico): metodologia, coleta e análise
  de dados. Esse roteiro está comentado.

Precisa de mais ou menos capítulos? Crie ou remova arquivos e ajuste as linhas
`\include{...}` em `tcc.tex`. Pode também renomear capítulos, por exemplo
"Desenvolvimento" para "Metodologia".

> ⚠️ **Não edite** `abntex2.cls`, `abntex2cite.sty`, `abntex2abrev.sty`,
> `abntex2-*.bst` e `abntex2-options.bib`. Eles implementam as normas ABNT.

---

## 4. Compilando no seu computador

Instale uma distribuição TeX completa:

| Sistema | Instalação |
|---|---|
| Linux (Debian/Ubuntu) | `sudo apt install texlive-full` |
| Windows | [TeX Live](https://tug.org/texlive/) ou [MiKTeX](https://miktex.org/) |
| macOS | [MacTeX](https://tug.org/mactex/) |

Depois, na pasta do projeto, rode:

```bash
latexmk -pdf tcc.tex
```

Sem o `latexmk`, rode os comandos na ordem abaixo. As referências só aparecem
depois da sequência completa.

```bash
pdflatex tcc
bibtex   tcc
pdflatex tcc
pdflatex tcc
```

No **VS Code**, a extensão [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
compila automaticamente ao salvar.

---

## 5. Guia rápido de escrita

Há exemplos prontos e comentados de figura e tabela em `cap2/fundamentacao.tex`,
e de código-fonte e algoritmo em `cap3/desenvolvimento.tex`. Copie, descomente
e adapte.

**Citações** (formato autor-data da ABNT):

```latex
\cite{exemplo-livro}          % (SOBRENOME, 2022)
\citeonline{exemplo-livro}    % Sobrenome (2022)
\cite[p.~42]{exemplo-livro}   % (SOBRENOME, 2022, p. 42)
```

A chave (`exemplo-livro`) é o identificador da entrada em `referencias.bib`.
Só aparecem nas Referências as obras citadas no texto. Para citações
numéricas, troque `\usepackage[alf]{abntex2cite}` por
`\usepackage[num]{abntex2cite}` em `tcc.tex`.

> 💡 Google Scholar, ACM DL, IEEE Xplore e o Zotero exportam BibTeX. Mesmo
> assim, confira os campos: autores, título, ano e local costumam vir errados.

**Figuras** — coloque o arquivo em `imagens/`. Formatos aceitos: PNG, JPG e
PDF. Para diagramas, prefira PDF.

```latex
\begin{figure}[!ht]
    \centering
    \includegraphics[width=0.75\textwidth]{imagens/arquitetura.pdf}
    \caption{Arquitetura da solução.}
    \label{fig:arquitetura}
    \fonte{Elaborado pelo autor.}
\end{figure}
```

**Referências cruzadas** — nunca escreva o número da figura, tabela ou seção
à mão. Use rótulos:

```latex
A arquitetura é apresentada na Figura~\ref{fig:arquitetura}
e detalhada na Seção~\ref{sec:implementacao}.
```

**Marcações de revisão** — `\red{...}`, `\blue{...}` e `\ma{...}` (magenta)
colorem trechos de texto. São úteis para comentários com o(a) orientador(a).

---

## 6. Problemas comuns

| Sintoma | Solução |
|---|---|
| Aparece `??` no lugar de citações ou referências | Compile de novo. Fora do Overleaf, use `latexmk` ou a sequência completa da seção 4. |
| `Citation 'x' undefined` | A chave citada não existe em `referencias.bib` ou foi digitada errada. |
| `File 'imagens/...' not found` | Confira o nome e a extensão do arquivo. Maiúsculas e minúsculas importam. |
| Acentos quebrados | Salve os arquivos `.tex` e `.bib` em UTF-8. |
| Caracteres `&`, `%`, `_`, `#` ou `$` causam erro | Escape com barra: `\&`, `\%`, `\_`, `\#`, `\$`. |
| Compilação lenta | Ative a opção `draft` na primeira linha do `\documentclass`. As figuras viram caixas vazias. |

---

## 7. Antes de entregar

- [ ] Nenhum marcador `<...>` sobrou no texto.
- [ ] Se usou `\lipsum` para gerar texto fictício, apague esses comandos.
      Depois remova `\usepackage{lipsum}` de `tcc.tex`.
- [ ] Não há marcações `\red`, `\blue` ou `\ma` esquecidas.
- [ ] A lista de siglas tem apenas siglas usadas no texto.
- [ ] Toda figura e tabela é citada no texto e tem legenda e fonte.
- [ ] As referências estão completas e corretas.
- [ ] A ficha catalográfica é a versão definitiva fornecida pela biblioteca,
      se exigida.
- [ ] Para impressão frente e verso, troque `oneside` por `twoside` no
      `\documentclass`.

Para listar os marcadores que ainda faltam preencher, rode no terminal:

```bash
grep -rn "<[^>]*>" --include="*.tex" .
```

---

Encontrou um problema ou tem uma sugestão para o template? Abra uma
[issue](https://github.com/hsborges/template-facom-tcc/issues).
