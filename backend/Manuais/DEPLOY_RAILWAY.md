# Deploy no Railway

Este documento explica como fazer o deploy do backend no Railway.

##  Pré-requisitos

1. Conta no Railway (https://railway.app/)
2. Repositório Git com o código
3. Instância MySQL configurada no Railway

##  Passos para Deploy

### 1. Configurar o Banco de Dados MySQL no Railway

No Railway:
- Crie um novo serviço MySQL
- Anote as credenciais fornecidas (HOST, PORT, DATABASE, USER, PASSWORD)

### 2. Adicionar Variáveis de Ambiente no Railway

No painel do Railway, vá em **Variables** e adicione as seguintes variáveis:

```
DATABASE_URL=jdbc:mysql://<HOST>:<PORT>/<DATABASE>?useSSL=true&allowPublicKeyRetrieval=true&serverTimezone=UTC&useUnicode=true&characterEncoding=UTF-8
MYSQLUSER=<USER>
MYSQLPASSWORD=<PASSWORD>
PORT=8080
CORS_ORIGINS=https://seu-frontend.vercel.app
```

**Importante**: Substitua `<HOST>`, `<PORT>`, `<DATABASE>`, `<USER>`, `<PASSWORD>` pelos valores do seu MySQL.

### 3. Conectar o Repositório Git

No Railway:
1. Clique em **New Project**
2. Selecione **Deploy from GitHub repo**
3. Escolha o repositório `backend-altave`
4. O Railway detectará automaticamente o Dockerfile

### 4. Configurar o Deploy

- O Railway usará o Dockerfile para build
- O serviço será iniciado automaticamente na porta configurada

##  Verificação

Após o deploy, verifique:
1. Se a aplicação está rodando no link fornecido pelo Railway
2. Se o endpoint de health check responde
3. Se as migrações do Flyway foram executadas corretamente

##  Troubleshooting

### Erro: "Cannot find bean"

- Verifique se as variáveis de ambiente estão configuradas corretamente
- Verifique os logs do Railway para mais detalhes

### Erro de conexão com banco de dados

- Verifique se o DATABASE_URL está correto
- Verifique se as credenciais do MySQL estão corretas
- Certifique-se de que o MySQL está acessível na rede do Railway

### Build falha

- Verifique se o Dockerfile está correto
- Verifique se não há dependências faltando
- Verifique os logs do build no Railway

##  Notas Importantes

- O diretório `uploads/` é criado automaticamente no container
- As variáveis de ambiente sobrescrevem as configurações do `application.properties`
- Certifique-se de que o CORS está configurado para aceitar requisições do seu frontend

