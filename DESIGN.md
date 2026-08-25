# Direção de arte: site do Dr. Raul Matos Salomão

Blefaroplastia | CRO-MG 34575 | Belo Horizonte
Construído em 2026-08-24, fiel ao mockup aprovado (`Recursos Site/MOCKUP DESKTOP.png`).

---

## Conceito

Preto profundo e ouro polido. A referência de estrutura é o site do Dr. Pompilio (043),
mas com o metal trocado de prata para ouro, o brilho subido e a direção da luz invertida,
para não sair o mesmo site com outra cor.

O site é escuro por natureza e usa faixas claras como respiro. Seções alternam
rigorosamente: escura, clara, escura, clara, do hero até o rodapé.

---

## Paleta

| Token | Hex | Uso |
|---|---|---|
| `--ink` | `#08080A` | fundo das seções escuras, base do site |
| `--ink-2` | `#0E0D10` | rodapé, header |
| `--ink-3` | `#141216` | topo do gradiente dos cards escuros |
| `--cream` | `#F3EEE4` | fundo das seções claras |
| `--ink-cream` | `#14120E` | texto sobre creme |
| `--mute-cream` | `#5C5548` | texto secundário sobre creme |
| `--paper` | `#F4EFE5` | texto principal sobre escuro |
| `--mute` | `#A99E8A` | texto secundário sobre escuro |
| `--gold-deep` | `#8A6B1F` | ouro escuro, acento nas seções claras |
| `--gold` | `#C9A227` | ouro base, ícones, bordas |
| `--gold-bright` | `#FBE9A8` | highlight especular |

**Ouro espelho** (acento único do site):
`linear-gradient(100deg,#B08A1F 0%,#D8B33A 30%,#FFF3C6 52%,#D8B33A 72%,#B8901F 100%)`

Aparece na palavra destacada de cada headline, nos botões primários, na moldura do
monograma e no arco. Uma expressão destacada por headline, nunca duas.

Nas seções claras o gradiente troca para uma versão escura
(`#6E5314 → #B08A1C → #8A6B1F`), senão o ouro claro some no creme.

---

## Tipografia

**Par tipográfico fechado pelo Felipe: o mesmo do 024 ArqLife.** A stack foi copiada
literal de lá, incluindo a Optima Modoki na frente (fonte comprada, ainda sem arquivo,
então na prática quem renderiza é a Marcellus).

- **Display:** `'Optima Modoki', 'Marcellus', Optima, Candara, 'Gill Sans', 'Segoe UI'`,
  peso 400. Headlines, títulos de seção, nomes de card, monograma e numeração.
- **Corpo e utilitária:** Montserrat 400/500/600. Rótulos e botões em caixa alta com
  tracking de `.16em` a `.24em`.
- Link do Google Fonts idêntico ao do ArqLife:
  `family=Marcellus&family=Montserrat:wght@400;500;600`

Duas travas que sobraram das tentativas anteriores e continuam valendo:

1. **Cuidado com `line-height` apertado no display.** Em português os acentos altos
   encostam no topo da caixa de linha e ficam cortados. A Marcellus tem métrica folgada e
   aguenta 1.12 no hero, que é onde ele está. Títulos de seção e CTA em 1.22. Se a fonte
   de display mudar, conferir o "ê" de "você" na headline antes de baixar esse valor.
2. **Nada de didone nem de Garamond fino.** Bodoni Moda apagava no preto e Cormorant
   Garamond cortava o circunflexo de "você". As duas foram testadas e reprovadas.

Tamanhos atuais: hero `clamp(36px,4.85vw,62px)`, títulos de seção `clamp(30px,4.3vw,52px)`,
CTA final `clamp(30px,4.5vw,54px)`, título de card 22px.

Escala fluida com `clamp()` em toda a tipografia de display, valores acima.

---

## Assinatura visual: o arco da pálpebra

O único elemento decorativo do site. É um arco horizontal muito raso, com a curva de uma
pálpebra superior, traçado em 1px com gradiente de ouro e um brilho concentrado no ponto
mais alto.

Aparece em três escalas:
1. **Divisória de seção** (`.arc-divider`), largura total, entre uma seção clara e a
   escura seguinte.
2. **Sublinhado de título** (`.arc-title`), 160px, embaixo dos títulos centralizados.
3. **Abertura do CTA final** (`.arc-title.big`), 320px.

O arco se desenha ao entrar na tela: o JS mede o `getTotalLength()` do path e anima o
`stroke-dashoffset`. Com `prefers-reduced-motion`, aparece pronto.

---

