# 🐛 Troubleshooting & FAQ

Soluções rápidas para problemas comuns.

---

## 📊 Problemas com Excel

### Arquivo abre mas está lento

**Problema:** Ao abrir o arquivo, o Excel demora muito  
**Causa:** Muitos dados ou fórmulas complexas

**Solução:**
1. Remova dados com > 12 meses
2. Desative cálculo automático:
   - Fórmulas → Opções de Cálculo → Manual
3. Feche outras abas abertas
4. Reinicie o Excel
5. Se persistir, divida em arquivos (por ano)

---

### Macros não funcionam

**Problema:** Clico botão mas nada acontece  
**Causa:** Macros não estão habilitadas

**Solução:**
1. Arquivo → Opções → Central de Confiabilidade
2. Clique em "Configurações da Central de Confiabilidade"
3. Configurações de Macros
4. Selecione "Ativar todas as macros"
5. OK → OK
6. Reinicie o Excel

**Alternativa (Security Bypass):**
- Se sua empresa bloqueia macros:
  1. Clique em "Habilitar Conteúdo" quando aparecer
  2. Se não aparecer, não há macros necessárias

---

### Fórmulas mostram erro (#REF!, #VALUE!, #NAME!)

**Problema:** Células com erro ao invés de valores  
**Causa:** Referência de célula quebrada ou tipo de dado errado

**Solução:**
1. Clique na célula com erro
2. Verifique a fórmula (barra de fórmulas)
3. Corrija referências (ex: A1 ao invés de A)
4. Certifique-se do tipo de dado (texto vs número)
5. Pressione F9 para recalcular
6. Pressione Enter

**#REF! Error:**
```
Causa: Você deletou uma célula referenciada
Solução: Use Ctrl+Z para desfazer
```

**#VALUE! Error:**
```
Causa: Tipo de dado errado na fórmula
Solução: Digite número onde fórmula espera número
```

---

### Dados duplicados aparecem

**Problema:** Mesmas informações em múltiplas linhas  
**Causa:** Cópia acidental ou paste duplicado

**Solução:**
1. Selecione dados
2. Dados → Remover Duplicatas
3. Selecione colunas a verificar
4. OK

---

### Arquivo está muito grande (> 50MB)

**Problema:** Arquivo lento para abrir/salvar  
**Causa:** Muitos dados ou formatação excessiva

**Solução:**
1. **Limpar formatação:**
   - Selecione tudo (Ctrl+A)
   - Início → Limpar → Limpar Tudo

2. **Remover dados antigos:**
   - Deletar linhas com dados > 12 meses

3. **Compactar:**
   - Salvar Como → Formato Excel reduzido

4. **Dividir:**
   - Crie arquivo separado por ano

---

## 🔓 Problemas com Dados

### CPF não valida

**Problema:** Mensagem "CPF inválido" mas CPF está correto  
**Causa:** Formato errado

**Solução:**
1. Formato correto: `123.456.789-10`
2. Remova espaços em branco
3. Use apenas números e símbolos corretos
4. Verifique dígitos verificadores

