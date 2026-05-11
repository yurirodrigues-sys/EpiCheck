# EpiCheck: Um Simulador Epidemiológico
---

1. Tecnologias utilizadas

O EpiCheck foi construído inteiramente como um widget HTML/CSS/JavaScript renderizado inline no chat, usando:

- **HTML5 + CSS3** — estrutura e layout responsivo com CSS Grid e variáveis de tema (suporte automático a modo escuro/claro).
- **JavaScript (ES6)** — lógica de simulação numérica, atualização reativa dos controles e formatação de valores.
- **Chart.js 4.4** — renderização do gráfico de linhas com tooltips interativos e atualização em tempo real via `chart.update()`.
- **Tabler Icons** — ícones vetoriais via webfont.

---

2. Como o modelo SEIR funciona

O SEIR é um modelo compartimental: divide a população em quatro grupos que evoluem ao longo do tempo segundo equações diferenciais ordinárias.

**S — Suscetíveis:** pessoas que ainda podem contrair a doença. A cada dia, uma fração é exposta ao vírus dependendo do contato com infectados.

**E — Expostos:** pessoas infectadas, mas ainda no período de incubação — não transmitem a doença ainda. Essa é a principal diferença do SEIR em relação ao modelo SIR mais simples.

**I — Infectados:** indivíduos capazes de transmitir a doença. O pico desta curva é o momento crítico para os sistemas de saúde.

**R — Recuperados:** pessoas que desenvolveram imunidade (ou faleceram). Uma vez aqui, saem do ciclo de transmissão.

As equações que governam a dinâmica são:

```
dS/dt = −β·S·I / N
dE/dt =  β·S·I / N − σ·E
dI/dt =  σ·E − γ·I
dR/dt =  γ·I
```

Os três parâmetros centrais são **β** (taxa de transmissão por contato), **σ** (taxa de progressão da incubação) e **γ** (taxa de recuperação). A partir deles se calcula o número reprodutivo básico **R₀ = β / γ**: se R₀ > 1, a epidemia se propaga; se R₀ < 1, ela se extingue naturalmente.

Experimente os presets de **Influenza**, **COVID-19**, **Sarampo** e **Ebola** para ver como doenças com parâmetros distintos produzem curvas completamente diferentes.

3. Limitações

O EpiCheck é uma simulação simplificada, desconsiderando aspectos como ações humanas, diversidade populacional, etc.
Ferramentas como o EpiCheck são úteis pelo ponto de vista educacional/pedagógico, mas não devem ser utilizadas isoladamente como base empírica para a tomada de decisões sociopolíticas.

Criado com Claude.AI
