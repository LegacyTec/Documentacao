# Configuração de Email

Configuração do serviço de email utilizando Resend API.

## Procedimento

### 1. Criar conta no Resend
- Acesse: https://resend.com/signup
- Realize o cadastro
- Confirme o email

### 2. Obter API Key
- Acesse: https://resend.com/api-keys
- Clique em "Create API Key"
- Defina nome: "Altave Notificações"
- Copie a chave gerada (formato: `re_xxxxxxxxxxxx`)

### 3. Configurar variável de ambiente
No Railway, adicione a variável:

```
EMAIL_API_KEY=re_xxxxxxxxxxxx
```

## Comportamento

- **Com API Key configurada**: Envia emails via Resend
- **Sem API Key**: Registra nos logs sem enviar

## Limites do plano gratuito

- 3.000 emails/mês
- Plano pago: $20/mês para 50.000 emails

## Modo de teste (sem API Key)

Sem configurar `EMAIL_API_KEY`, o sistema:
- Executa normalmente
- Registra nos logs: "EMAIL_API_KEY não configurada. Email seria enviado para: ..."
- Útil para demonstrações

## Modo produção (com API Key)

Com `EMAIL_API_KEY` configurada:
- Envia emails reais
- Relatórios disponíveis no dashboard Resend
- Emails em português

## Exemplo de log (modo teste)

```
Iniciando verificação de perfis desatualizados...
Perfil desatualizado encontrado: João Silva
EMAIL_API_KEY não configurada. Email seria enviado para: joao@email.com
Assunto: Lembrete: Atualize seu perfil profissional - Altave
Verificação concluída. Total de notificações: 1
```

