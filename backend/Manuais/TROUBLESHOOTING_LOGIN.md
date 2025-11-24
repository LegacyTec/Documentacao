#  Troubleshooting - Problema de Login

##  Correções Aplicadas

1.  Adicionado V12 (placeholder) - corrigiu sequência Flyway
2.  Adicionado V15 com usuário de teste
3.  Corrigido V3 para usar email correto: `pedro@altave.com`
4.  Alterado V1 para incluir coluna `role`

## 🔍 Como Testar o Login

### 1. Verificar se o backend está rodando

Acesse a URL do Railway (exemplo: `https://backend-altave-production.up.railway.app`)

Você deve ver alguma resposta do backend (pode ser erro 404, mas significa que está funcionando).

### 2. Testar o endpoint de login diretamente

Use o Postman, cURL ou qualquer cliente HTTP:

```bash
curl -X POST https://SEU-BACKEND.railway.app/api/usuario/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "pedro@altave.com",
    "password": "123456"
  }'
```

**Resposta esperada** (200 OK):
```json
{
  "id": 1,
  "nomeCompleto": "Pedro Mattos",
  "email": "pedro@altave.com",
  "role": "ADMIN"
}
```

### 3. Verificar se o colaborador existe

```bash
curl https://SEU-BACKEND.railway.app/api/colaborador/by-email/pedro@altave.com
```

**Resposta esperada** (200 OK):
```json
{
  "id": 1,
  "nome": "Pedro Mattos",
  "email": "pedro@altave.com",
  ...
}
```

### 4. Configurar a variável no Vercel (Frontend)

No painel do Vercel:

1. Vá em **Settings** → **Environment Variables**
2. Adicione:
   - **Name**: `VITE_API_URL`
   - **Value**: `https://SEU-BACKEND.railway.app`
3. Redeploy

## 🐛 Problemas Comuns

### Erro: "Cannot GET /"
- O backend está ativo mas não tem rota raiz configurada
- Isso é normal, o importante é que `/api/usuario/login` funcione

### Erro 401 Unauthorized
- Credenciais incorretas
- Verifique se o usuário foi criado no banco
- Email: `pedro@altave.com` | Senha: `123456`

### Erro 404 Not Found
- O endpoint não existe
- Verifique se o serviço está deployado
- Verifique a URL do backend no Railway

### Erro de CORS
- Verifique se a URL do backend está no `CorsConfig.java`
- Adicione a URL do Railway no padrão correto:
```java
.allowedOriginPatterns(
    "https://*.railway.app",
    "https://SEU-FRONTEND.vercel.app"
)
```

### "Perfil de colaborador não encontrado"
- O colaborador não existe com o email `pedro@altave.com`
- Execute as migrations novamente
- Verifique se o email está correto em V3 e V15

##  Checklist de Verificação

- [ ] Backend deployado no Railway
- [ ] Variável `VITE_API_URL` configurada no Vercel
- [ ] Migrations executadas (V1, V2, V3, ..., V15)
- [ ] Usuário criado: `pedro@altave.com` / `123456`
- [ ] Colaborador criado com mesmo email
- [ ] CORS configurado corretamente
- [ ] Frontend faz redeploy após configurar variável

## 🔑 Credenciais de Teste

- **Email**: `pedro@altave.com`
- **Senha**: `123456`
- **Role**: `ADMIN`

## 📞 Logs do Railway

Para verificar os logs do backend:

1. No Railway, clique no seu serviço
2. Vá em **Deployments**
3. Clique no último deploy
4. Veja os logs

Procure por:
- `Starting BackendAltaveApplication`
- `Flyway schema history table`
- Qualquer erro relacionado a autenticação

##  Próximos Passos

Se ainda não funcionar:

1. Verifique os logs do Railway
2. Teste o endpoint de login diretamente com cURL
3. Verifique se o frontend está usando a variável `VITE_API_URL` corretamente
4. Abra o DevTools (F12) no navegador e veja os erros no Console
5. Verifique a aba Network para ver as requisições HTTP

