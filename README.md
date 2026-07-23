# Lenita — site

Site estático (HTML/CSS/JS puro, sem build) pra galeria de tatuagens da Lenita.

## Estrutura

```
lenita-tattoo/
├── index.html      → todo o conteúdo e as seções do site
├── styles.css      → visual (cores, tipografia, layout)
├── script.js       → menu mobile e ano do rodapé
└── assets/         → SVGs usados como imagens (troque pelas fotos reais)
```

## Fotos

As fotos reais já estão em `assets/photos/` (trabalhos + foto da Lenita
tatuando). A seção **disponíveis** ainda usa ícones de exemplo (SVG) porque
ainda não temos fotos de flash disponível — troque assim que tiver:

1. Coloque a foto nova dentro de `assets/photos/` (ex: `assets/photos/flash-1.jpg`).
2. No `index.html`, dentro de `.flash-card`, troque o bloco `<svg class="flash-icon">...</svg>` por:
   ```html
   <img src="assets/photos/flash-1.jpg" alt="Descrição do flash" class="flash-icon">
   ```
3. Pra adicionar um trabalho novo em **trabalhos feitos**, copie um bloco
   `<figure class="work">...</figure>` inteiro, cole antes do fechamento de
   `.work-grid` e ajuste `src`, `alt` e o texto do `figcaption`.
4. Sempre preencha o `alt="..."` com uma descrição curta — ajuda acessibilidade
   e SEO.

Dica: fotos em pé (retrato, proporção ~3:4) encaixam melhor no grid de
trabalhos sem cortar muita coisa importante.

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
