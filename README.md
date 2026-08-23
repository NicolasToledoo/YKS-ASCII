# YKS ASCII

> https://nicolastoledoo.github.io/YKS-ASCII/

Transforme imagens **ou texto** em arte ASCII. Modo Imagem com suporte a cores ANSI para terminal, e Modo Texto com dezenas de fontes figlet. Geração 100% no navegador, sem upload de dados.

## Funcionalidades

### Upload e Processamento
- Upload de imagem (PNG, JPG, WEBP até 10MB) via arrastar/soltar ou clique
- Processamento completo no cliente (privacidade garantida)

### Controles de Ajuste
- **Largura** (40-200 caracteres) — controla a resolução da saída
- **Contraste** (0.5x-2x) — ajuste linear de contraste
- **Brilho** (-100 a +100) — clareia ou escurece a imagem
- **Saturação** (0-200%) — desatura para cinza ou intensifica cores
- **Gama** (0.5x-3.0x) — correção não-linear de luminance
- **Agudeza** (0-100%) — filtro de nitIDEZ via convolução

### Modos de Renderização
- **Inverter** — inverte o mapeamento de caracteres (ideal para terminais escuros)
- **Detecção de Borda** — filtro Sobel para arte estilo sketch/line-drawing

### Conjuntos de Caracteres
- **Padrão** (10 caracteres) — equilibrado para uso geral
- **Detalhado** (13 caracteres) — mais gradientes
- **Estendido** (69 caracteres) — rampa Paul Bourke para fotografias
- **Blocos** (5 caracteres) — blocos Unicode para preenchimento sólido
- **Braille** — padrões Unicode Braille de alta densidade
- **Binário** (01) — estética de código
- **Mínimo** (4 caracteres) — design limpo
- **Personalizado** — defina seus próprios caracteres

### Modo Texto → ASCII (figlet)
- Alterna pelo botão **Texto** no topo da página
- Digite até 40 caracteres e escolha entre ~35 fontes figlet (Standard, Slant, Banner, Big, Block, Fraktur, Poison, 3D Diagonal, Graffiti, Sub-Zero, Script, Shadow, Speed, Varsity, entre outras)
- Renderização instantânea (debounce de 280ms) com fonte monospace e alinhamento à esquerda

### Exportação
- **Copiar** para área de transferência (preserva códigos ANSI)
- **Baixar TXT** — arquivo .txt com sequências ANSI opcionais
- **Baixar PNG** — renderiza a arte ASCII como imagem (JetBrains Mono, com `devicePixelRatio` para nitidez)
- **Copiar Img** — copia a arte como **imagem PNG** para a área de transferência (cola fiel em apps que colapsam espaços, como WhatsApp, Discord e Word)
- No Modo Texto, os mesmos botões (Copiar, TXT, PNG, Copiar Img) também estão disponíveis

> Dica: TXT/Copiar preservam os espaços e funcionam em editores/terminais monospace. Para compartilhar em apps que não usam fonte monospace, use **Copiar Img** ou **PNG**.

### Recursos Extras
- **Pré-visualização ao vivo** — gera ASCII automaticamente ao fazer upload e atualiza em tempo real ao ajustar controles
- **Progresso em tempo real** — barra de progresso durante o processamento
- **Tamanho de fonte responsivo** — auto-ajustado conforme viewport e largura

## Como usar

1. Abra `index.html` no navegador
2. Arraste ou selecione uma imagem
3. A arte ASCII é gerada automaticamente
4. Ajuste os controles para refinar o resultado (atualização ao vivo)
5. Use "Inverter" para terminais escuros
6. Ative "Detecção de Borda" para arte estilo sketch
7. Escolha "Personalizado" para definir sua própria rampa de caracteres
8. Copie para área de transferência ou baixe como TXT/PNG

## Estrutura do arquivo ANSI

```
ESC[<código_da_cor>m
<arte_ascii>
ESC[0m
```

## Arquivos

- `index.html` — aplicação completa (HTML + CSS + JS inline)
- `vendor/figlet-bundle.js` — lib figlet + todas as fontes `.flf` embutidas (script clássico, expõe `window.figlet` e `window.__FLF`; funciona via `file://` e GitHub Pages, sem `import`/`fetch`)
- `fonts/*.flf` — catálogo curado de fontes FIGlet (Standard, Slant, Banner, Big, Block, Fraktur, Poison, 3D Diagonal, Graffiti, Sub-Zero, Script, Shadow, Speed, Varsity, etc.)

## Tecnologias

HTML5, CSS3, JavaScript puro. Processamento via Canvas API nativo. Fundo animado via WebGL. Modo Texto usa a lib **figlet** (vendorizada, com fontes `.flf` embutidas no `vendor/figlet-bundle.js`, parseia no cliente). Sem dependências de runtime externas nem backend — funciona em GitHub Pages **e** via `file://` (abrir o `index.html` direto no navegador).
