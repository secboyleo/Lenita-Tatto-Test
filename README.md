# Lenita — site

Site estático (HTML/CSS/JS puro, sem build) pra galeria de tatuagens da Lenita.

## Estrutura

```
lenita-tattoo/
├── index.html          → todo o conteúdo e as seções do site
├── styles.css          → visual (cores, tipografia, layout)
├── script.js           → menu mobile e ano do rodapé
└── assets/photos/      → todas as fotos usadas no site
```

## Fotos — tamanho e proporção certos

Os dois grids do site (**trabalhos feitos** e **disponíveis**) usam a mesma
proporção de imagem: **3:4 (retrato)**. O CSS já corta (`object-fit: cover`)
qualquer foto que não vier exatamente nessa proporção, então o ideal é já
mandar a imagem cortada certa pra não perder parte importante do desenho.

**Tamanho recomendado:** 900×1200px (mínimo) até 1200×1600px (ideal).
Formato JPG, qualidade ~80-85% — dá uma foto leve e nítida sem pesar o site.

- Fotos maiores que isso: eu redimensiono.
- Fotos em outra proporção (quadrada, paisagem, celular vertical padrão
  9:16 etc.): também dá pra usar, só que o CSS vai cortar as bordas
  esquerda/direita ou topo/base pra encaixar no 3:4 — melhor deixar a parte
  principal da tattoo centralizada na foto.

### Adicionar um trabalho novo em "trabalhos feitos"

Copie um bloco `<figure class="work">...</figure>` inteiro dentro de
`.work-grid` no `index.html`, e ajuste `src`, `alt` e o texto do `figcaption`.

### Trocar/adicionar um flash em "disponíveis"

Copie um bloco `<figure class="flash-card">...</figure>` inteiro dentro de
`.flash-grid`, ajuste `src`/`alt`/nome, e coloque a foto em
`assets/photos/`. O selo "disponível" (ou "fechada") é o `<span class="ribbon">`
no topo do bloco.

Sempre preencha o `alt="..."` com uma descrição curta — ajuda acessibilidade
e SEO.

## Como colocar no ar (GitHub + Vercel)

### 1. Subir pro GitHub

```bash
cd lenita-tattoo
git init
git add .
git commit -m "site da Lenita"
```

Crie um repositório novo no GitHub (pode ser público ou privado) e depois:

```bash
git remote add origin https://github.com/SEU-USUARIO/lenita-tattoo.git
git branch -M main
git push -u origin main
```

### 2. Importar na Vercel

1. Entre em [vercel.com](https://vercel.com) e faça login com sua conta do GitHub.
2. Clique em **Add New → Project**.
3. Selecione o repositório `lenita-tattoo`.
4. Framework: deixe em **Other** (é site estático, não precisa de build command
   nem output directory — a Vercel já serve os arquivos como estão).
5. Clique em **Deploy**.

Em menos de um minuto o site já vai estar no ar em um endereço tipo
`lenita-tattoo.vercel.app`. Depois, se quiser, dá pra ligar um domínio próprio
em **Project Settings → Domains**.

### 3. Atualizar o site depois

Qualquer alteração que você fizer nos arquivos e enviar com:

```bash
git add .
git commit -m "atualiza galeria"
git push
```

...a Vercel já detecta e publica a nova versão automaticamente. Não precisa
fazer nada manual na Vercel depois do primeiro deploy.

## Editando o texto

Todo o conteúdo (títulos, textos, links) está direto no `index.html`, em
português, fácil de achar com Ctrl+F pelo texto que aparece na tela.

O link de contato aponta pro Instagram `@lenitaaaaaaaaaaaa`. Pra trocar,
procure por `instagram.com/lenitaaaaaaaaaaaa` no `index.html` (aparece em 3
lugares) e substitua.