**Verifique CPF Online:**
- [Validador CPF](https://www.4devs.com.br/validar_cpf)

---

### Banco não reconhecido

**Problema:** "Banco não encontrado na lista"  
**Causa:** Código errado ou banco não existe na tabela

**Solução:**
1. Verifique código do banco:
   - Vá em TABELAS → veja lista oficial
2. Se banco não está lá:
   - Adicione manualmente em TABELAS
   - Use código oficial do Banco Central
3. Use nome da instituição se não souber código

---

### Valores aparecem como texto

**Problema:** Números aparecem alinhados à esquerda  
**Causa:** Dados foram digitados como texto

**Solução:**
1. Selecione coluna com problema
2. Dados → Texto em Colunas
3. Próximo → Próximo → Avançado
4. Formato: Geral
5. Concluir

---

### Datas aparecem como números

**Problema:** Vejo 45000 ao invés de 10/01/2024  
**Causa:** Formatação de data não aplicada

**Solução:**
1. Selecione células
2. Clique direito → Formatar Células
3. Número → Data
4. Escolha formato desejado
5. OK

---

## 💾 Problemas com Backup/Salvamento

### Arquivo não salva

**Problema:** Clico Ctrl+S mas nada acontece  
**Causa:** Permissões de pasta ou arquivo protegido

**Solução:**
1. **Verifique permissões:**
   - Clique direito na pasta → Propriedades → Segurança
   - Certifique-se que tem acesso de escrita

2. **Se arquivo está protegido:**
   - Arquivo → Info → Proteger Pasta de Trabalho → Desproteger
   - Digite senha se solicitado

3. **Salvar em outro local:**
   - Arquivo → Salvar Como → Escolha nova pasta

---

### Arquivo corrompido

**Problema:** "Arquivo não pode ser aberto"  
**Causa:** Arquivo danificado durante salvamento

**Solução:**
1. **Reparar com Excel:**
   - Arquivo → Abrir → Procurar arquivo
   - Clique em dropdown ao lado de Abrir
   - Selecione "Abrir e Reparar"

2. **Se não funcionar, recupere backup:**
   - Procure em Backups/
   - Use versão anterior

3. **Última opção:**
   - Verifique Histórico de Arquivos (Windows)
   - Ou use Time Machine (Mac)

---

### Perdi dados acidentalmente

**Problema:** Deletei dados e não tenho backup  
**Causa:** Falta de backup automático

**Solução:**
1. **Imediato - Desfazer:**
   - Pressione Ctrl+Z repetidamente
   - Volte até antes de deletar

2. **Se fecha o arquivo:**
   - Não salve
   - Procure backup automático:
     - Windows: Versões Anteriores
     - Mac: Time Machine

3. **Recuperar arquivo:**
   - Windows: Arquivo → Info → Versões
   - Procure versão anterior

4. **Prevenção futura:**
   - Ative Autosave
   - Arquivo → Opções → Salvar
   - ✅ AutoRecover a cada X minutos

---

## 🔐 Problemas de Segurança

### Senha esquecida

**Problema:** Planilha está protegida e esqueci a senha  
**Causa:** Proteção de planilha ativa

**Solução:**
Infelizmente, Excel não permite recuperar senha. Opções:
1. Contate criador original
2. Restaure backup sem proteção
3. Use versão de software desprotegida (último recurso)

**Prevenção:** Guarde senhas em local seguro (password manager)

---

### Arquivo aberto por outra pessoa

**Problema:** "Arquivo aberto por [usuário]"  
**Causa:** Múltiplos usuários editam mesmo arquivo

**Solução:**
1. **Opção 1 - Esperar:**
   - Aguarde outra pessoa fechar

2. **Opção 2 - Abrir Leitura:**
   - Clique "Abrir como Leitura"
   - Faça anotações
   - Peça para outro salvar e fechar

3. **Opção 3 - OneDrive/SharePoint:**
   - Mova arquivo para cloud (recomendado)
   - Permite edição simultânea

---

## 🌐 Problemas de Compartilhamento

### Não consigo abrir arquivo de outra pessoa

**Problema:** Erro ao tentar abrir arquivo .xlsx  
**Causa:** Versão diferente ou arquivo corrompido

**Solução:**
1. **Verificar versão Excel:**
   - Arquivo requer Excel 2016+
   - Você tem versão menor?
   - Atualize Excel

2. **Testar com backup:**
   - Peça nova cópia do arquivo
   - Pode estar corrompido na transferência

3. **Converter formato:**
   - Peça arquivo em .xls (mais compatível)
   - Converter: Arquivo → Salvar Como → Excel 97-2003

---

### Fórmulas desaparecem ao compartilhar

**Problema:** Envio arquivo com fórmulas, chega sem elas  
**Causa:** Antivírus ou software de segurança removem macros

**Solução:**
1. **Salvar sem macros:**
   - Arquivo → Salvar Como → Formato: Excel (.xlsx)
   - Remove VBA mas mantém fórmulas

2. **Adicionar com segurança:**
   - Recipient ativa macros em seu computador
   - Copia fórmulas

3. **Compartilhar com segurança:**
   - Use OneDrive/Google Drive
   - Arquivo fica intacto
   - Melhor para colaboração

---

## 📱 Problemas com Google Sheets

### Convertido para Google Sheets não funciona 100%

**Problema:** Fórmulas e formatação quebram  
**Causa:** Diferenças entre Excel e Google Sheets

**Solução:**
1. **Manter no Excel:**
   - Recomendado para máxima compatibilidade
   - Google Sheets é só para visualização

2. **Converter com cuidado:**
   - Valide todas as fórmulas
   - Teste cálculos
   - Reapply formatação

3. **Usar offline:**
   - Baixe arquivo como .xlsx
   - Edite no Excel local

---

## ⚡ Problemas de Performance

### Excel travando

**Problema:** Aplicação não responde/trava  
**Causa:** Muitas fórmulas complexas ou dados

**Solução:**
1. **Feche programas:**
   - Libere memória RAM
   - Feche navegador com muitas abas

2. **Desabilite cálculo automático:**
   - Fórmulas → Opções de Cálculo → Manual
   - Calcule quando necessário (Shift+Ctrl+F9)

3. **Divida arquivo:**
   - 10.000+ linhas? Divida por ano
   - Mantenha 1-2 anos ativos

4. **Limpe formatação:**
   - Remova cores e fontes desnecessárias

---

### Salvar arquivo demora muito

**Problema:** Leva 1+ minuto para salvar  
**Causa:** Arquivo grande com muitas fórmulas

**Solução:**
1. **Compactar:**
   - Remova dados com > 12 meses
   - Arquivo → Salvar Como → Excel Compactado

2. **Reduzir fórmulas:**
   - Consolide cálculos
   - Use SUMPRODUCT ao invés de múltiplas somas

3. **Limpar histórico:**
   - Edit → Limpar Histórico de Edição
   - Salvar

---

## ❓ FAQ - Perguntas Frequentes

### P: Posso usar em Mac?
**R:** Sim! Excel 2016+ no Mac funciona perfeitamente. VBA tem limitações mas fórmulas funcionam.

### P: Funciona em Excel Online (365)?
**R:** Sim, mas com limitações (sem VBA, sem formatação avançada).

### P: Quantos dados posso adicionar?
**R:** ~10.000 linhas funcionam bem. Acima disso, considere dividir arquivo.

### P: Preciso de internet?
**R:** Não! Arquivo é local. Internet é apenas para compartilhar via OneDrive.

### P: Como fazer backup automático?
**R:** Arquivo → Opções → Salvar → AutoRecover a cada 5 minutos.

### P: Posso enviar por email?
**R:** Sim, mas cuidado com tamanho. Compacte se > 25MB.

### P: O que fazer se Excel crashear?
**R:** Excel salva recovery file. Procure em Arquivo → Recuperar.

### P: Posso usar em smartphone?
**R:** Excel mobile tem versão, mas recomendo desktop para melhor experiência.

### P: Como importar de CSV?
**R:** Arquivo → Abrir → Selecione arquivo.csv → Escolha delimitador.

### P: Posso proteger com senha?
**R:** Sim! Estrutura → Proteger Planilha → Digite senha.

### P: Excel consome muita memória?
**R:** Normal 50-100MB. Se usar > 500MB, feche e reabra.

---

## 📞 Ainda Precisa de Ajuda?

- ❌ Não encontrou solução acima?
- 📧 Email: [seu-email]
- 💬 GitHub Issues: [abra uma issue]
- 📱 WhatsApp: [seu-número]

---

**Última Atualização:** Setembro 2024  
**Versão:** 1.0

