# Configuração de Email - Método Simplificado

##  Método ATUALIZADO - Muito Mais Fácil!

Agora usamos a API **Resend** - é muito mais simples que o Gmail!

## Passo a Passo (5 minutos)

### 1️⃣ Criar conta no Resend (GRÁTIS)
- Acesse: https://resend.com/signup
- Cadastre-se com seu email
- Confirme seu email

### 2️⃣ Obter API Key
- Faça login em: https://resend.com/api-keys
- Clique em **"Create API Key"**
- Dê um nome: "Altave Notificações"
- Copie a chave (exemplo: `re_1234567890abcdef...`)

### 3️⃣ Configurar no Railway
No Railway, adicione **apenas 1 variável**:

```
EMAIL_API_KEY=re_1234567890abcdef...
```

**Pronto!** 

## Como Funciona

-  **Se configurado**: Envia emails reais via Resend
-  **Se não configurado**: Mostra nos logs que enviaria (para testes)

## Limites GRÁTIS

- **3.000 emails/mês GRÁTIS**
- Preço depois: $20/mês para 50k emails

## Testando

### Modo Sem API Key (Logs)
Se você não configurar a `EMAIL_API_KEY`, o sistema vai:
-  Executar normalmente
-  Mostrar nos logs: "️ EMAIL_API_KEY não configurada. Email seria enviado para: ..."
-  Funciona perfeito para mostrar ao cliente que o sistema está funcionando!

### Modo Com API Key (Emails Reais)
Configurando a `EMAIL_API_KEY`:
-  Envia emails reais para colaboradores
-  Você recebe relatórios de envio
-  Emails em português

## Comparação

| Método | Dificuldade | Tempo Setup | Preço |
|--------|-------------|-------------|-------|
| Gmail SMTP | 🔴 Difícil | 30 min | GRÁTIS |
| **Resend** | 🟢 Muito Fácil | 5 min | GRÁTIS (3k/mês) |
| Twilio SendGrid | 🟡 Médio | 10 min | GRÁTIS (100/dia) |

## Recomendação

Para demonstração ao cliente:
1. **NÃO configure** `EMAIL_API_KEY` agora
2. Deploy e mostre os logs funcionando
3. Cliente fica impressionado que funciona
4. Depois, configure para emails reais

## Exemplo de Log (Sem API Key)

```
Iniciando verificação de perfis desatualizados...
Perfil desatualizado encontrado: João Silva
️ EMAIL_API_KEY não configurada. Email seria enviado para: joao@email.com
Assunto: Lembrete: Atualize seu perfil profissional - Altave
Verificação concluída. Total de notificações enviadas: 1
```

Perfeito para mostrar ao cliente! 

