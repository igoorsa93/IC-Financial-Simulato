# 💼 IC Financial Simulator

<div align="center">

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen?style=for-the-badge)

**Simulador de Investimentos em Fundos Imobiliários (FIIs)**

*Desafio DIO · Ferramentas de Simulação de Investimentos com Excel*

</div>

---

## 📌 Sobre o Projeto

O **IC Financial Simulator** é uma planilha Excel interativa para simulação e planejamento de investimentos em **Fundos de Investimento Imobiliário (FIIs)**. A ferramenta combina cálculos financeiros, análise de cenários e referências de mercado em uma interface visual clara e objetiva.

### 🎯 Objetivos do Desafio

| # | Objetivo | Status |
|---|----------|--------|
| 1 | Criar ferramentas de simulação de investimentos em Excel | ✅ |
| 2 | Aplicar cálculos financeiros (rendimento mensal, dividendos) | ✅ |
| 3 | Documentar processos técnicos de forma clara e estruturada | ✅ |
| 4 | Utilizar o GitHub para compartilhamento de documentação técnica | ✅ |

---

## 📁 Estrutura do Repositório

```
ic-financial-simulator/
│
├── 📊 IC_Financial_Simulator.xlsx    ← Planilha principal
├── 📄 README.md                       ← Documentação (este arquivo)
│
└── 📂 images/
    ├── screenshot-simulador.png       ← Visão geral da aba Simulador
    ├── screenshot-cenarios.png        ← Tabela de Cenários de Projeção
    ├── screenshot-meta.png            ← Painel de Meta Financeira
    ├── screenshot-fiis.png            ← FIIs Reais Sugeridos
    └── screenshot-alocacao.png        ← Alocação por Perfil de Investidor
```

---

## 🗂️ Estrutura da Planilha

A planilha possui **3 abas** com funções distintas:

### `Simulador` — Interface Principal
A aba central da ferramenta, dividida em painéis:

| Painel | Localização | Função |
|--------|-------------|--------|
| ⚙️ Configurações Pessoais | Esquerda, topo | Salário, rendimento da carteira e sugestão de investimento |
| 📡 Taxas de Mercado | Direita, topo | Selic, CDI, IFIX yield médio e rendimento assumido |
| 📈 Parâmetros de Investimento | Esquerda, meio | Aporte mensal, prazo e taxa de rendimento |
| 🎯 Meta Financeira | Direita, meio | Valor da meta, prazo desejado, progresso e tempo necessário |
| 🏆 Resultados Projetados | Esquerda | Patrimônio acumulado e dividendos mensais estimados |
| 🔭 Cenários de Projeção | Esquerda, tabela | Projeções para 2, 5, 10, 20 e 30 anos |
| 🏢 FIIs Reais Sugeridos | Direita, tabela | Referência de tickers, DY 12m, P/VP e cotações |
| 🧩 Perfil & Alocação | Inferior | Distribuição por tipo de FII conforme perfil do investidor |

### `Dados` — Base de Referência
Tabela com os percentuais de alocação para cada combinação de **Perfil × Tipo de FII**, usada pelas fórmulas `INDEX/MATCH` da aba Simulador.

### `Guia Rápido` — Documentação Interna
Passo a passo de uso da planilha e referência das fórmulas financeiras aplicadas.

---

## ⚙️ Como Usar

### Passo 1 — Configurações Pessoais

> Preencha as células destacadas em **azul** na seção ⚙️

| Célula | Campo | Valor Padrão |
|--------|-------|:------------:|
| `D5` | Salário Mensal (R$) | R$ 2.000,00 |
| `D6` | Rendimento da Carteira (% a.m.) | 0,600% |
| `D7` | Sugestão de Investimento | *Automático — 30% do salário* |

### Passo 2 — Parâmetros de Investimento

| Célula | Campo | Valor Padrão |
|--------|-------|:------------:|
| `D10` | Quanto investir por mês (R$) | R$ 200,00 |
| `D11` | Por quantos anos? | 5 anos |
| `D12` | Taxa de Rendimento Mensal (%) | 1,079% |

### Passo 3 — Defina sua Meta Financeira

| Célula | Campo | Valor Padrão |
|--------|-------|:------------:|
| `H11` | Valor da Meta (R$) | R$ 100.000,00 |
| `H12` | Prazo Desejado (anos) | 10 anos |

> Os campos **Patrimônio Projetado**, **Faltam para a Meta**, **% Atingida** e **Tempo Necessário** são calculados automaticamente.

### Passo 4 — Escolha seu Perfil

Na célula `D29`, selecione via **lista suspensa**:

- `Conservador` — Maior segurança, foco em TIJOLO e PAPEL
- `Moderado` — Equilíbrio entre risco e retorno *(padrão)*
- `Agressivo` — Maior exposição a PAPEL e DESENVOLVIMENTO

A tabela de alocação atualiza automaticamente os percentuais e valores em R$.

### Passo 5 — Distribua nos FIIs Reais (Opcional)

Na tabela **FIIs Reais Sugeridos**, informe o **Valor Investido (R$)** para cada ticker. A planilha calcula automaticamente a quantidade de cotas.

---

## 📐 Fórmulas Financeiras

### 1. Patrimônio Acumulado — Juros Compostos com Aportes

Calcula o montante total ao final do período com aportes mensais regulares:

$$M = PMT \times \frac{(1 + i)^{n} - 1}{i}$$

| Variável | Descrição | Célula |
|----------|-----------|--------|
| $PMT$ | Aporte mensal | `D10` |
| $i$ | Taxa de rendimento mensal | `D12` |
| $n$ | Número de meses (`anos × 12`) | `D11 × 12` |

