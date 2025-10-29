# Plataforma Interna de Mapeamento de Competências - Altave

![Image](https://github.com/user-attachments/assets/e433376b-1fb6-4094-8b4d-72e69cb91a27)

> 🚀 **LegacyTech** | 3º Semestre - FATEC SJC | API - Sprint 2

<p align="center">
    <a href="#-sobre-o-projeto">Sobre</a> |
    <a href="#-estrutura-do-projeto">Estrutura</a> |
    <a href="#-como-rodar">Como Rodar</a> |
    <a href="#-product-backlog">Backlog</a> |
    <a href="#-sprints">Sprints</a> |
    <a href="#-padrões-e-convenções">Padrões</a> |
    <a href="#-equipe">Equipe</a>
</p>

---

## 🎯 Sobre o Projeto

Plataforma web para mapeamento de competências internas da Altave. Permite que colaboradores criem perfis profissionais e gestores visualizem habilidades da equipe para formação estratégica de times.

**Problema:** Dificuldade em identificar habilidades específicas entre colaboradores à medida que a empresa cresce.

**Solução:** "LinkedIn interno" com perfis, busca avançada por competências e visão analítica para gestão de talentos.

## 📁 Estrutura do Projeto

```
boards/
├── backend/          # API Spring Boot (Java)
├── frontend/         # Interface React + TypeScript + Vite
├── Documentacao/     # Modelagem de dados, diagramas
├── Manual de Instalação
└── manual do usuario.md
```

### 📦 Repositórios



| Componente | Link | Deploy |
|------------|------|--------|
| **Backend** | [🔗 Repositório](https://github.com/pedromattos11/backend-altave) | Railway |
| **Frontend** | [🔗 Repositório](https://github.com/Edwilsonsj) | Vercel |


### 🛠️ Tecnologias

| Tecnologia | Uso |
|------------|-----|
| **Java 17 + Spring Boot** | API REST, JPA/Hibernate |
| **MySQL** | Banco de dados relacional (3FN) |
| **React 18 + TypeScript** | Interface do usuário |
| **Vite** | Build tool e dev server |
| **Tailwind CSS v4** | Estilização utilitária |

## ▶️ Como Rodar

Consulte o [Manual de Instalação](./Manual%20de%20Instalação.md) para instruções detalhadas de setup local.

**Resumo:**
- **Backend:** `cd backend && mvn spring-boot:run`
- **Frontend:** `cd frontend && npm install && npm run dev`

## 👥 Equipe

| FUNÇÃO | NOME | REDES SOCIAIS | FOTO |
| --- | --- | --- | --- |
| Product OWner | Pedro H. Mattos | [![Linkedin](https://img.shields.io/badge/Linkedin-blue?style=flat-square&logo=Linkedin&logoColor=white)]() [![GitHub](https://img.shields.io/badge/GitHub-111217?style=flat-square&logo=github&logoColor=white)]() |<p align="center"><img src= "https://github.com/user-attachments/assets/8108bdb8-c9d3-473e-9800-da1286cc91e5" alt="Pedro" style="width:60px;height:60px;">
| Scrum Master| Cleber Kirch | [![Linkedin](https://img.shields.io/badge/Linkedin-blue?style=flat-square&logo=Linkedin&logoColor=white)](https://www.linkedin.com/in/cleberkirch/) [![GitHub](https://img.shields.io/badge/GitHub-111217?style=flat-square&logo=github&logoColor=white)](https://github.com/cleberkirch86/) |<p align="center"><img src= "https://github.com/user-attachments/assets/9683e19f-7d59-4273-8a08-8cbddadcf2c8" alt="Cleber" style="width:60px;height:60px;">
| Developer | Ed Wilson | [![Linkedin](https://img.shields.io/badge/Linkedin-blue?style=flat-square&logo=Linkedin&logoColor=white)](https://linkedin.com) [![GitHub](https://img.shields.io/badge/GitHub-111217?style=flat-square&logo=github&logoColor=white)](https://github.com) |<p align="center"><img src= "https://github.com/user-attachments/assets/32812572-8636-43e6-bc31-88844c1fe8c3" alt=" Ed " style="width:60px;height:60px;">
| DBA | Aguinaldo Junior | [![Linkedin](https://img.shields.io/badge/Linkedin-blue?style=flat-square&logo=Linkedin&logoColor=white)](https://www.linkedin.com/in/aguinaldo-cardoso-427270200) [![GitHub](https://img.shields.io/badge/GitHub-111217?style=flat-square&logo=github&logoColor=white)](https://github.com/aguinaldojunior31) |<p align="center"><img src= "https://github.com/user-attachments/assets/29fe9cac-0ca1-410d-a42e-e8b6daf94640" alt="Aguinaldo" style="width:60px;height:60px;">
| Developer | Carlos Eduardo | [![Linkedin](https://img.shields.io/badge/Linkedin-blue?style=flat-square&logo=Linkedin&logoColor=white)](https://www.linkedin.com/in/carlos-eduardo-costa-13146697/) [![GitHub](https://img.shields.io/badge/GitHub-111217?style=flat-square&logo=github&logoColor=white)](https://github.com/carloscosta67) |<p align="center"><img src= "https://github.com/user-attachments/assets/699b1fd1-9f7e-4b9c-8bd0-8ad78f66ee7f" alt="Carlos" style="width:60px;height:60px;">
| DBA | Diego Vitvicki | [![Linkedin](https://img.shields.io/badge/Linkedin-blue?style=flat-square&logo=Linkedin&logoColor=white)](https://www.linkedin.com/in/diegovitvicki/) [![GitHub](https://img.shields.io/badge/GitHub-111217?style=flat-square&logo=github&logoColor=white)](https://github.com/dievit) |<p align="center"><img src= "https://github.com/user-attachments/assets/947ab778-da15-455e-b3b7-bd90b4758dfc" alt="Diego" style="width:60px;height:60px;">





## 📝 Requisitos

<details>
<summary><b>Requisitos Funcionais</b></summary>

- CRUD de perfis profissionais (competências, certificações, experiências)
- Visualização hierárquica (gestores visualizam suas equipes)
- Sistema de tags e avaliações por gestores
- Busca avançada por habilidades
- Relatórios de competências (desejável)
- Notificações de atualização de perfil (desejável)

</details>

<details>
<summary><b>Requisitos Não Funcionais</b></summary>

- Interface minimalista e funcional
- Banco de dados relacional normalizado (3FN)
- 3 tipos de perfis: Diretor, Supervisor, Colaborador
- Massa de dados com 100+ registros
- Documentação completa (modelagem, dicionário de dados)

</details>

## :star: Product Backlog

| Rank | Prioridade | User Story | Estimativa (Story Points) | Sprint |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Alta | Como **Colaborador**, quero **criar e manter meu perfil profissional** para que a empresa tenha visibilidade sobre minhas competências e experiências. | 8 | 1 |
| 2 | Alta | Como **Colaborador**, quero poder **adicionar minhas competências técnicas e soft skills** ao meu perfil para que minhas habilidades sejam facilmente identificadas. | 5 | 1 |
| 3 | Alta | Como **Gestor (Diretor ou Supervisor)**, quero **visualizar os perfis dos colaboradores da minha equipe** para identificar talentos e habilidades específicas. | 8 | 1 |
| 4 | Média | Como **Gestor**, quero poder **adicionar tags e avaliações aos perfis dos meus colaboradores** para complementar as informações e facilitar a busca por talentos. | 8 | 2 |
| 5 | Média | Como **Gestor**, quero **realizar buscas por habilidades específicas** na plataforma para encontrar colaboradores com as competências necessárias para um projeto ou demanda. | 13 | 2 |
| 6 | Média | Como **Administrador do Sistema**, quero **gerenciar os perfis de usuários**, definindo suas permissões (diretor, supervisor, colaborador), para garantir a hierarquia correta na plataforma. | 8 | 2 |
| 7 | Baixa | Como **Gestor**, quero poder **avaliar o meu departamento**, visualizando um resumo das competências existentes, para tomar decisões estratégicas. | 13 | 3 |
| 8 | Baixa | Como **Colaborador**, quero poder **incluir minhas certificações e experiências anteriores** no perfil para fornecer um panorama completo da minha trajetória profissional. | 5 | 3 |
| 9 | Baixa | Como **Administrador do Sistema**, quero **gerar relatórios básicos sobre as competências mais comuns e mais raras** na empresa para apoiar a gestão de talentos. | 8 | 3 |

## :calendar: Sprints

| SPRINTS | PERÍODOS | DESCRIÇÃO |
|---|---|---|
| Sprint 1 | 08/09/2025 à 28/09/2025 | Desenvolvimento do CRUD de perfis, adição de competências e visualização hierárquica pelos gestores. |
| Sprint 2 | 06/10/2025 à 26/10/2025 | Implementação da busca por habilidades, sistema de tags/avaliação para gestores e gerenciamento de perfis pelo admin. |
| Sprint 3 | 03/11/2025 à 23/11/2025 | Desenvolvimento de relatórios, adição de certificações/experiências, testes finais e elaboração da documentação. |

## 📋 Sprint Backlog e Alocação

### 🏃‍♂️ Sprint 1 (Em andamento)
**Período:** 08/09/2025 – 28/09/2025

📄 **[Ver alocação detalhada e burndown → SPRINT_1.md](./SPRINT_1.md)**

**User Stories:**
- 🔄 **US 1:** Criar e manter perfil profissional (8 SP)
- 🔄 **US 2:** Adicionar competências ao perfil (5 SP)
- 🔄 **US 3:** Visualizar perfis da equipe (8 SP)

**Progress:** 25 tarefas | ✅ 7 concluídas | 🔄 7 em progresso | 📋 11 a fazer

---

### 🏃‍♂️ Sprint 2 (Finaliza hoje - 26/10)
**Período:** 06/10/2025 – 26/10/2025

📄 **[Ver alocação detalhada e burndown → SPRINT_2.md](./SPRINT_2.md)**

**User Stories:**
- 🔄 **US 4:** Adicionar tags e avaliações aos perfis (8 SP)
- 🔄 **US 5:** Busca por habilidades específicas (13 SP)
- 🔄 **US 6:** Gerenciar perfis e permissões (8 SP)

**Progress:** 17 issues | ✅ 7 concluídas (41%) | 🔄 5 em progresso | ⚙️ 3 em validação | 📋 2 pendentes

---

### 🏃‍♂️ Sprint 3 (A Fazer)
**Período:** 03/11/2025 – 23/11/2025

- [ ] **US 7:** Como **Gestor**, quero poder **avaliar o meu departamento**.
- [ ] **US 8:** Como **Colaborador**, quero poder **incluir minhas certificações e experiências anteriores**.
- [ ] **US 9:** Como **Administrador**, quero **gerar relatórios básicos sobre as competências**.

---

## 📜 Padrões e Convenções

### Estratégia de Branches (GitFlow Simplificado)

```
main            → Código estável/produção
sprint-N        → Branch de cada sprint (ex: sprint-1, sprint-2)
feature/nome    → Features individuais (ex: feature/busca-avancada)
```

**Fluxo:**
1. Criar branch `feature/nome` a partir de `main`
2. Desenvolver e commitar seguindo o padrão
3. Abrir PR para `main`
4. Após aprovação, merge para `main`

### Padrão de Commits (Conventional Commits)

```
tipo(escopo): descrição curta

[corpo opcional]

[rodapé opcional]
```

**Tipos:**
- `feat`: Nova funcionalidade
- `fix`: Correção de bug
- `docs`: Documentação
- `style`: Formatação, lint
- `refactor`: Refatoração de código
- `test`: Testes
- `chore`: Tarefas de build, configs

**Exemplos:**
```bash
feat(backend): adicionar endpoint de busca por competências
fix(frontend): corrigir validação de formulário de perfil
docs(readme): atualizar instruções de instalação
refactor(backend): extrair lógica do AdminController para AdminService
```

---

🔥 **#GoLegacyTech** 🚀
