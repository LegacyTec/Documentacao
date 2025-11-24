# Variáveis de Ambiente para o Railway

Baseado na sua configuração atual no Railway, você precisa criar/adicionar as seguintes variáveis de ambiente:

##  Variáveis Já Configuradas (já estão no Railway)

Você já tem estas variáveis:
-  `SPRING_DATASOURCE_URL` 
-  `SPRING_DATASOURCE_USERNAME`
-  `SPRING_DATASOURCE_PASSWORD`
-  `SPRING_JPA_DATABASE_PLATFORM`
-  `SPRING_JPA_HIBERNATE_DDL_AUTO`

##  Variáveis Adicionais Necessárias

No painel do Railway, adicione estas variáveis:

### 1. CORS Origins (importante para o frontend)
```
CORS_ORIGINS
```
**Valor**: `https://front-altave.vercel.app,http://localhost:3000,http://localhost:5173`

### 2. Flyway (migrações do banco)
```
SPRING_FLYWAY_ENABLED=true
SPRING_FLYWAY_BASELINE_ON_MIGRATE=true
SPRING_FLYWAY_VALIDATE_ON_MIGRATE=true
```

### 3. Configurações de Upload
```
SPRING_SERVLET_MULTIPART_ENABLED=true
SPRING_SERVLET_MULTIPART_MAX_FILE_SIZE=10MB
SPRING_SERVLET_MULTIPART_MAX_REQUEST_SIZE=10MB
```

##  Resumo das Variáveis

Copie e cole estas no Railway (Settings → Variables):

```env
# CORS para permitir requisições do frontend
CORS_ORIGINS=https://front-altave.vercel.app,http://localhost:3000,http://localhost:5173

# Flyway (migrações de banco de dados)
SPRING_FLYWAY_ENABLED=true
SPRING_FLYWAY_BASELINE_ON_MIGRATE=true
SPRING_FLYWAY_VALIDATE_ON_MIGRATE=true

# Upload de arquivos
SPRING_SERVLET_MULTIPART_ENABLED=true
SPRING_SERVLET_MULTIPART_MAX_FILE_SIZE=10MB
SPRING_SERVLET_MULTIPART_MAX_REQUEST_SIZE=10MB
```

## 🔍 Como Adicionar no Railway

1. Vá no seu projeto no Railway
2. Clique no serviço `backend-altave`
3. Vá em **Variables** (no menu lateral)
4. Clique em **New Variable** para cada uma acima
5. Digite o nome e valor
6. Salve

##  Verificação

Após adicionar as variáveis, o deploy deve funcionar corretamente!

**Nota**: O `application.properties` já foi atualizado para usar as variáveis `SPRING_*` que você já tem configuradas.

