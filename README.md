# Mentoria do Maicon · Quiz + página do vídeo

Página única pensada para o link da bio do Instagram.

1. **Quiz (primeira tela, sozinho):** 7 perguntas. A cada resposta, um ponto voa até o gráfico e a linha do "caminho até o primeiro contrato" sobe conforme o que a pessoa respondeu. No final aparece onde ela trava e o formato indicado (aula individual ou mentoria mensal).
2. **Página do vídeo (VSL):** abre depois do resultado, com título e conteúdo personalizados pelo quiz. Todos os botões abrem o WhatsApp com as respostas já escritas na mensagem.

Não precisa de build, servidor nem biblioteca: é HTML, CSS e JavaScript puros, num arquivo só.

---

## Arquivos

| Arquivo | Para que serve |
|---|---|
| `index.html` | A página inteira (quiz + vídeo). Estilo e código ficam dentro do próprio arquivo. |
| `404.html` | Página de "não encontrada" no mesmo visual, com botão de volta para o quiz. |
| `.nojekyll` | Arquivo vazio que avisa o GitHub Pages para publicar os arquivos como estão. |
| `README.md` | Este guia. |

---

## Publicar no GitHub Pages (uns 5 minutos)

1. No GitHub, crie um repositório novo (ex.: `mentoria-maicon`). Pode ser **público**.
2. Envie os arquivos desta pasta para a raiz do repositório: **Add file → Upload files** e arraste os arquivos.
   - O `.nojekyll` é um arquivo oculto e às vezes não aparece para arrastar. Se faltar, crie pelo próprio GitHub: **Add file → Create new file**, nome `.nojekyll`, deixe vazio e salve.
3. Vá em **Settings → Pages**. Em *Build and deployment*, escolha **Deploy from a branch**, branch **main**, pasta **/ (root)**, e clique em **Save**.
4. Em 1 a 2 minutos o endereço aparece no topo dessa mesma tela, no formato `https://SEU-USUARIO.github.io/mentoria-maicon/`.
5. Abra no celular e faça o quiz até o fim antes de mandar para o cliente.

**Link direto para a página do vídeo:** coloque `#video` no fim do endereço (ex.: `.../mentoria-maicon/#video`). Serve para stories ou para quem já fez o quiz.

---

## Antes de mandar a demo para o cliente

- **Prévia do link no WhatsApp:** no `index.html`, troque `SEU-USUARIO` e `NOME-DO-REPOSITORIO` pelo endereço real nas linhas `canonical`, `og:url` e `og:image`. Depois envie uma imagem `og-image.jpg` (1200 × 630) para a raiz do repositório. Sem a imagem o link funciona, mas aparece sem foto na conversa. O prompt para gerar a imagem está mais abaixo.
- **WhatsApp na demo:** enquanto o número for o de exemplo, os botões de WhatsApp abrem uma **prévia da mensagem** que chegaria para o Maicon, em vez de um link quebrado. É um bom argumento de venda: ele vê exatamente como o lead chega.
- **Atalho de demonstração:** no rodapé do quiz existe o link "Ver a página do vídeo", para mostrar a segunda tela sem responder tudo. Ele some quando o modo demo é desligado.

---

## Para ir ao ar de verdade (o que o Maicon troca)

### 1. Bloco de configuração

No `index.html`, procure por `CONFIGURAÇÃO` (fica no começo do código JavaScript, perto do fim do arquivo):

```js
var CONFIG = {
  whatsapp: "55XXXXXXXXXXX",
  video: { type: null, src: "" },
  demo: true
};
```

- **whatsapp:** DDI 55 + DDD + número, só dígitos. Ex.: `"5531999999999"`. Com o número certo, os botões passam a abrir o WhatsApp com a mensagem pronta.
- **video:**
  - YouTube: `{ type: "youtube", src: "ID_DO_VIDEO" }`. O ID é o trecho depois de `v=` no link (em `youtube.com/watch?v=abc123`, o ID é `abc123`). Deixe o vídeo como **Não listado** se não quiser que apareça no canal.
  - Arquivo próprio: `{ type: "mp4", src: "video.mp4" }` e envie o vídeo para o repositório. Comprima antes (o GitHub recusa arquivos acima de 100 MB e vídeo pesado demora a carregar no 4G).
