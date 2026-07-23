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

## Como trocar as imagens de exemplo pelas fotos reais

As imagens em `assets/flash-*.svg` são só placeholders (desenhos de linha, no
mesmo estilo do site) pra você ver o layout funcionando. Pra usar fotos de
verdade:

1. Coloque as fotos dentro da pasta `assets/` (ex: `assets/rosa-1.jpg`).
2. No `index.html`, troque o `src` da tag `<img>` correspondente, ex:
   ```html
   <img src="assets/rosa-1.jpg" alt="Descrição da tattoo">
   ```
3. Sempre preencha o `alt="..."` com uma descrição curta — ajuda acessibilidade
   e SEO.
4. Pra adicionar um card novo na galeria, copie um bloco `<figure class="card">
   ...</figure>` inteiro e cole antes do fechamento de `.gallery`.

Dica: fotos quadradas (1:1) encaixam melhor no grid sem cortar.

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
