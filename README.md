# 💼 IC Financial Simulator

Simuladores interativos de investimentos em **Fundos de Investimento Imobiliário (FIIs)** com análise completa de cenários, projeções financeiras e alocação automática por perfil de investidor.

---

## 📊 Ferramentas Disponíveis

### 1️⃣ **IC Financial Simulator** — Versão Padrão
**Arquivo:** `IC_Financial_Simulator.xlsx` (28 KB)

A versão principal e mais acessível do simulador, ideal para investidores que querem uma experiência clara e objetiva com foco em simulações de FIIs.

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

### 2️⃣ **IC Financial** — Versão Expandida com Gestão Financeira
**Arquivo:** `IC_Finacial.xlsx` (136 KB)

A versão completa e profissional com recursos avançados de gestão financeira pessoal integrada com análise de investimentos em FIIs.

#### 🚀 Funcionalidades Principais:

| Módulo | Descrição |
|--------|-----------|
| **👤 TITULAR** | Dados pessoais completos (CPF, RG, endereço, contato) |
| **🏦 RENDIMENTOS BANCÁRIOS** | Consolidação de rendimentos de múltiplos bancos com totais |
| **📋 NOTAS BANCÁRIAS** | Extrato detalhado com categorias de despesas/receitas |
| **💼 ANÁLISE INTEGRADA** | Cruzamento entre situação financeira e planejamento em FIIs |
| **📊 RELATÓRIOS** | Geração automática de relatórios consolidados |
| **🎯 PLANEJAMENTO** | Simulação com base na situação financeira real |

#### 📌 Seções do IC_Financial:

1. **DADOS DO TITULAR**
   - Informações pessoais (nome, CPF, data de nascimento)
   - Contato (telefone, celular, email)
   - Endereço residencial completo
   - Status conjugal e dependentes

2. **INFORMES DE RENDIMENTOS BANCÁRIOS**
   - Total consolidado
   - Detalhamento por banco (Banco do Brasil, Itaú, Bradesco, etc.)
   - Valores atuais
   - Documentos anexados (PDFs)

3. **NOTAS BANCÁRIAS / EXTRATO DE HOLERITES**
   - Todas as entradas catalogadas por data
   - Categorias (Holerite, Freelance, Renda Extra, Venda, Reembolso, Bônus, Comissão, etc.)
   - Valores individuais
   - Timeline completa de 12+ meses

#### 💡 Caso de Uso Avançado:

```
Seu cenário financeiro real:
├─ Rendimento Banco do Brasil: R$ 5.000,00
├─ Rendimento Itaú: R$ 4.000,00
├─ Rendimento Bradesco: R$ 3.000,00
└─ Total: R$ 12.000,00

Categorias de entrada:
├─ Holerite (salário): R$ 4.500,00
├─ Freelance: R$ 1.200,00
├─ Renda Extra: R$ 600,00
├─ Dividendos: R$ 4.800,00
└─ ... e mais 15+ categorias

Resultado:
→ Proposta de aporte em FIIs: R$ 3.600,00/mês
→ Projeção em 5 anos: R$ +145.000,00
```

---

## 🚀 Como Usar

### Versão Padrão (IC_Financial_Simulator)

**Passo 1: Preencha os Dados (células em azul)**
```
D5:  Salário Mensal (R$)
D6:  Rendimento da Carteira (% a.m.)
D10: Quanto investir por mês (R$)
D11: Por quantos anos?
D12: Taxa de Rendimento Mensal (%)
```

**Passo 2: Escolha seu Perfil**
Na célula `D29`, selecione:
- **Conservador** — Segurança, foco em TIJOLO e PAPEL
- **Moderado** — Equilíbrio (padrão)
- **Agressivo** — Risco, foco em PAPEL e DESENVOLVIMENTO

**Passo 3: Acompanhe os Resultados**
As projeções e alocações atualizam automaticamente!

---

### Versão Expandida (IC_Financial)

**Passo 1: Preencha os Dados Pessoais**
- Aba "TITULAR": Seus dados completos

