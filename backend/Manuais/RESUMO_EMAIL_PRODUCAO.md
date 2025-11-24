# Sistema de Notificações por Email

## Configuração de Produção

## Funcionamento

O sistema verifica **diariamente às 8:00** todos os colaboradores que:
- Nunca atualizaram o perfil (`ultima_atualizacao = null`)
- Não atualizaram há **6 meses** ou mais

Quando encontra um perfil desatualizado, envia um email automaticamente.

## Configuração do Scheduler

Arquivo: `ProfileNotificationScheduler.java`

- Frequência: Diária às 8:00
- Intervalo: 6 meses
- Cron expression: `0 0 8 * * *`

## Mensagem

- Assunto: "Lembrete: Atualize seu perfil profissional - Altave"
- Conteúdo: Notificação de perfil desatualizado (6+ meses)

## Variáveis de Ambiente

No Railway ou localmente:

```env
EMAIL_API_KEY=<sua_api_key_resend>
EMAIL_FROM=<email_verificado>
```

**Produção:** Verificar domínio próprio no Resend e usar email do tipo `notificacoes@altave.com.br`.

## Teste Manual

Endpoint de teste:

```bash
curl http://localhost:8080/api/teste/email?destinatario=<email_teste>
```

## Logs

O sistema registra:
- Quantidade de colaboradores notificados
- Status de cada envio
- Detalhes da API Resend

## Configuração para Produção

1. Verificar domínio no Resend:
   - https://resend.com/domains
   - Adicionar domínio da empresa
   - Configurar registros DNS

2. Atualizar EMAIL_FROM:
   - Usar email do domínio verificado
   - Exemplo: `notificacoes@empresa.com.br`

3. Monitoramento:
   - Verificar logs diários após 8:00
   - Acompanhar métricas de envio

---

**Última atualização:** 24/11/2025

