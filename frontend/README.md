# Frontend - Plataforma de Mapeamento de Competências Altave

![React](https://img.shields.io/badge/React-18-blue?logo=react&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-purple?logo=vite&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-v4-38bdf8?logo=tailwind-css&logoColor=white)
![Status](https://img.shields.io/badge/status-Em_Desenvolvimento-yellow)

Interface de usuário da plataforma de mapeamento de competências internas da Altave. Permite que colaboradores gerenciem perfis profissionais e gestores visualizem habilidades da equipe.

## 🎯 Sobre o Projeto

Frontend desenvolvido com React 18, TypeScript e Vite, focado em performance e experiência do usuário. A interface é minimalista, responsiva e totalmente tipada.

**Principais funcionalidades:**
- ✅ CRUD de perfis profissionais
- ✅ Gerenciamento de competências (hard e soft skills)
- 🔄 Visualização hierárquica (gestores/equipe)
- 📋 Busca avançada por habilidades
- 📋 Dashboard analítico para gestores

## 🛠️ Stack Tecnológico

| Tecnologia | Versão | Propósito |
|------------|--------|----------|
| **React** | 18.3 | Biblioteca de UI baseada em componentes |
| **TypeScript** | 5.6 | Tipagem estática e autocompletar |
| **Vite** | 7.0 | Build tool ultra-rápido com HMR |
| **Tailwind CSS** | v4 | Estilização utilitária |
| **Axios** | - | Cliente HTTP para API |
| **React Router** | - | Roteamento SPA |
| **ESLint** | - | Linting e boas práticas |

## 📋 Pré-requisitos

Antes de começar, você precisa ter instalado:

- [Node.js](https://nodejs.org/) (v18 ou superior)
- [npm](https://www.npmjs.com/) ou [pnpm](https://pnpm.io/)
- [Git](https://git-scm.com/)

## 🚀 Como Rodar

### 1. Clone o repositório
```bash
git clone https://github.com/EdWilsonsj/front-altave.git
cd front-altave
```

### 2. Instale as dependências
```bash
npm install
# ou
pnpm install
```

### 3. Configure as variáveis de ambiente
Crie um arquivo `.env` na raiz do projeto:
```env
VITE_API_URL=http://localhost:8080
```

### 4. Inicie o servidor de desenvolvimento
```bash
npm run dev
# ou
pnpm dev
```

O app estará disponível em `http://localhost:5173`

### 5. Build para produção
```bash
npm run build
npm run preview  # Preview do build
```

## 📁 Estrutura do Projeto

```
src/
├── components/       # Componentes reutilizáveis
│   ├── dashboard/    # Componentes do dashboard
│   └── layout/       # Header, Footer, Sidebar
├── contexts/         # Context API (Theme, Auth)
├── pages/            # Páginas principais
│   ├── PaginaLogin.tsx
│   ├── PaginaDashboard.tsx
│   └── PaginaPerfil.tsx
├── services/         # APIs e serviços externos
├── types/            # Tipos TypeScript
├── App.tsx           # Componente raiz
└── main.tsx          # Entry point
```

## 📝 Scripts Disponíveis

```bash
npm run dev        # Inicia servidor de desenvolvimento
npm run build      # Build para produção
npm run preview    # Preview do build local
npm run lint       # Executa ESLint
```

## 🎯 Padrões de Código

Veja [CODING_GUIDE.md](./CODING_GUIDE.md) para padrões detalhados.

**Resumo:**
- Componentes funcionais com hooks
- TypeScript estrito (sem `any`)
- Tailwind CSS para estilização
- Convenção de nomes: PascalCase para componentes, camelCase para funções

## 🔗 Links Úteis

- [🏠 Repositório Principal](https://github.com/LegacyTec/boards)
- [🔌 Backend API](https://github.com/pedromattos11/backend-altave)
- [🚀 Deploy (Vercel)](https://seu-app.vercel.app)

---

**Desenvolvido por LegacyTech** | FATEC SJC - 3º Semestre
