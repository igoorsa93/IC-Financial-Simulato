# 🔧 Documentação Técnica - Agregador Financeiro IC

## 1. Arquitetura de Dados

### 1.1 Modelo de Dados

```
PESSOA FÍSICA (Dimensão)
├── CPF (Chave Primária)
├── Nome
├── Endereço
├── Telefone
└── Email

BANCO (Dimensão)
├── Código do Banco
├── Nome da Instituição
├── Tipo (Público/Privado)
└── CNPJ

RENDIMENTO_BANCÁRIO (Fato)
├── ID Rendimento
├── CPF (FK)
├── Código Banco (FK)
├── Período (AAAA-MM)
├── Valor Bruto
├── IR Retido
└── Data Comprovante

MOVIMENTO_MENSAL (Fato)
├── ID Movimento
├── CPF (FK)
├── Data
├── Banco (FK)
├── Valor
├── Tipo Operação
└── Descrição
```

### 1.2 Relacionamentos

```
PESSOA_FÍSICA (1) ──────── (N) RENDIMENTO_BANCÁRIO
PESSOA_FÍSICA (1) ──────── (N) MOVIMENTO_MENSAL

BANCO (1) ──────── (N) RENDIMENTO_BANCÁRIO
BANCO (1) ──────── (N) MOVIMENTO_MENSAL

TABELAS ◄── VALIDAÇÃO (Todas as abas)
```

---

## 2. Fórmulas Principais

### 2.1 Validação

**Validar CPF:**
```excel
=IF(AND(LEN(A2)=11, ISNUMBER(VALUE(A2))), "✓", "✗")
```

**Validar Banco (Código Numérico):**
```excel
=IF(AND(ISNUMBER(A2), A2>0, A2<9999), "✓", "✗")
```

**Validar Período (AAAA-MM):**
```excel
=IF(AND(LEN(A2)=7, FIND("-",A2)=5), "✓", "✗")
```

**Validar Valor (Positivo):**
```excel
=IF(AND(ISNUMBER(A2), A2>=0), "✓", "✗")
```

### 2.2 Agregações

**Total de Rendimentos por Banco:**
```excel
=SUMIFS(
    Rendimentos!$E:$E,
    Rendimentos!$C:$C, "="&CodigoBanco,
    Rendimentos!$D:$D, "=2024*"
)
```

**Total de Movimentações Mensais:**
```excel
=SUMIFS(
    Movimentos!$E:$E,
    Movimentos!$D:$D, "="&CodigoBanco,
    Movimentos!$B:$B, ">=2024-01-01"
)
```

**Consolidado Anual:**
```excel
=SUMIF(Rendimentos!$D:$D, "=2024*", Rendimentos!$E:$E)
```

**Média Mensal:**
```excel
=AVERAGE(Movimentos!$E:$E)
```

### 2.3 Cálculos Financeiros

**Valor Líquido (Bruto - IR):**
```excel
=E2 - F2
```

**IR Retido em Percentual:**
```excel
=IF(E2=0, 0, F2/E2*100)
```

**Rendimento Acumulado:**
```excel
=SUM($E$2:E2)
```

---

## 3. Estrutura de Validação

### 3.1 CPF

**Formato:** XXX.XXX.XXX-XX (com máscara)  
**Dígitos verificadores:** Calculados  
**Validação:** Verifica sequências inválidas

### 3.2 Bancos

**Código:** 0000-9999  
**Fonte:** Banco Central do Brasil  
**Validação:** Lista conhecida

### 3.3 Datas

**Formato:** DD/MM/YYYY  
**Período Alternativo:** YYYY-MM  
**Validação:** Data válida do calendário

### 3.4 Valores Monetários

**Formato:** #,##0.00 (R$)  
**Validação:** Positivos ou zero  
**Arredondamento:** 2 casas decimais

---

## 4. Módulos VBA (Opcional)

### 4.1 Validação de CPF

```vba
Function ValidarCPF(cpf As String) As Boolean
    Dim i As Integer
    Dim soma As Integer
    Dim resto As Integer
    
    cpf = Replace(Replace(Replace(cpf, ".", ""), "-", ""), " ", "")
    
    If Len(cpf) <> 11 Then
        ValidarCPF = False
        Exit Function
    End If
    
    ' Sequências inválidas
    If cpf = String(11, "0") Or cpf = String(11, "1") Or _
       cpf = String(11, "2") Or cpf = String(11, "3") Or _
       cpf = String(11, "4") Or cpf = String(11, "5") Or _
       cpf = String(11, "6") Or cpf = String(11, "7") Or _
       cpf = String(11, "8") Or cpf = String(11, "9") Then
        ValidarCPF = False
        Exit Function
    End If
    
    ' Primeiro dígito
    soma = 0
    For i = 0 To 8
        soma = soma + Val(Mid(cpf, i + 1, 1)) * (10 - i)
    Next i
    
    resto = soma Mod 11
    If resto < 2 Then
        resto = 0
    Else
        resto = 11 - resto
    End If
    
    If Val(Mid(cpf, 10, 1)) <> resto Then
        ValidarCPF = False
        Exit Function
    End If
    
    ' Segundo dígito
    soma = 0
    For i = 0 To 9
        soma = soma + Val(Mid(cpf, i + 1, 1)) * (11 - i)
    Next i
    
    resto = soma Mod 11
    If resto < 2 Then
        resto = 0
    Else
        resto = 11 - resto
    End If
    
    If Val(Mid(cpf, 11, 1)) <> resto Then
        ValidarCPF = False
    Else
        ValidarCPF = True
    End If
End Function
```

