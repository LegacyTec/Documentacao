# Teste de Email Local

## Configuração

Configuração local em `application-local.properties`:

```properties
email.api.key=${EMAIL_API_KEY}
email.from=${EMAIL_FROM}
```

## Procedimento de teste

```bash
cd backend-altave
./mvnw spring-boot:run -Dspring-boot.run.profiles=local
```

## Comportamento esperado

1. Sistema inicia
2. Aguardar até 2 minutos (scheduler)
3. Logs exibirão:
   ```
   Iniciando verificação de perfis desatualizados...
   Email enviado com sucesso para: colaborador@example.com
   ```

## Configuração Railway

Variáveis necessárias:
```
EMAIL_API_KEY=<sua_api_key_resend>
EMAIL_FROM=<seu_email_verificado>
```