## Luz

- Halo dourado **descendo do topo** de cada seção escura (`radial-gradient` em
  `.section-dark::before`). No Pompilio a luz sobe do rodapé, aqui desce. É de propósito.
- Halo grande atrás do Dr. Raul no hero (`.hero-glow`).
- Cards escuros com brilho interno no canto superior esquerdo e borda dourada de 1px.
- Reflexo especular correndo na diagonal dos botões primários no hover.

---

## Fotos

| Arquivo | Origem | Tratamento |
|---|---|---|
| `hero-desktop.jpg` | `IMAGEM NOVA HERO COM BACKGROUND.png` | 1672x941 em qualidade 95, cena completa do hero no desktop |
| `hero-desktop-2x.jpg` | idem | 2560x1441, reamostrada em bicúbica com máscara de nitidez, para telas grandes |
| `dr-raul-hero.jpg` | `DR RAUL - PARA O HERO.png` | 900px, recorte do Dr. usado **só no mobile**, com máscara de alfa embutida no CSS (ver abaixo) |
| `dr-raul-retrato.jpg` | `DR. RAUL.png` | 820px, moldura de linha dourada e halo atrás |
| `centro-cirurgico.jpg` | `ESTRUTURA HOSPITALAR.png` | 1000px, escurecida e com gradação quente, fundindo no preto pela esquerda |
| `resultado-01` a `04` | 4 das 9 fotos de antes e depois | barras do story recortadas automaticamente, sem esticar nem cortar o rosto |
| `equipe-01.jpg` | `Dr. Raul Trabalhando 2.jfif` | recortada **acima do campo cirúrgico**, tom quente por filtro CSS |
| `equipe-02.jpg` | `WhatsApp ... (10).jpeg` | idem |

**As duas fotos de centro cirúrgico são recortes deliberados.** As originais mostram o
campo aberto, com tecido e sangue à vista, o que a Resolução CFO-196/2019 veda em
publicidade e o que espanta paciente numa página de conversão. O corte pega só o que
interessa: a sala, os focos cirúrgicos, os monitores e a equipe paramentada. Se alguém
trocar por uma versão sem corte, os dois problemas voltam juntos.

**Por que o hero tem duas resoluções.** O arquivo que veio do ChatGPT tem 1672px de
largura. Numa tela de 1920 o navegador esticava essa imagem e o resultado ficava mole,
principalmente no rosto. A compressão não era a culpada: em teste lado a lado, q86 e q95
eram praticamente idênticos no zoom. O problema era o upscale do navegador, que usa
filtro bilinear.

A solução foi entregar a ampliação pronta em vez de deixar o navegador improvisar:

- `hero-desktop.jpg` (1672px, q95, 131 KB): telas até ~1670 de largura.
- `hero-desktop-2x.jpg` (2560px, 198 KB): reamostrada em bicúbica de alta qualidade e com
  máscara de nitidez leve (`amount` 0.55, raio 1px). Telas grandes e retina.
- O `srcset` com `sizes="100vw"` deixa o navegador escolher, e o `preload` carrega o
  candidato certo com `imagesrcset` mais `media`.

**O `<picture>` com fallback em GIF de 1x1 é intencional.** A `.hero-bg` fica
`display:none` no mobile, mas navegador baixa imagem escondida do mesmo jeito. Com o
`<source media="(min-width: 901px)">`, no celular nenhuma fonte casa e a `img` cai no GIF
de 1x1 embutido. O `media` no `<link rel="preload">` fecha o outro lado. Resultado: o
celular baixa zero byte do hero de desktop, e é de lá que vem quase todo o tráfego pago.

**O recorte do Dr. no hero.** `DR RAUL - PARA O HERO.png` já vem sem fundo, com canal
alfa de verdade. Salvar ele como JPEG achata o alfa em preto e cria um retângulo preto
atrás do Dr., que fica visível porque o halo dourado passa por cima do fundo da página
mas não por cima da foto. Já aconteceu uma vez, não repetir.

Só que o PNG com alfa em 900px pesa **912 KB**, inviável para tráfego pago no celular.
A solução final separa as duas coisas:

- `dr-raul-hero.jpg` (72 KB): a foto achatada em preto, só o conteúdo.
- `dr-raul-hero-mask.png` (22 KB): a mesma imagem com RGB todo branco e o alfa original.
  Como o RGB é constante, comprime dez vezes melhor que a foto.
- A `img` recebe esse alfa por `mask-image`. Resultado idêntico ao PNG transparente, por
  94 KB em vez de 912 KB.

