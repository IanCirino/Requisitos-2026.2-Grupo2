---
name: AdE - Amigo do Estudante
colors:
  surface: '#faf8ff'
  surface-dim: '#d2d9f4'
  surface-bright: '#faf8ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f2f3ff'
  surface-container: '#eaedff'
  surface-container-high: '#e2e7ff'
  surface-container-highest: '#dae2fd'
  on-surface: '#131b2e'
  on-surface-variant: '#43474d'
  inverse-surface: '#283044'
  inverse-on-surface: '#eef0ff'
  outline: '#74777e'
  outline-variant: '#c4c6ce'
  surface-tint: '#49607e'
  primary: '#000f22'
  on-primary: '#ffffff'
  primary-container: '#0a2540'
  on-primary-container: '#768dad'
  inverse-primary: '#b0c8eb'
  secondary: '#006398'
  on-secondary: '#ffffff'
  secondary-container: '#5bb8fe'
  on-secondary-container: '#00476e'
  tertiary: '#001304'
  on-tertiary: '#ffffff'
  tertiary-container: '#002b0d'
  on-tertiary-container: '#0fa048'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#d2e4ff'
  primary-fixed-dim: '#b0c8eb'
  on-primary-fixed: '#001c37'
  on-primary-fixed-variant: '#314865'
  secondary-fixed: '#cce5ff'
  secondary-fixed-dim: '#93ccff'
  on-secondary-fixed: '#001d31'
  on-secondary-fixed-variant: '#004b73'
  tertiary-fixed: '#7ffc97'
  tertiary-fixed-dim: '#62df7d'
  on-tertiary-fixed: '#002109'
  on-tertiary-fixed-variant: '#005320'
  background: '#faf8ff'
  on-background: '#131b2e'
  surface-variant: '#dae2fd'
typography:
  display-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 3rem
    fontWeight: '800'
    lineHeight: 3.5rem
    letterSpacing: -0.025em
  display-lg-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 2.25rem
    fontWeight: '800'
    lineHeight: 2.75rem
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 2rem
    fontWeight: '700'
    lineHeight: 2.5rem
    letterSpacing: -0.02em
  headline-lg-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 1.5rem
    fontWeight: '700'
    lineHeight: 2rem
    letterSpacing: -0.015em
  headline-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 1.5rem
    fontWeight: '600'
    lineHeight: 2rem
    letterSpacing: -0.015em
  headline-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 1.25rem
    fontWeight: '600'
    lineHeight: 1.75rem
    letterSpacing: -0.01em
  body-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 1.125rem
    fontWeight: '400'
    lineHeight: 1.875rem
    letterSpacing: 0em
  body-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 1rem
    fontWeight: '400'
    lineHeight: 1.625rem
    letterSpacing: 0em
  body-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 0.875rem
    fontWeight: '400'
    lineHeight: 1.375rem
    letterSpacing: 0.005em
  label-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 0.875rem
    fontWeight: '600'
    lineHeight: 1.25rem
    letterSpacing: 0.01em
  label-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 0.75rem
    fontWeight: '600'
    lineHeight: 1rem
    letterSpacing: 0.025em
  label-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 0.6875rem
    fontWeight: '700'
    lineHeight: 0.875rem
    letterSpacing: 0.04em
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1.5rem
  gutter-sm: 1rem
  gutter-lg: 2rem
  margin: 2rem
  margin-sm: 1rem
  margin-lg: 3rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2.5rem
---

## Brand & Style

O Amigo do Estudante (AdE) é a plataforma preparatória para o ENADE da Universidade de Fortaleza (UNIFOR). O design system ancora-se em uma estética **Corporate / Modern com foco EdTech e Editorial Acadêmico**: transmite seriedade institucional, rigor técnico e clareza analítica, equilibrados por uma energia estimulante de mentoria e acompanhamento pedagógico.

### Arquétipo e Personalidade
- **Autoridade Confiável:** A precisão formal e a reputação de excelência acadêmica da UNIFOR guiam a apresentação de dados, enunciados complexos e métricas de desempenho.
- **Clareza Cognitiva:** Foco irrestrito na redução da carga mental. Durante simulações de prova, a interface atua como suporte neutro e objetivo para a leitura de textos longos e gráficos.
- **Estímulo Progressivo:** O acompanhamento de simulados, gabaritos comentados e métricas de evolução entrega feedbacks visuais rápidos, celebrando conquistas e orientando pontos de reforço.

### Estilo Visual
A abordagem adota superfícies limpas em tons neutros frios, tipografia geométrica humanizada e estruturada, além de um sistema de cores funcionais de alto contraste estrito (WCAG 2.1 AA/AAA). As fronteiras dos componentes empregam contornos suaves e preenchimentos sutis em vez de sombras pesadas, mantendo a interface arejada, estável e livre de distrações cognitivas.

## Colors

A paleta equilibra a solidez da tradição acadêmica da UNIFOR com acentos modernos de interface analítica e estados de validação rigorosos:

