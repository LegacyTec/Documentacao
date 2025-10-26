# 📘 Manual de Instalação - Plataforma Altave

Este manual contém todas as instruções necessárias para configurar e executar o projeto completo da Plataforma de Mapeamento de Competências Altave em seu computador.

## 📋 Visão Geral do Projeto

A Plataforma Altave é composta por dois repositórios principais:
- **Frontend**: React + TypeScript + Vite
- **Backend**: Java 17 + Spring Boot 3.5.5

## 🛠️ Pré-requisitos

Antes de começar, você precisará ter as seguintes ferramentas instaladas em sua máquina:

### Software Obrigatório

#### Para o Backend:
- **Java JDK 17** ou superior
  - Windows: [Download do Adoptium](https://adoptium.net/pt-BR/temurin/releases/?version=17)
  - Alternativa: Usar [SDKMAN!](https://sdkman.io/) para gerenciar versões do Java
- **Maven 3.6+** (geralmente já vem com as IDEs)
  - [Download do Maven](https://maven.apache.org/download.cgi)
- **Git**
  - [Download do Git](https://git-scm.com/downloads)

#### Para o Frontend:
- **Node.js 18+** (recomendado: LTS mais recente)
  - [Download do Node.js](https://nodejs.org/)
- **npm** (já vem com o Node.js) ou **yarn**

### Banco de Dados (Opcional para Desenvolvimento)
- **MySQL 8.0+** (opcional - somente para ambiente de produção)
  - Para desenvolvimento local, o projeto usa **H2 Database** (banco em memória)
  - [Download do MySQL](https://dev.mysql.com/downloads/mysql/)

### IDEs Recomendadas
- **IntelliJ IDEA** (recomendado para Java)
- **Visual Studio Code** (funciona bem para ambos)
- **Eclipse** ou **Cursor** (alternativas)

---

## 🚀 Instalação e Configuração

### Passo 1: Clonar os Repositórios

Crie uma pasta para o projeto e clone os dois repositórios:

```bash
# Criar pasta do projeto
mkdir altave-project
cd altave-project

# Clonar o frontend
git clone https://github.com/EdWilsonsj/front-altave.git

# Clonar o backend
git clone https://github.com/pedromattos11/backend-altave.git
```

Sua estrutura de pastas deve ficar assim:
```
altave-project/
├── front-altave/
└── backend-altave/
```

---

## 🔧 Configuração do Backend

### Passo 2: Acessar a pasta do backend

```bash
cd backend-altave
```

### Passo 3: Verificar a instalação do Java

Verifique se o Java 17 está instalado corretamente:

```bash
java -version
```

Você deve ver algo como:
```
openjdk version "17.0.x" ...
```

### Passo 4: Configuração do Banco de Dados

**Para Desenvolvimento Local (Recomendado):**

O projeto já está configurado para usar o **H2 Database** (banco em memória) em ambiente local. Não é necessária nenhuma configuração adicional.

**Para Produção ou MySQL:**

Se você deseja usar MySQL, crie um arquivo de configuração:

1. Crie o arquivo `application-local.properties` em `src/main/resources/`:

```properties
# MySQL Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/altave_db?createDatabaseIfNotExist=true
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA Configuration
spring.jpa.hibernate.ddl-auto=validate
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

# Flyway Configuration
spring.flyway.enabled=true
spring.flyway.baseline-on-migrate=true
```

> ⚠️ **Importante**: O arquivo `application-local.properties` é ignorado pelo Git por segurança.

### Passo 5: Compilar e executar o backend

#### Opção A: Usando o Maven Wrapper (Recomendado)

**No Windows (PowerShell):**
```powershell
.\mvnw.cmd spring-boot:run
```

**No Windows (CMD):**
```cmd
mvnw.cmd spring-boot:run
```

**No Linux/Mac:**
```bash
./mvnw spring-boot:run
```

#### Opção B: Usando Maven instalado

```bash
mvn spring-boot:run
```

#### Opção C: Pela IDE

1. Abra o projeto na sua IDE (IntelliJ, Eclipse, VS Code)
2. Localize a classe `BackendAltaveApplication.java`
3. Clique com o botão direito e selecione **"Run"** ou **"Debug"**

### Passo 6: Verificar se o backend está funcionando

Após iniciar, você deve ver no console:
```
Started BackendAltaveApplication in X.XXX seconds
```

O backend estará disponível em: **http://localhost:8080**

Para testar, acesse no navegador:
```
http://localhost:8080/api/health
```
(Ou qualquer endpoint configurado no projeto)

---

## 💻 Configuração do Frontend

### Passo 7: Acessar a pasta do frontend

Abra um **novo terminal** (mantenha o backend rodando no outro terminal):

```bash
cd front-altave
```

### Passo 8: Instalar as dependências

```bash
npm install
```

Ou se você usar Yarn:
```bash
yarn install
```

Este processo pode levar alguns minutos dependendo da sua conexão com a internet.

### Passo 9: Configurar variáveis de ambiente (se necessário)

O projeto já está configurado para se conectar ao backend em `http://localhost:8080` através do proxy do Vite.

Se precisar customizar, crie um arquivo `.env.local` na raiz do projeto frontend:

```env
VITE_API_URL=http://localhost:8080
```

> ⚠️ **Importante**: Arquivos `.env*` são ignorados pelo Git por segurança.

### Passo 10: Executar o frontend

```bash
npm run dev
```

Ou com Yarn:
```bash
yarn dev
```

O frontend estará disponível em: **http://localhost:5173**

Você deve ver no console algo como:
```
  VITE v7.x.x  ready in XXX ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

### Passo 11: Acessar a aplicação

Abra seu navegador e acesse:
```
http://localhost:5173
```

---

## ✅ Verificação da Instalação

Se tudo estiver funcionando corretamente, você deve ter:

- ✅ Backend rodando em `http://localhost:8080`
- ✅ Frontend rodando em `http://localhost:5173`
- ✅ Frontend conseguindo se comunicar com o backend via proxy
- ✅ Interface da aplicação carregando no navegador

---

## 🔍 Solução de Problemas Comuns

### Backend não inicia

**Erro: "Java version not found"**
- Solução: Instale o Java 17 e configure a variável de ambiente `JAVA_HOME`

**Erro: "Port 8080 already in use"**
- Solução: Encerre o processo que está usando a porta 8080 ou mude a porta no `application.properties`:
```properties
server.port=8081
```

**Erro: "Could not find or load main class"**
- Solução: Execute `mvn clean install` para recompilar o projeto

### Frontend não inicia

**Erro: "node: command not found"**
- Solução: Instale o Node.js

**Erro: "Cannot find module"**
- Solução: Delete a pasta `node_modules` e o arquivo `package-lock.json`, depois execute `npm install` novamente

**Erro: "Port 5173 already in use"**
- Solução: Encerre o processo que está usando a porta ou o Vite automaticamente tentará outra porta

### Problemas de conexão Frontend ↔ Backend

**Erro: "Network Error" ou "CORS Error"**
- Verifique se o backend está rodando em `http://localhost:8080`
- Verifique se o proxy está configurado corretamente no `vite.config.ts`

---

## 📦 Build para Produção

### Backend

Para gerar o arquivo JAR executável:

```bash
mvn clean package
```

O arquivo será gerado em `target/backend-altave-0.0.1-SNAPSHOT.jar`

Para executar:
```bash
java -jar target/backend-altave-0.0.1-SNAPSHOT.jar
```

### Frontend

Para gerar os arquivos estáticos otimizados:

```bash
npm run build
```

Os arquivos serão gerados na pasta `dist/`

Para testar a build de produção localmente:
```bash
npm run preview
```

---

## 🛠️ Scripts Úteis

### Backend
```bash
# Compilar o projeto
mvn compile

# Executar testes
mvn test

# Limpar e recompilar
mvn clean install

# Executar em modo debug
mvn spring-boot:run -Dspring-boot.run.jvmArguments="-Xdebug"
```

### Frontend
```bash
# Modo desenvolvimento
npm run dev

# Build de produção
npm run build

# Preview da build
npm run preview

# Lint (verificar código)
npm run lint
```

---

## 📚 Tecnologias Utilizadas

### Backend
- Java 17
- Spring Boot 3.5.5
- Spring Data JPA
- Spring Security
- Maven
- MySQL (produção)
- H2 Database (desenvolvimento)
- Flyway (migrações de banco de dados)

### Frontend
- React 19
- TypeScript 5.8
- Vite 7
- TailwindCSS 4
- React Router DOM 7
- Radix UI
- Recharts
- Lucide Icons

---

## 📞 Suporte

Para dúvidas ou problemas:
- Frontend: [https://github.com/EdWilsonsj/front-altave/issues](https://github.com/EdWilsonsj/front-altave/issues)
- Backend: [https://github.com/pedromattos11/backend-altave/issues](https://github.com/pedromattos11/backend-altave/issues)

---

## 📝 Notas Importantes

1. **Nunca commite** arquivos de configuração com senhas ou chaves de API
2. Use o banco **H2** para desenvolvimento local (mais rápido e simples)
3. Configure o **MySQL** apenas quando for necessário testar em ambiente similar ao de produção
4. Mantenha sempre o **backend rodando** antes de iniciar o frontend
5. As migrations do Flyway criarão automaticamente as tabelas necessárias no banco

---

## 🎉 Pronto!

Agora você tem o ambiente completo da Plataforma Altave rodando em sua máquina. Bom desenvolvimento! 🚀

