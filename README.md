# Mentoria do Maicon · Quiz + página do vídeo

Página única pensada para o link da bio do Instagram. Mentoria de **crescimento nas redes**: ensinar as pessoas a crescer e viralizar na internet (seguidores, alcance, conteúdo que prende, constância e leitura dos números). Não é sobre vender pelo Instagram. Tráfego pago fica com a Nextrix.

1. **Diagnóstico (primeira tela, sozinho):** 7 perguntas. A cada resposta, um ponto voa até o gráfico e a linha de crescimento sobe conforme o que a pessoa respondeu. Na pergunta 2 ela escolhe a meta (ex.: primeiros mil seguidores, viralizar) e a linha tracejada do gráfico ganha o nome dessa meta. No final aparece o veredito ("Não é o algoritmo. É o seu perfil.", ou o começo dos vídeos, a constância, a leitura dos números), o que isso está custando, um passo para fazer hoje e o formato indicado (sessão individual ou mentoria de 30 dias).
2. **Página do vídeo (VSL):** abre depois do resultado, com o título escrito para o ponto onde a pessoa trava e os 3 primeiros passos que o Maicon faria no perfil dela (uma amostra grátis do método). Todos os botões abrem o WhatsApp com as respostas já escritas na mensagem.

### O ângulo da copy

Todo mundo que vende mentoria de Instagram promete "crescer com estratégia". O diferencial real do Maicon é que ele roda anúncios na Nextrix: paga por cada visualização e sabe pelos números o que faz alguém parar de rolar o feed. A página inteira gira em torno disso, com o nome **orgânico com régua de anúncio**: a régua de quem paga por atenção, aplicada no conteúdo orgânico do aluno.

O diagnóstico prepara essa conversa: abre prometendo mostrar o que trava o perfil ("Spoiler: não é o algoritmo"), faz perguntas com cenas que a pessoa reconhece (o vídeo que empaca nas mesmas 200 visualizações, a trend copiada, o perfil que ninguém segue) e termina com um passo grátis para fazer hoje e os passos 2 e 3 guardados para a página do vídeo. Antes de publicar, o Maicon confirma se concorda com essa forma de apresentar o trabalho dele.

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

- [ ] **Entregas** dos cartões **Sessão individual** e **Mentoria de 30 dias**: auditoria ao vivo, bio reescrita, 10 ganchos, calendário de 30 dias, 4 encontros, revisão de vídeos, leitura semanal dos números, bônus de gravação e de WhatsApp direto. São sugestões: fica só o que o Maicon entrega de verdade.
- [ ] Duração da sessão (`[duração]`) e valores em `R$ [valor]` (o valor de cada item e o preço final)
- [ ] **Garantia** (`[o Maicon define a garantia]`). Se ele não quiser dar garantia, apague o cartão.
- [ ] **Vagas por mês** (`[X]`). Só deixe se o limite for real; escassez inventada queima a confiança.
- [ ] 3 depoimentos (`[Nome]`, `[@perfil]`, `[X]`, `[Y]`, `[Z]`). Use só depoimentos reais, com autorização da pessoa e, de preferência, com print do antes e depois.
- [ ] Etapas do **método** (Auditoria ao vivo, Ganchos que seguram, Rotina de 30 dias), a linha do tempo dos **90 dias** e as respostas das **Dúvidas** (confirmar com o Maicon)
- [ ] Rodapé: `[Razão social] · CNPJ · [e-mail de contato]`
- [ ] Perguntas do diagnóstico, se quiser ajustar: lista `Q` no código. Cada pergunta tem o texto (`q`), as opções (`o`), a versão curta que aparece no gráfico e na mensagem do WhatsApp (`s`) e quanto cada resposta faz a linha subir (`d`). Os nomes das metas ficam na lista `GOALS`. Em `GARGALOS` ficam, para cada ponto onde a pessoa trava, o texto do diagnóstico, o título da página do vídeo e os 3 primeiros passos (`plan`).

---

## Medição (opcional)

O código já dispara estes eventos: `quiz_start`, `quiz_answer` (com o número da pergunta), `quiz_complete`, `quiz_restart`, `vsl_open`, `video_play` e `whatsapp_click` (com a origem do clique).

Eles **não fazem nada sozinhos**. Passam a funcionar quando o Pixel da Meta (`fbq`) ou o Google Tag Manager/GA4 (`dataLayer`) forem instalados. Com eles dá para ver em qual pergunta as pessoas desistem e qual botão mais leva ao WhatsApp.

Pela LGPD, ao instalar qualquer rastreamento coloque também um aviso de cookies e só carregue os scripts depois do aceite. E revise a frase do rodapé que diz que as respostas do diagnóstico não são armazenadas: com rastreamento, as respostas resumidas passam a ir para a ferramenta de medição.

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
Horizontal social media preview image, exactly 1200x630, landscape. Solid dark graphite background (#1D1D1D) with a soft, blurred lime green (#E4FC44) light glow on the right side, subtle and premium. On the left half, large bold white headline text in a rounded geometric sans-serif similar to Poppins Bold, two lines: "Por que o seu perfil não cresce?" and, below it in lime green (#E4FC44), "Descubra em 1 minuto." Under the headline, small light gray text: "Diagnóstico gratuito · Mentoria do Maicon". On the right half, a minimal glowing lime green follower growth line chart rising from bottom left to top right, with 7 small round dots on the line and a thin dashed horizontal goal line near the top. Lots of negative space, clean modern layout, no people, no logos, no icons, no extra text.
```

Confira se os acentos do texto saíram certos. Geradores de imagem às vezes erram letras; se errar, gere sem o texto e escreva por cima no Canva.

---

## O que foi testado

- Celular 320, 360 e 390 px de largura; computador 1366 e 1920 px
- Fluxo completo: responder, voltar, refazer, abrir a página do vídeo, abrir a prévia do WhatsApp, dúvidas, link direto `#video`
- Notebook de tela baixa (1366 × 768): o botão principal da página do vídeo aparece sem rolar
- Sem rolagem para o lado, sem erros no console, botões com pelo menos 44 px de altura
- HTML validado (html-validate, sem erros)
- Respeita a opção do aparelho de reduzir movimento
- Se o aparelho não tiver WebGL, a luz do fundo vira um gradiente e todo o resto funciona