- **Primary (`#0A2540` - Deep Navy):** Representa a solidez institucional. Utilizado em barras de navegação estruturais, botões primários de ação definitiva (ex.: "Iniciar Simulado", "Enviar Respostas"), cabeçalhos de seção e títulos de maior hierarquia.
- **Secondary (`#0284C7` - Vivid Cyan/Azure):** Cor de foco dinâmico, progresso e interatividade ativa. Aplicada em seletores de questões, abas ativas, links, indicadores de taxa de acerto e estados de foco de inputs.
- **Tertiary / Success (`#16A34A` - Forest Green):** Usada estritamente para gabaritos corretos, status de questões dominadas e métricas positivas. Garante leitura inequívoca com texto em contraste branco ou sobre fundo `#F0FDF4`.
- **Neutral Primary (`#0F172A` - Slate Ink):** O preto-ardósia balanceado para leitura de enunciados extensos, eliminando a fadiga gerada pelo preto puro (`#000000`) sem perder o contraste com o canvas.
- **Neutral Canvas & Surfaces (`#F8FAFC`, `#FFFFFF`):** Base estrutural dos cartões de prova e dashboards.
- **Borders & Dividers (`#E2E8F0`, `#CBD5E1`):** Delimitação precisa de alternativas e metadados.
- **Feedback Semântico:**
  - *Error (`#DC2626`):* Alternativas incorretas e alertas críticos.
  - *Warning / Review (`#D97706`):* Questões marcadas para revisão, tempo restante limite e alertas de atenção pedagógica.

## Typography

A família **Plus Jakarta Sans** unifica todo o sistema, combinando clareza técnica contemporânea com proporções abertas que garantem conforto visual prolongado.

- **Leitura de Enunciados (`body-lg` e `body-md`):** Possui altura de x avantajada e espaçamento entre linhas relaxado (1.6x a 1.7x o tamanho da fonte), facilitando a assimilação de enunciados analíticos, tabelas integradas e transcrições de casos.
- **Hierarquia de Títulos:** Títulos em peso 700 e 800 utilizam rastreamento negativo moderado (`-0.02em` a `-0.025em`) para criar densidade visual e autoridade nos painéis de desempenho e módulos de estudo.
- **Labels e Badges de Metadados (`label-sm`, `label-md`):** Empregam peso 600 ou 700 com ligeiro tracking positivo para legibilidade imediata em marcadores como "Formação Geral", "Conhecimento Específico" e índices de dificuldade.

## Layout & Spacing

A composição do AdE baseia-se em uma grade fluida de 12 colunas para desktop (máximo de 1440px centralizado), 8 colunas para tablets e 4 colunas para dispositivos móveis.

### Distribuição e Margens
- **Mobile (< 768px):** Margens externas de `1rem` (`margin-sm`), calhas de `1rem` (`gutter-sm`). Enunciados ocupam largura integral, com a barra de navegação de questões fixada no rodapé inferior em gaveta deslizante.
- **Tablet (768px - 1024px):** Margens de `1.5rem` a `2rem`, estruturação em 8 colunas para permitir visualização lado a lado de enunciados e opções.
- **Desktop (>= 1024px):** Layout assimétrico de split view:
  - *Coluna de Leitura e Resolução (8 colunas):* Espaço focado na questão, textos de apoio e alternativas com preenchimento interno `space-xl`.
  - *Coluna de Apoio Pedagógico (4 colunas):* Cronômetro de prova, mapa visual de questões respondidas/pendentes, filtros rápidos e status do bloco ENADE.

### Ritmo Vertical
O espaçamento interno de componentes adota múltiplos de `0.25rem` (4px base):
- `space-xs` (4px): Separação entre ícones e rótulos de badges.
- `space-sm` (8px): Espaçamento entre alternativas adjacentes e grupos de chips.
- `space-md` (16px): Padding interno de campos de texto, botões e cartões secundários.
- `space-lg` (24px): Separação entre o enunciado e o bloco de alternativas.
- `space-xl` (40px): Transições entre seções analíticas de métricas e separação de blocos temáticos.

## Elevation & Depth

O sistema prioriza a **clareza sobre o ornamento**, utilizando camadas tonais (`Tonal Surfaces`) e contornos discretos de baixo contraste, complementados por sombras sutis em situações de sobreposição contextual:

### Camadas de Superfície
- **Nível 0 (Background):** `#F8FAFC` — Canvas geral neutro e calmo.
- **Nível 1 (Cartões e Blocos Principais):** `#FFFFFF` com borda sólida de `1px` em `#E2E8F0`. Sem sombra em repouso para evitar cansaço visual.
- **Nível 2 (Alternativa Selecionada / Card em Destaque):** Borda de `1.5px` em `#0284C7` ou `#0A2540`, com fundo `#F0F9FF`.
- **Nível 3 (Elementos Flutuantes / Modais / Gabarito Suspenso):** Sombra suave e difusa de profundidade: `0 10px 25px -5px rgba(10, 37, 64, 0.08), 0 8px 10px -6px rgba(10, 37, 64, 0.04)` combinada a contorno de `1px` em `#CBD5E1`.