```excel
=D10*((((1+D12)^(D11*12))-1)/D12)
```

---

### 2. Dividendos Mensais Estimados

Aplica o rendimento da carteira sobre o patrimônio acumulado:

$$Div_{mensal} = Patrimônio \times Rendimento_{carteira}$$

```excel
=D15*D6
```

---

### 3. Rendimento Anual Convertido para Mensal

Converte a taxa anual da Selic/CDI para equivalência mensal:

$$i_{mensal} = (1 + i_{anual})^{1/12} - 1$$

```excel
=(1+I5)^(1/12)-1
```

---

### 4. Tempo Necessário para a Meta

Calcula quantos meses são necessários para atingir o valor desejado:

$$n = \frac{\ln\left(\frac{Meta \times i}{PMT} + 1\right)}{\ln(1 + i)}$$

```excel
=LN((H11*D12/D10)+1)/LN(1+D12)/12
```

---

### 5. Alocação Dinâmica por Perfil

Busca o percentual de cada tipo de FII com base no perfil selecionado:

```excel
=IFERROR(INDEX(Dados!$D:$D, MATCH(D29&"-"&B33, Dados!$A:$A, 0)), 0)
```

> Combina `INDEX` + `MATCH` para busca dinâmica. A chave é formada por `Perfil-TipoFII` (ex: `"Moderado-PAPEL"`).

---

### 6. Quantidade de Cotas de FII

Calcula quantas cotas inteiras podem ser adquiridas com o valor informado:

```excel
=IFERROR(INT(J22/J21), 0)
```

---

## 🔭 Cenários de Projeção

Projeções automáticas com os parâmetros padrão (R$ 200/mês · 1,079% a.m.):

| Prazo | Patrimônio Acumulado | Dividendos/mês |
|:-----:|:--------------------:|:--------------:|
| 2 anos | R$ 5.445,53 | R$ 32,67 |
| 5 anos | R$ 16.755,38 | R$ 100,53 |
| 10 anos | R$ 48.656,84 | R$ 291,94 |
| 20 anos | R$ 225.039,68 | R$ 1.350,24 |
| 30 anos | R$ 864.433,93 | R$ 5.186,60 |

> *Altere os inputs para ver sua projeção personalizada. Os cenários recalculam automaticamente.*

---

## 📡 Taxas de Mercado (Referência)

| Indicador | Taxa (a.a.) |
|-----------|:-----------:|
| Taxa Selic (meta Copom) | 14,00% |
| CDI | 13,90% |
| IFIX – Yield Médio 10 anos | 8,00% |
| Rendimento Assumido (a.a.) | 7,44% |

> *Valores de referência. Sujeitos a variação diária. Não constituem recomendação de investimento.*

---

## 🏢 FIIs Reais Sugeridos (Referência)

| Ticker | Segmento | DY 12m | P/VP | Cotação |
|--------|----------|:------:|:----:|:-------:|
| MXRF11 | Papel (CRI) | 12,21% | 1,00 | R$ 9,19 |
| HGLG11 | Tijolo (Logística) | 8,99% | 0,89 | R$ 148,30 |
| KNRI11 | Híbrido | 8,29% | 0,97 | R$ 158,23 |
| XPML11 | Tijolo (Shoppings) | 10,59% | 0,95 | R$ 104,38 |

> *Dados sujeitos a variação diária. Não é recomendação de investimento.*

---

## 🧩 Perfis de Alocação

| Tipo de FII | Conservador | Moderado | Agressivo |
|-------------|:-----------:|:--------:|:---------:|
| PAPEL | 30% | 32% | 50% |
| TIJOLO | 50% | 35% | 10% |
| HÍBRIDOS | 10% | 8% | 5% |
| FOFs | 10% | 5% | 5% |
| DESENVOLVIMENTO | 0% | 10% | 20% |
| HOTELARIAS | 0% | 10% | 10% |
| **Total** | **100%** | **100%** | **100%** |

---

## 🛠️ Tecnologias Utilizadas

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Markdown](https://img.shields.io/badge/Markdown-000000?style=flat&logo=markdown&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)

- **Microsoft Excel** — Planilha, fórmulas, formatação condicional e validação de dados
- **openpyxl (Python)** — Geração e formatação programática da planilha
- **GitHub** — Versionamento e publicação da documentação
- **Markdown** — Documentação estruturada

---

## 📚 Referências

- [Documentação Oficial do GitHub](https://docs.github.com/)
- [GitHub Markdown Guide](https://docs.github.com/pt/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [GitHub Quick Start — DIO](https://github.com/digitalinnovationone/github-quickstart)
- [Formação GitHub Certification — GitBook](https://aline-antunes.gitbook.io/formacao-fundamentos-github)
- [Planilha Resolvida Original — DIO](https://hermes.dio.me/files/assets/a04b81b1-8e35-4e72-aeb9-98aed8ed4403.xlsx)

---

## 👤 Autor

<div align="center">

**Igor Cardoso**

*Analista de BI & Dados · Power BI · SQL · Python · Excel · n8n*

[![GitHub](https://img.shields.io/badge/GitHub-igorcardoso-181717?style=for-the-badge&logo=github)](https://github.com/igorcardoso)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Igor_Cardoso-0A66C2?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/igorcardoso)

</div>

---

<div align="center">

*Projeto desenvolvido como parte do desafio da [Digital Innovation One (DIO)](https://www.dio.me/) · 2025*

</div>
