# 💼 IC Financial Simulator

Simuladores interativos de investimentos em **Fundos de Investimento Imobiliário (FIIs)** com análise completa de cenários, projeções financeiras e alocação automática por perfil de investidor.

---

## 📊 Ferramentas Disponíveis

### 1️⃣ **IC Financial Simulator** — Versão Padrão
**Arquivo:** `IC_Financial_Simulator.xlsx` (28 KB)

A versão principal e mais acessível do simulador, ideal para investidores que querem uma experiência clara e objetiva.

#### 🎯 Funcionalidades:

| Seção | Descrição |
|-------|-----------|
| **⚙️ Configurações Pessoais** | Salário mensal, rendimento da carteira, sugestão de investimento |
| **📡 Taxas de Mercado** | Selic, CDI, IFIX, rendimento assumido (dados de referência) |
| **📈 Parâmetros de Investimento** | Aporte mensal, prazo, taxa de rendimento mensal |
| **🎯 Meta Financeira** | Define valor, prazo desejado e acompanha progresso |
| **🏆 Resultados Projetados** | Patrimônio acumulado e dividendos mensais estimados |
| **🔭 Cenários Automáticos** | Projeções para 2, 5, 10, 20 e 30 anos |
| **🏢 FIIs Reais Sugeridos** | Tickers, Dividend Yield 12m, P/VP e cotações |
| **🧩 Perfil & Alocação Dinâmica** | Conservador, Moderado ou Agressivo |

#### 💡 Exemplo de Uso:
```
Aporte mensal:     R$ 200,00
Prazo:             5 anos
Taxa mensal:       1,079%
─────────────────────────────
Patrimônio esperado: R$ 16.755,38
Dividendos/mês:      R$ 100,53
```

---

### 2️⃣ **IC Financial** — Versão Expandida
**Arquivo:** `IC_Finacial.xlsx` (136 KB)

A versão completa e aprofundada com recursos adicionais para análise detalhada e planejamento financeiro avançado.

#### 🚀 Diferenciais:

- ✅ **Análise Aprofundada** — Dados mais detalhados e cenários estendidos
- ✅ **Planejamento Avançado** — Ferramentas complementares de estratégia de investimento
- ✅ **Comparativos** — Análise lado a lado de múltiplos cenários
- ✅ **Dados Estendidos** — Base de dados maior com mais FIIs e variações
- ✅ **Relatórios** — Geração de relatórios personalizados

---

## 🚀 Como Usar

### Passo 1: Escolha a Versão
- **Iniciante/Rápido?** → Use `IC_Financial_Simulator.xlsx`
- **Análise Profunda?** → Use `IC_Finacial.xlsx`

### Passo 2: Abra no Excel
Duplo clique no arquivo escolhido ou:
```bash
Arquivo → Abrir → Selecione o Excel desejado
```

### Passo 3: Preencha os Dados (campos em azul)
```
D5:  Salário Mensal (R$)
D6:  Rendimento da Carteira (% a.m.)
D10: Quanto investir por mês (R$)
D11: Por quantos anos?
D12: Taxa de Rendimento Mensal (%)
```

### Passo 4: Escolha seu Perfil
Na célula `D29`, selecione:
- **Conservador** — Segurança, foco em TIJOLO e PAPEL
- **Moderado** — Equilíbrio (padrão)
- **Agressivo** — Risco, foco em PAPEL e DESENVOLVIMENTO

### Passo 5: Acompanhe os Resultados
As projeções e alocações **atualizam automaticamente**!

---

## 📐 Fórmulas Utilizadas

### 1. Patrimônio Acumulado (Juros Compostos com Aportes)
```
M = PMT × [(1 + i)^n - 1] / i
```
**Exemplo Excel:**
```excel
=D10*((((1+D12)^(D11*12))-1)/D12)
```

### 2. Dividendos Mensais Estimados
```
Div_mensal = Patrimônio × Rendimento_carteira
```
```excel
=D15*D6
```

### 3. Conversão de Taxa Anual para Mensal
```
i_mensal = (1 + i_anual)^(1/12) - 1
```
```excel
=(1+I5)^(1/12)-1
```

### 4. Tempo Necessário para Atingir a Meta
```
n = ln(Meta × i / PMT + 1) / ln(1 + i)
```
```excel
=LN((H11*D12/D10)+1)/LN(1+D12)/12
```

### 5. Alocação Dinâmica por Perfil
```excel
=IFERROR(INDEX(Dados!$D:$D, MATCH(D29&"-"&B33, Dados!$A:$A, 0)), 0)
```

---

## 📋 Cenários de Projeção (Padrão)
*Usando R$ 200/mês a 1,079% a.m.*

| Prazo | Patrimônio Acumulado | Dividendos/mês |
|:-----:|:--------------------:|:--------------:|
| 2 anos | R$ 5.445,53 | R$ 32,67 |
| 5 anos | R$ 16.755,38 | R$ 100,53 |
| 10 anos | R$ 48.656,84 | R$ 291,94 |
| 20 anos | R$ 225.039,68 | R$ 1.350,24 |
| 30 anos | R$ 864.433,93 | R$ 5.186,60 |

> *Altere os inputs para ver sua projeção personalizada!*

---

## 🏢 FIIs Reais Sugeridos (Referência)

| Ticker | Segmento | DY 12m | P/VP | Cotação |
|--------|----------|:------:|:----:|:-------:|
| MXRF11 | Papel (CRI) | 12,21% | 1,00 | R$ 9,19 |
| HGLG11 | Tijolo (Logística) | 8,99% | 0,89 | R$ 148,30 |
| KNRI11 | Híbrido | 8,29% | 0,97 | R$ 158,23 |
| XPML11 | Tijolo (Shoppings) | 10,59% | 0,95 | R$ 104,38 |

> ⚠️ *Dados de referência. Não é recomendação de investimento.*

---

## 🧩 Matriz de Alocação por Perfil

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

## 📡 Taxas de Mercado (Referência)

| Indicador | Taxa (a.a.) |
|-----------|:-----------:|
| Taxa Selic (meta Copom) | 14,00% |
| CDI | 13,90% |
| IFIX – Yield Médio 10 anos | 8,00% |
| Rendimento Assumido | 7,44% |

> ⚠️ *Valores de referência. Sujeitos a variação diária.*

---

## 🛠️ Tecnologias e Ferramentas

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)

- **Microsoft Excel** — Fórmulas avançadas, formatação condicional e validação de dados
- **Juros Compostos** — Cálculos precisos de acúmulo de patrimônio
- **INDEX/MATCH** — Busca dinâmica de alocação por perfil
- **GitHub** — Versionamento e compartilhamento

---

## 💡 Dicas de Uso

✅ **Mude os valores** (células azuis) para simular seus próprios cenários  
✅ **Use diferentes perfis** para comparar estratégias de risco  
✅ **Acompanhe a Meta Financeira** para ver progresso real  
✅ **Distribua nos FIIs Reais** para uma carteira prática  
✅ **Compare versões** — Use ambas para melhor análise  

---

## 👤 Autor

**Igor Cardoso**

*Analista de BI & Dados · Power BI · SQL · Python · Excel · n8n*

[![GitHub](https://img.shields.io/badge/GitHub-igoorsa93-181717?style=for-the-badge&logo=github)](https://github.com/igoorsa93)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Igor_Cardoso-0A66C2?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/igorcardoso)

---

<div align="center">

**Projeto de Simulação de Investimentos em FIIs**

*Desenvolvido com ❤️ para investidores que querem planejar melhor*

</div>