**Passo 2: Registre os Rendimentos**
- Aba "INFORMES": Rendimentos por banco

**Passo 3: Detalhe as Receitas**
- Aba "NOTAS": Cada entrada categorizada

**Passo 4: Simule Investimentos**
- Com base na sua situação real, a ferramenta sugere alocação em FIIs

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

## 📊 Categorias de Receitas (IC_Financial)

O sistema reconhece as seguintes categorias:

| Categoria | Descrição |
|-----------|-----------|
| **Holerite** | Salário mensal |
| **Freelance** | Trabalhos autônomos |
| **Renda Extra** | Ganhos adicionais |
| **Venda** | Venda de produtos/itens |
| **Reembolso** | Devolução de valores |
| **Bônus** | Bônus ou gratificação |
| **Comissão** | Comissões por vendas |
| **Aluguel** | Renda de aluguel |
| **Dividendos** | Rendimento de investimentos |
| **Presente** | Doações recebidas |
| **Lazer** | Atividades de lazer |
| **Saúde** | Reembolsos de saúde |
| **Farmácia** | Gastos com medicamentos |
| **Aluguel** | Despesa de aluguel |
| **Transporte** | Gastos com transporte |
| **Alimentação** | Gastos com alimentos |
| **Educação** | Gastos com educação |
| **Vestuário** | Gastos com roupas |
| **Academia** | Mensalidade de academia |
| **Streaming** | Serviços de streaming |
| **Internet** | Serviço de internet |
| **Energia** | Conta de energia |
| **Água** | Conta de água |
| **Supermercado** | Compras em supermercado |
| **Pet** | Gastos com animais |
| **Viagem** | Gastos com viagens |

---

## 🛠️ Tecnologias e Ferramentas

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)

- **Microsoft Excel** — Fórmulas avançadas, formatação condicional e validação de dados
- **Juros Compostos** — Cálculos precisos de acúmulo de patrimônio
- **INDEX/MATCH** — Busca dinâmica de alocação por perfil
- **Validação de Dados** — Dropdowns e regras para facilitar entrada
- **GitHub** — Versionamento e compartilhamento

---

## 💡 Dicas de Uso

✅ **Versão Padrão?** Use quando quer simular rapidamente sem dados pessoais  
✅ **Versão Expandida?** Use para planejamento realista com sua situação financeira  
✅ **Mude os valores** (células azuis) para simular seus próprios cenários  
✅ **Use diferentes perfis** para comparar estratégias de risco  
✅ **Acompanhe a Meta Financeira** para ver progresso real  
✅ **Distribua nos FIIs Reais** para uma carteira prática  
✅ **Compare versões** — Use ambas para melhor análise  

---

## 🔄 Comparativo: Qual Usar?

| Aspecto | Simulador Padrão | IC Financial |
|--------|:----------------:|:------------:|
| **Simplicidade** | ✅✅✅ | ✅✅ |
| **Rapidez** | ✅✅✅ | ✅ |
| **Análise Aprofundada** | ✅✅ | ✅✅✅ |
| **Dados Pessoais** | ✗ | ✅✅✅ |
| **Gestão Financeira** | ✗ | ✅✅✅ |
| **FIIs Reais** | ✅✅✅ | ✅✅ |
| **Múltiplos Bancos** | ✗ | ✅✅✅ |
| **Categorias Despesas** | ✗ | ✅✅✅ |

---

## 👤 Autor

**Igor Cardoso**

*Analista de BI & Dados · Power BI · SQL · Python · Excel · n8n*

[![GitHub](https://img.shields.io/badge/GitHub-igoorsa93-181717?style=for-the-badge&logo=github)](https://github.com/igoorsa93)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Igor_Cardoso-0A66C2?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/igorcardoso)

---

<div align="center">

**Projeto de Simulação de Investimentos em FIIs + Gestão Financeira Pessoal**

*Desenvolvido com ❤️ para investidores que querem planejar melhor*

</div>