### Foco e Acessibilidade Visual
O estado de foco de teclado (tecla Tab) emprega um duplo anel concêntrico composto por um espaçamento de `2px` em branco seguido por um anel externo de `3px` na cor `#0284C7` com 100% de opacidade, assegurando conformidade estrita com a WCAG 2.1 AA.

## Shapes

O sistema adota o padrão **Rounded (Nível 2)**, equilibrando a postura formal institucional com a abordagem amigável e acessível de uma ferramenta de estudo interativo.

- **Tokens Base (0.5rem / 8px):** Inputs, botões de comando padrão, opções de múltipla escolha e itens de lista.
- **Tokens `rounded-lg` (1rem / 16px):** Cartões de questões, painéis de estatísticas, modais de resolução comentada e cards do dashboard do estudante.
- **Tokens `rounded-xl` (1.5rem / 24px):** Banners institucionais de boas-vindas, cards de simulação finalizada e contêineres de gráficos analíticos.
- **Exceção Pill-shaped (`full` / 9999px):** Reservado exclusivamente para badges de metadados (Dificuldade, Ano da Prova, Categoria ENADE), indicadores de cronômetro e mini-marcadores numéricos do grid de questões.

## Components

### 1. Botões (Action Buttons)
- **Primary:** Fundo `#0A2540`, texto `#FFFFFF`, borda transparente, cantos `rounded-md` (8px). Altura mínima de 44px para cumprir requisitos ergonômicos de toque. Em hover: escurecimento sutil e leve elevação táctil.
- **Secondary / Action:** Fundo `#0284C7`, texto `#FFFFFF`. Empregado para navegação de fluxo ("Próxima Questão", "Revisar Gabarito").
- **Outline / Ghost:** Borda `1px` `#CBD5E1`, fundo transparente, texto `#0A2540`. Utilizado em ações como "Salvar Rascunho" ou "Marcar para Revisão".

### 2. Alternativas de Múltipla Escolha (Question Options)
- **Estado Padrão:** Cartão com fundo `#FFFFFF`, borda de `1.5px` em `#E2E8F0`, padding `1rem`, raio `rounded-md`. Letra identificadora (A, B, C, D, E) alocada em um círculo com borda `#CBD5E1` e fundo `#F8FAFC`.
- **Estado Selecionado:** Borda `2px` em `#0284C7`, fundo `#F0F9FF`, letra de identificação com fundo `#0284C7` e texto `#FFFFFF`.
- **Estado de Correção / Gabarito:**
  - *Correta:* Borda `2px` `#16A34A`, fundo `#F0FDF4`, com ícone de confirmação.
  - *Incorreta (marcada pelo aluno):* Borda `2px` `#DC2626`, fundo `#FEF2F2`, com indicador de erro explícito.

### 3. Badges de Metadados ENADE
- Formato pílula (`rounded-full`), altura de 24px, tipografia `label-sm`, padding horizontal de 10px.
- **Componente Curricular:** Fundo `#E0F2FE`, texto `#0369A1` ("Conhecimento Específico", "Formação Geral").
- **Ano ENADE:** Fundo `#F1F5F9`, texto `#334155`, borda `1px` `#E2E8F0` (ex.: "ENADE 2023").
- **Dificuldade:**
  - *Fácil:* Fundo `#DCFCE7`, texto `#15803D`.
  - *Média:* Fundo `#FEF3C7`, texto `#B45309`.
  - *Difícil:* Fundo `#FEE2E2`, texto `#B91C1C`.

### 4. Grade de Navegação de Questões (Simulado Grid)
- Matriz compacta com botões circulares ou quadrados arredondados de 36x36px:
  - *Não respondida:* Borda `1px` `#CBD5E1`, texto `#64748B`, fundo `#FFFFFF`.
  - *Respondida:* Fundo `#0A2540`, texto `#FFFFFF`.
  - *Em revisão:* Fundo `#D97706`, texto `#FFFFFF` ou marcador superior âmbar.
  - *Questão ativa:* Anel externo duplo em `#0284C7`.

### 5. Campos de Entrada e Filtros de Busca
- Altura de 44px, fundo `#FFFFFF`, borda `1px` `#CBD5E1`, cor de texto `#0F172A`, placeholder `#94A3B8`.
- Transição de foco imediata com anel `#0284C7` de 2px e fundo inalterado.

### 6. Cartões de Resolução Comentada (Feedback Acadêmico)
- Cartões com fundo `#F8FAFC`, borda lateral esquerda de `4px` estruturada com a cor semântica do resultado (`#16A34A` para acerto, `#DC2626` para erro), contendo justificativa detalhada do professor/colegiado e referências das Diretrizes Curriculares Nacionais do curso.