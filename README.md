# Controle Tecnológico — Jotta Engenharia

App de ensaios de laboratório: solos, CAUQ, concreto e caracterização de insumos.
Roda no navegador, funciona sem sinal e grava tudo num banco de dados (Supabase), com login da equipe.

Esta pasta é o que vai para o GitHub Pages. O laboratorista instala pelo link,
e a atualização chega sozinha.

---

## Publicar pela primeira vez

**1. Crie o repositório**

No GitHub, `New repository`. Nome sugerido: `controle-tecnologico`.
Pode ser **público** — não há senha nem dado de cliente dentro do app.
No código só vai a chave pública do banco; quem lê e grava os ensaios é quem
entra com login, e cada empresa só vê os seus.

**2. Mande esta pasta para lá**

Pelo site: `Add file → Upload files`, arraste **o conteúdo desta pasta**
(não a pasta em si) e confirme com `Commit changes`.

Pela linha de comando:

```bash
git init
git add .
git commit -m "primeira versão"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/controle-tecnologico.git
git push -u origin main
```

**3. Ligue o Pages**

No repositório: `Settings → Pages`.
Em *Source*, escolha **Deploy from a branch**; em *Branch*, **main** e pasta **/ (root)**.
Salve. Em um ou dois minutos o endereço aparece nessa mesma tela:

```
https://SEU-USUARIO.github.io/controle-tecnologico/
```

Esse é o link que você distribui.

---

## Como o laboratorista instala

**Android (Chrome)** — abre o link, toca nos três pontinhos e escolhe
**Instalar aplicativo**. O ícone vai para a tela inicial e abre em tela cheia,
sem barra de endereço.

**iPhone (Safari)** — abre o link, toca em **Compartilhar** e escolhe
**Adicionar à Tela de Início**.

Depois de instalado funciona sem internet. A internet só é necessária para
sincronizar com o banco de dados.

---

## Publicar uma correção

Substitua o `index.html` e o `sw.js` pelos novos e faça o commit. Nada mais.

Em até meia hora com o app aberto — ou na próxima vez que abrirem — os
celulares mostram uma faixa **"Versão nova disponível"** com os botões
*Atualizar agora* e *Depois*. O app nunca troca de versão sozinho: se o
laboratorista estiver no meio de um lançamento, nada se perde.

> **Por que o `sw.js` também precisa ir junto:** é a linha `VERSAO` dentro dele
> que faz o navegador perceber que mudou alguma coisa. Ela é gerada a partir do
> próprio `index.html`, então cada versão do app tem a sua. Mandar só o
> `index.html` deixa os celulares presos na versão antiga.

---

## O que tem em cada arquivo

| Arquivo | Para que serve |
|---|---|
| `index.html` | O app inteiro, num arquivo só |
| `sw.js` | Guarda o app para funcionar sem sinal e avisa da versão nova |
| `manifest.webmanifest` | Nome, cores e ícones que o celular usa ao instalar |
| `icone-*.png` | Ícones da tela inicial |
| `versao.txt` | A versão publicada, útil para conferir o que está no ar |

---

## Marca do laboratório

A identidade já vem dentro do arquivo: logo, cores, fontes e o nome da empresa.
O laboratorista não configura nada — abre e trabalha. Isso vale para o topo da
tela, o título da janela, o ícone na tela inicial e o alto de todas as folhas
do relatório.

Cada cliente recebe o seu arquivo. Para gerar o de outro laboratório, crie
`marca/<cliente>/` com o `marca.json` e os arquivos de logo, e rode
`bash build.sh <cliente>`. O código do app não muda — só a pasta da marca.

**Nesta versão:** Jotta Engenharia. As cores vêm de `marca/<cliente>/paleta.json`
`#FFC400`, tipografia Barlow Semi Condensed nos títulos e Inter nos dados, as
duas embutidas para o app abrir sem sinal. O amarelo é sempre ação (botão, aba
corrente), nunca situação de ensaio — quem diz se passou ou não é o verde, o
âmbar e o vermelho, sempre com texto junto da cor.

---

## Banco de dados

Na primeira vez, o app pede o login: **Laboratorista** ou **Gestor**, o seu nome
e a senha do grupo. O que um aparelho lança chega aos outros em segundos.
Sem sinal, o lançamento fica guardado no celular e sobe quando a internet voltar.

---

## Perguntas que costumam aparecer

**Preciso pagar alguma coisa?**
Não. GitHub Pages é gratuito para repositório público.

**O repositório público expõe os ensaios?**
Não. O que fica no GitHub é o programa e a identidade visual do laboratório —
nada de obra, pessoa ou resultado. Os ensaios ficam no celular e no banco de
dados, que só abre com login.

**E se eu quiser um APK depois?**
Dá para acrescentar sem refazer nada: o mesmo repositório pode ganhar uma
automação que compila o APK a cada publicação.

**Posso continuar mandando o arquivo HTML solto?**
Pode, e ele funciona. Mas aberto direto do arquivo o celular guarda o histórico
de um jeito frágil, e cada aparelho fica numa versão diferente. Pelo link, os
dois problemas somem.