**A máscara vai embutida no CSS como `data:image/png;base64`.** Isso não é enfeite: com
`url("../img/...")`, o Chrome recusa carregar a máscara em `file://` e a foto some por
completo da tela. Como o Felipe revisa abrindo o arquivo direto, tem que ser data URI. O
arquivo `dr-raul-hero-mask.png` fica na pasta só como fonte para regerar o base64.

O retrato da seção "Quem é o Dr. Raul" não usa máscara. Lá o retângulo é proposital, ele
vive dentro de uma moldura de linha dourada.

As fotos de antes e depois **não** recebem `object-fit: cover`. Cortar a altura cortaria
justamente o "depois", que fica na metade de baixo de cada imagem.

---

## Movimento

- Sequência de entrada do hero: rótulo, três linhas da headline, subheadline, botões,
  foto e faixa de selos, escalonados por CSS `animation-delay`.
- Demais blocos entram com `IntersectionObserver` (`.reveal`), deslocamento de 20px e
  atraso escalonado via `--d`.
- FAQ em acordeão com `grid-template-rows: 0fr → 1fr`, que anima de verdade, sem
  `max-height` chutado.
- Tudo desligado em `prefers-reduced-motion: reduce`.

---

## Estrutura (12 seções)

| # | Seção | Fundo |
|---|---|---|
| 1 | Header fixo | escura |
| 2 | Hero + faixa de 5 selos | escura |
| 3 | Sinais (8 cards) | CLARA |
| 4 | A cirurgia (6 cards com WhatsApp próprio) | escura |
| 5 | Resultados, antes e depois (4 casos) | CLARA |
| 6 | Quem é o Dr. Raul | escura |
| 7 | Como funciona (5 etapas) | CLARA |
| 8 | Estrutura hospitalar | escura |
| 9 | Compromissos + CTA | CLARA |
| 10 | Perguntas frequentes (12) | escura |
| 11 | CTA final | CLARA |
| 12 | Rodapé | escura |

---

## Regras que não podem ser quebradas

- **O hero tem duas versões e isso é de propósito.** No desktop é full bleed: a imagem
  `hero-desktop.jpg` ocupa a faixa inteira, com o Dr. no terço direito e o texto por cima
  do terço escuro da esquerda. No mobile essa cena horizontal não cabe (o Dr. ficaria
  cortado), então `.hero-bg` e `.hero-veil` somem e volta o recorte dele em coluna única.
  A troca acontece em `max-width:900px`. Quando chegar a versão mobile da imagem gerada,
  é aqui que ela entra.
- **Mobile, ordem do hero:** rótulo, headline, foto, subheadline, botões. A foto entra
  entre o título e o subtítulo, nunca depois dos botões.
- **"Especialista" só para Harmonização Facial.** No CFO o termo é reservado a
  especialidade registrada. Em blefaroplastia o Dr. Raul tem pós-graduação, então no site
  ele é sempre "pós-graduado em blefaroplastia", nunca "especialista em blefaroplastia".
- **WhatsApp por serviço:** cada um dos 6 cards de procedimento abre o WhatsApp com a
  mensagem já preenchida daquele procedimento.
- **Toda seção termina em conversão.** São 19 links de WhatsApp na página e cada um leva
  uma mensagem diferente, escrita a partir do contexto da seção de onde saiu. Isso não é
  só volume de botão: quando a mensagem chega já dizendo de onde veio ("me reconheci nos
  sinais", "vi os resultados", "quero tirar dúvida sobre como a cirurgia é feita"), o
  atendimento começa qualificado. Ao criar seção nova, criar a mensagem junto.
- **Nada de travessão** em nenhum texto do site.
- **Nada de "médico"** em lugar nenhum. O Dr. Raul é cirurgião-dentista, CRO-MG 34575.
- **Nenhuma promessa de resultado.** O rodapé carrega o aviso legal e a seção de antes e
  depois carrega o disclaimer de variação individual.
- **Nenhuma imagem de cirurgia em andamento**, sangue, pontos ou marcação no rosto.
  Das 9 fotos recebidas, 5 mostram justamente isso e ficaram de fora.

---

## Acessibilidade

- Skip link, foco visível em ouro, `aria-expanded` no menu e no acordeão.
- Contraste conferido nos textos secundários sobre creme e sobre preto.
- Imagens com `alt` descritivo, `loading="lazy"` fora do hero.
- Navegação por teclado funcional em todo o acordeão.

---

## Peso

1,3 MB no total. Fontes pelo Google Fonts com `display=swap`, hero com `preload` e
`fetchpriority="high"`.