### 4.2 Consolidação de Rendimentos

```vba
Sub ConsolidarRendimentos()
    Dim wsRend As Worksheet
    Dim wsResume As Worksheet
    Dim lastRow As Long
    Dim totalRendimento As Double
    Dim totalIR As Double
    
    Set wsRend = ThisWorkbook.Sheets("INFORMES")
    Set wsResume = ThisWorkbook.Sheets("RESUMO")
    
    lastRow = wsRend.Cells(wsRend.Rows.Count, 1).End(xlUp).Row
    
    totalRendimento = 0
    totalIR = 0
    
    For i = 2 To lastRow
        totalRendimento = totalRendimento + wsRend.Cells(i, 5).Value
        totalIR = totalIR + wsRend.Cells(i, 6).Value
    Next i
    
    wsResume.Range("B2").Value = totalRendimento
    wsResume.Range("B3").Value = totalIR
    wsResume.Range("B4").Value = totalRendimento - totalIR
    
    MsgBox "Consolidação concluída!", vbInformation
End Sub
```

---

## 5. Índices de Bancos Brasileiros

| Código | Instituição | Tipo |
|--------|-------------|------|
| 001 | Banco do Brasil | Público |
| 033 | Santander | Privado |
| 041 | Banco do Nordeste | Público |
| 047 | Banco de São Paulo | Privado |
| 074 | Banco J. P. Morgan | Privado |
| 102 | XP Investimentos | Privado |
| 104 | Caixa Econômica | Público |
| 119 | Western Union | Privado |
| 208 | BTG Pactual | Privado |
| 341 | Itaú Unibanco | Privado |
| 422 | Banco Safra | Privado |
| 655 | Banco Votorantim | Privado |
| 745 | Banco Citibank | Privado |
| 756 | Sicoob | Cooperativa |

---

## 6. Formatação e Estilos

### 6.1 Paleta de Cores

```
Cabeçalho:     #1F4E78 (Azul Escuro)
Subheader:     #4472C4 (Azul Médio)
Label:         #D9E1F2 (Azul Claro)
Sucesso:       #C6EFCE (Verde)
Erro:          #FFC7CE (Vermelho)
Atenção:       #FFEB9C (Amarelo)
Fundo:         #FFFFFF (Branco)
```

### 6.2 Tipografia

```
Cabeçalho:     Bold, 12pt
Subheader:     Bold, 11pt
Label:         Bold, 10pt
Dados:         Regular, 10pt
Valor:         Regular, 10pt (Moeda)
```

### 6.3 Formatação de Números

```
Moeda:         #,##0.00
Percentual:    0.00%
Data:          DD/MM/YYYY
Inteiro:       0
```

---

## 7. Performance

### Limites Recomendados

| Métrica | Limite |
|---------|--------|
| Linhas por aba | 10.000 |
| Colunas | 26 |
| Fórmulas aninhadas | 15 |
| Tamanho arquivo | 50MB |

### Otimizações

```vba
' Desabilitar atualizações
Application.ScreenUpdating = False
Application.Calculation = xlCalculationManual

' ... código ...

' Reabilitar
Application.ScreenUpdating = True
Application.Calculation = xlCalculationAutomatic
Application.Calculate
```

---

## 8. Segurança

### 8.1 Proteção

```vba
' Proteger planilha
ws.Protect Password:="sua_senha", _
           DrawingObjects:=True, _
           Contents:=True

' Desproteger
ws.Unprotect Password:="sua_senha"
```

### 8.2 Boas Práticas

✅ Senhas fortes  
✅ Backup regular  
✅ Verificação de dados  
✅ Acesso controlado  

---

## 9. Troubleshooting Técnico

### Macros não funcionam
1. Arquivo → Opções → Central de Confiabilidade
2. Ativar Todas as Macros

### Fórmulas mostram erro
1. Verifique referências de células
2. Confirme formato de dados
3. Recalcule com F9

### Arquivo corrompido
1. Abrir → Procurar arquivo
2. Clicar em "Abrir e Reparar"

---

## 10. Manutenção

### Backup Automático

```vba
Sub CriarBackup()
    Dim pastaBackup As String
    Dim nomeArquivo As String
    
    pastaBackup = ThisWorkbook.Path & "\backups\"
    nomeArquivo = "IC_Financial_" & Format(Now(), "yyyyMMdd") & ".xlsx"
    
    MkDir pastaBackup
    ThisWorkbook.SaveCopyAs pastaBackup & nomeArquivo
End Sub
```

---

**Versão:** 1.0  
**Última atualização:** Setembro 2024
