# 👤 Guia do Usuário - Agregador Financeiro IC

## 📖 Começando

### Pré-requisitos
- ✅ Excel 2016 ou superior
- ✅ Macros habilitadas (opcional)
- ✅ Informações financeiras em mãos

### Primeira Vez?

1. **Baixe o arquivo** `IC_Financial.xlsx`
2. **Abra no Excel** e clique em "Habilitar Conteúdo"
3. **Comece em** aba **TITULAR**

---

## 🎯 Passo a Passo

### Etapa 1: Preencher Dados Pessoais

**Onde:** Aba `TITULAR`

```
┌─────────────────────────────────┐
│ DADOS DA PESSOA FÍSICA          │
├─────────────────────────────────┤
│ Nome Completo      [____________] │
│ CPF                [___.___.___-__] │
│ RG                 [____________] │
│ Data Nascimento    [__/__/____]   │
│ Endereço           [____________] │
│ Email              [____________] │
│ Telefone           [(__) _____-__] │
└─────────────────────────────────┘
```

**Passo a passo:**
1. Clique na célula de entrada do **Nome**
2. Digite seu nome completo
3. Pressione TAB para próximo campo
4. Preencha **CPF** no formato: 123.456.789-10
5. Preencha todos os campos solicitados

### Etapa 2: Registrar Informes de Rendimentos

**Onde:** Aba `INFORMES`

**Tipos de Rendimentos:**
- 💰 Rendimentos Bancários
- 📈 Rendimentos de Investimentos
- 🏦 Rendimentos de Aplicações
- 💵 Outras Rendas Financeiras

**Como adicionar:**
1. Vá para aba `INFORMES`
2. Preencha a primeira linha vazia:
   - **Banco:** Selecione da lista (TABELAS)
   - **Código:** Código do banco (001, 033, etc)
   - **Período:** No formato AAAA-MM (ex: 2024-01)
   - **Valor Bruto:** Valor total recebido
   - **IR Retido:** Imposto retido na fonte

**Dica:** Use Ctrl+D para duplicar linhas

### Etapa 3: Adicionar Extratos Mensais

**Onde:** Aba `NOTAS`

Use para registrar **movimentações mensais**:
- 📋 Holerites
- 📊 Extratos bancários
- 💳 Comprovantes de transferência
- 📑 Notas de crédito

**Como adicionar:**
1. Vá para aba `NOTAS`
2. Preencha:
   - **Data:** Dia da movimentação (dd/mm/yyyy)
   - **Banco:** Qual banco (conforme lista)
   - **Tipo:** Crédito/Débito
   - **Valor:** Montante movimentado
   - **Descrição:** Detalhes da operação

### Etapa 4: Revisar Totalizações

**Onde:** Aba `RESUMO` (gerada automaticamente)

Aqui você vê:
- 📊 **Total de Rendimentos**
- 💸 **Total de IR Retido**
- 💰 **Rendimento Líquido**
- 📈 **Consolidação por Banco**
- 📅 **Período Coberto**

---

## 🔍 Validações Automáticas

O sistema verifica:

✅ **CPF válido** — Dígitos verificadores  
✅ **Bancos conhecidos** — Lista oficial BCB  
✅ **Datas válidas** — Formato e período  
✅ **Valores positivos** — Sem negativos  
✅ **Campos obrigatórios** — Preenchimento  

### O que fazer se aparecer ERRO?

1. **Mensagem vermelha aparece:**
   - Leia a descrição
   - Corrija o valor
   - Clique validar

2. **Se ainda tiver erro:**
   - Verifique o formato
   - Consulte FAQ
   - Contate suporte

---

## 💾 Salvando Seu Trabalho

### Salvar Normalmente
```
Ctrl + S
ou
Arquivo → Salvar
```

### Criar Backup
```
Arquivo → Salvar Como
Digite: "IC_Financial_Backup_[data].xlsx"
```

### Dica de Segurança
🔐 **Crie backup semanal!**
- Copie arquivo para pasta externa
- Use pen drive ou cloud (Google Drive, OneDrive)
- Mantenha 2-3 versões recentes

---

## 🚀 Funcionalidades Extras

### Menu de Navegação
Aba `MENU` oferece:
- ⚡ Acesso rápido a todas abas
- 🔄 Atualizar dados
- 📊 Gerar relatório
- 💾 Fazer backup

### Atalhos de Teclado

| Atalho | Função |
|--------|--------|
| `Ctrl+S` | Salvar |
| `Ctrl+Z` | Desfazer |
| `Ctrl+Y` | Refazer |
| `F5` | Ir para célula específica |
| `Ctrl+Home` | Ir para A1 |
| `Ctrl+End` | Ir para última célula |

### Formatação Condicional
Linhas aparecem coloridas para:
- 🟢 **Verde** — Dados OK
- 🟡 **Amarelo** — Revisar
- 🔴 **Vermelho** — Erro/Falta dados

---

## 📊 Gerar Relatório

### Passo 1: Revisar Dados
- ✅ Todos os campos preenchidos?
- ✅ Valores estão corretos?
- ✅ Sem mensagens de erro?

### Passo 2: Consolidar
```
Menu → Consolidar Dados
```

### Passo 3: Exportar
```
Menu → Exportar Relatório
```