- **demo:** troque para `false`. Somem os avisos de demonstração e o atalho "Ver a página do vídeo".

### 2. Liberar o Google

Apague a linha `<meta name="robots" content="noindex, nofollow">` no topo do `index.html`. Enquanto ela existir, o Google não indexa a página (de propósito, para a demo não aparecer nas buscas).

### 3. Conteúdo de exemplo (está marcado na página)

- [ ] Valores em `R$ [valor]` nos cartões **Aula individual** e **Mentoria mensal**
- [ ] 3 depoimentos (`[Nome]`, `[cidade]`, `[X]`, `[Y]`). Use só depoimentos reais, com autorização da pessoa.
- [ ] Etapas de **Como funciona** e respostas das **Dúvidas** (confirmar com o Maicon)
- [ ] Rodapé: `[Razão social] · CNPJ · [e-mail de contato]`
- [ ] Perguntas do quiz, se quiser ajustar: lista `Q` no código. Cada pergunta tem o texto (`q`), as opções (`o`), a versão curta que aparece no gráfico (`s`) e quanto cada resposta faz a linha subir (`d`).

---

## Medição (opcional)

O código já dispara estes eventos: `quiz_start`, `quiz_answer` (com o número da pergunta), `quiz_complete`, `quiz_restart`, `vsl_open`, `video_play` e `whatsapp_click` (com a origem do clique).

Eles **não fazem nada sozinhos**. Passam a funcionar quando o Pixel da Meta (`fbq`) ou o Google Tag Manager/GA4 (`dataLayer`) forem instalados. Com eles dá para ver em qual pergunta as pessoas desistem e qual botão mais leva ao WhatsApp.

Pela LGPD, ao instalar qualquer rastreamento coloque também um aviso de cookies e só carregue os scripts depois do aceite.

---

## Imagens que faltam (gerar no Gemini ou no ChatGPT)

### Ícone da aba (favicon)

Salve como `favicon.png` (512 × 512) na raiz e tire o comentário da linha `<link rel="icon" ...>` no topo do `index.html`.

```
Minimal square app icon, 1:1, 512x512. Solid graphite background (#1D1D1D). Centered, a bold lowercase letter "m" in pure white, in a heavy rounded geometric sans-serif similar to Poppins ExtraBold, followed by a small round lime green (#E4FC44) dot at the baseline like a period. Flat vector style, no gradients, no shadows, no texture, no other elements or text. Generous padding around the letter so it stays readable at 32x32 pixels. Crisp clean edges.
```

### Prévia do link (og-image.jpg)

Salve como `og-image.jpg` (1200 × 630) na raiz.

```
Horizontal social media preview image, exactly 1200x630, landscape. Solid dark graphite background (#1D1D1D) with a soft, blurred lime green (#E4FC44) light glow on the right side, subtle and premium. On the left half, large bold white headline text in a rounded geometric sans-serif similar to Poppins Bold, two lines: "Pare de estudar tráfego pago." and, below it in lime green (#E4FC44), "Comece a cobrar por ele." Under the headline, small light gray text: "Quiz de 1 minuto · Mentoria do Maicon". On the right half, a minimal glowing lime green line chart rising from bottom left to top right, with 7 small round dots on the line and a thin dashed horizontal line near the top. Lots of negative space, clean modern layout, no people, no logos, no icons, no extra text.
```

Confira se os acentos do texto saíram certos. Geradores de imagem às vezes erram letras; se errar, gere sem o texto e escreva por cima no Canva.

---

## O que foi testado

- Celular 320, 360 e 390 px de largura; computador 1366 e 1920 px
- Fluxo completo: responder, voltar, refazer, abrir a página do vídeo, abrir a prévia do WhatsApp, dúvidas
- Sem rolagem para o lado, sem erros no console, botões com pelo menos 44 px de altura
- HTML validado (html-validate, sem erros)
- Respeita a opção do aparelho de reduzir movimento
- Se o aparelho não tiver WebGL, a luz do fundo vira um gradiente e todo o resto funciona