Escolha formato:
- 📄 PDF (para imprimir)
- 📊 Excel (para editar)
- 📋 CSV (para outro programa)

---

## ❓ Perguntas Frequentes

### P1: Como adicionar novo banco não listado?
**R:** Vá em TABELAS e adicione banco com código oficial do BCB

### P2: Posso ter múltiplos informes do mesmo banco?
**R:** Sim, adicione linhas separadas para cada período

### P3: Como exportar para declaração de IR?
**R:** Menu → Exportar → Formato IRPF

### P4: O que fazer se perdi dados?
**R:** Procure arquivo de backup ou use Ctrl+Z

### P5: Posso usar em Google Sheets?
**R:** Parcialmente — algumas fórmulas podem não funcionar 100%

### P6: Como recuperar arquivo corrompido?
**R:** Arquivo → Abrir → Procurar → Abrir e Reparar

### P7: Quanto tempo leva para atualizar?
**R:** ~2-5 segundos com até 10.000 registros

### P8: Posso compartilhar com meu contador?
**R:** Sim, recomendado usar Apenas Leitura

### P9: Qual é o limite de dados?
**R:** ~10.000 linhas por aba sem problemas

### P10: Como deletar dados antigos?
**R:** Selecione linhas → Clique direito → Deletar

### P11: O arquivo é seguro?
**R:** Sim, use proteção com senha se desejar

### P12: Posso ter vários usuários?
**R:** Não recomendado (usar controle de versão)

### P13: Como configurar impressão?
**R:** Arquivo → Preparar Página → Configurar

### P14: Qual a melhor forma de organizar dados?
**R:** Por período (mês) e por banco

### P15: Como fazer backup automático?
**R:** Windows → Histórico de Arquivos ativa backup

---

## 🎓 Dicas de Pro

### Dica 1: Organize por Período
```
Exemplo:
Linha 2: Janeiro 2024
Linha 3: Janeiro 2024 (Banco 2)
Linha 4: Fevereiro 2024
...
```

### Dica 2: Use Filtros
1. Clique em Dados → Filtro Automático
2. Filtre por banco
3. Filtre por período
4. Filtre por valor

### Dica 3: Tabelas Dinâmicas
```
Inserir → Tabela Dinâmica
Agregue por:
- Banco
- Período
- Tipo de Rendimento
```

### Dica 4: Gráficos de Análise
```
Selecione dados → Inserir → Gráfico
Escolha tipo:
- Colunas (comparação)
- Linhas (tendência)
- Pizza (proporção)
```

### Dica 5: Proteção de Dados
```
Estrutura → Proteger Planilha
Digite senha
Confirme
```

---

## 🔒 Segurança de Dados

### Informações Sensíveis No Arquivo

Seus dados incluem:
- 🔐 CPF (Identificação)
- 🔐 Dados bancários
- 🔐 Endereço completo
- 🔐 Valores de renda

### Recomendações de Segurança

✅ **Faça backup regularmente**  
✅ **Use senhas fortes**  
✅ **Não compartilhe arquivo aberto**  
✅ **Mantenha software atualizado**  
✅ **Use antivírus ativo**  
✅ **Proteja seu computador**  

**Nunca compartilhe com pessoas não confiáveis!**

---

## 📞 Suporte

### Antes de Contatar Suporte

1. Verifique FAQ acima
2. Consulte Troubleshooting
3. Tente reabrir o arquivo
4. Verifique versão do Excel

### Como Reportar Problema

Inclua:
- [ ] Versão do Excel (ex: 2019, 365)
- [ ] SO (Windows/Mac)
- [ ] Descrição clara do problema
- [ ] Passos para reproduzir
- [ ] Screenshot (se possível)

### Canais de Suporte
- 📧 Email: [seu-email]
- 💬 GitHub Issues
- 📱 WhatsApp: [seu-número]

---

## 📚 Recursos Adicionais

### Documentos Inclusos
- 📄 README.md — Visão geral
- 📄 DOCUMENTACAO_TECNICA.md — Técnico
- 📄 Este guia — Usuário

### Links Úteis
- [Banco Central do Brasil](https://www.bcb.gov.br)
- [Tabela de Bancos](https://www.bcb.gov.br/pom/spb/estatisticas/instituicoes.html)
- [IR - Receita Federal](https://www.gov.br/irpf)

### Ferramentas Complementares
- 📊 Excel Analyzer — Análise profunda
- 💾 CloudBackup — Sincronização automática
- 📈 PowerBI — Dashboards visuais

---

## 🎉 Próximas Etapas

Depois de usar a ferramenta:

1. **Imprima ou exporte** relatório para registros
2. **Leve ao contador** com dados organizados
3. **Guarde comprovantes** de todas transações
4. **Atualize mensalmente** com novos dados
5. **Faça backup** regularmente

---

## ⭐ Feedback

Adoraríamos sua opinião!

- O que você achou?
- O que funcionou bem?
- O que pode melhorar?
- Tem sugestões?

📧 Envie feedback para: [seu-email]

---

**Versão:** 1.0  
**Última atualização:** Setembro 2024  
**Status:** ✅ Pronto para Uso

### Próximos Passos
👉 [Voltar para README](README.md)  
👉 [Ver Documentação Técnica](DOCUMENTACAO_TECNICA.md)
