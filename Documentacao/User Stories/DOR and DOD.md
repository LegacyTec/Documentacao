# 📌 Definition of Ready (DOR) e Definition of Done (DOD)

Critérios aplicados a cada tela/fluxo do projeto.

## 1. Tela de Login

### 🔄 DOR (Pronto para iniciar)
- [ ] Wireframe/protótipo disponível no Figma
- [ ] Campos definidos (e-mail/usuário, senha)
- [ ] Regras de autenticação validadas
- [ ] Definição de mensagens de erro
- [ ] API de autenticação disponível

### ✅ DOD (Concluído quando)
- [ ] Implementada conforme design (light/dark)
- [ ] Validação de campos obrigatória (e-mail válido, senha não vazia)
- [ ] Integração com backend funcionando
- [ ] Mensagens de erro exibidas corretamente
- [ ] Testes unitários + integração realizados
- [ ] Responsividade validada e deploy aprovado

---

## 2. Tela de Primeiro Cadastro

### 🔄 DOR (Pronto para iniciar)
- [ ] Wireframe/protótipo pronto
- [ ] Campos definidos (nome, e-mail, senha, confirmar senha)
- [ ] Regras de senha definidas
- [ ] Endpoint de cadastro disponível
- [ ] Fluxo definido (redireciona para login)

### ✅ DOD (Concluído quando)
- [ ] Formulário implementado conforme design
- [ ] Validações aplicadas (senhas iguais, e-mail válido, campos obrigatórios)
- [ ] Integração com backend concluída
- [ ] Mensagens de sucesso/erro exibidas
- [ ] Testado em navegadores principais e homologado

---

## 3. Fluxo "Esqueci minha Senha"

### 🔄 DOR (Pronto para iniciar)
- [ ] Wireframe disponível
- [ ] Regras de recuperação definidas (envio de e-mail, token)
- [ ] API de recuperação disponível
- [ ] Template de e-mail aprovado

### ✅ DOD (Concluído quando)
- [ ] Tela com campo de e-mail implementada
- [ ] Envio de e-mail funcionando
- [ ] Fluxo de redefinição concluído
- [ ] Mensagens adequadas exibidas
- [ ] Responsividade validada e cenários testados

---

## 4. Primeira Entrada na Plataforma

### 🔄 DOR (Pronto para iniciar)
- [ ] Wireframe definido (onboarding, boas-vindas)
- [ ] Regras de negócio validadas
- [ ] Dependência do backend confirmada

### ✅ DOD (Concluído quando)
- [ ] Fluxo implementado conforme protótipo
- [ ] Funciona apenas na primeira entrada (lógica validada)
- [ ] Responsividade ok, testado com contas novas/existentes

---

## 5. Tela Colaborador inserir Competências e Experiências

### 🔄 DOR (Pronto para iniciar)
- [ ] Protótipo pronto
- [ ] Campos definidos (competência, nível, experiência)
- [ ] API/backend disponível
- [ ] Regras de negócio definidas
- [ ] Estrutura de dados validada

### ✅ DOD (Concluído quando)
- [ ] Formulário implementado e funcional
- [ ] CRUD completo (inserir, editar, excluir)
- [ ] Integração funcionando
- [ ] Validações aplicadas e mensagens adequadas
- [ ] Responsividade testada e homologado

---

## 6. Modo de Cores Light-Dark

### 🔄 DOR (Pronto para iniciar)
- [ ] Design system definido para ambos modos
- [ ] Cores e contrastes aprovados
- [ ] Componentes adaptáveis criados

### ✅ DOD (Concluído quando)
- [ ] Toggle implementado em todas as telas
- [ ] Preferência do usuário salva
- [ ] Transição suave entre modos
- [ ] Acessibilidade validada (contraste adequado)
- [ ] Funciona em todos os navegadores

---

## 7. Tela ADM - Visualizar Perfis dos Colaboradores

### 🔄 DOR (Pronto para iniciar)
- [ ] Wireframe com listagem e filtros pronto
- [ ] Permissões por perfil definidas (Supervisor, Diretor, Gerente)
- [ ] API de listagem disponível
- [ ] Campos a exibir definidos
- [ ] Regras de visualização por hierarquia

### ✅ DOD (Concluído quando)
- [ ] Interface implementada conforme design
- [ ] Controle de acesso funcionando
- [ ] Listagem com paginação implementada
- [ ] Filtros de busca funcionais
- [ ] Exportação de dados disponível
- [ ] Performance otimizada para grandes listas

---

## 8. Tela Gestor - Inserir Competências do Colaborador

### 🔄 DOR (Pronto para iniciar)
- [ ] Protótipo de inserção/edição pronto
- [ ] Fluxo de aprovação definido
- [ ] Permissões por tipo de gestor validadas
- [ ] API de inserção/atualização disponível
- [ ] Campos e validações definidos

### ✅ DOD (Concluído quando)
- [ ] Formulário implementado
- [ ] Sistema de notificações funcionando
- [ ] Controle de permissões aplicado
- [ ] Histórico de alterações salvo
- [ ] Integração completa e testada

---

## 9. Gráficos - Análise de Competências por Setores

### 🔄 DOR (Pronto para iniciar)
- [ ] Tipos de gráficos definidos
- [ ] Métricas e KPIs especificados
- [ ] API de dados agregados disponível
- [ ] Design dos gráficos aprovado
- [ ] Biblioteca de gráficos escolhida

### ✅ DOD (Concluído quando)
- [ ] Gráficos renderizando corretamente
- [ ] Dados em tempo real (ou atualizados)
- [ ] Filtros por setor/período funcionais
- [ ] Responsividade em dispositivos móveis
- [ ] Exportação de relatórios disponível
- [ ] Performance otimizada para grandes datasets

---

## 🎯 Critérios Gerais de DOD para Todas as Telas

### 📱 Responsividade e Compatibilidade
- [ ] Desktop (1920x1080, 1366x768)
- [ ] Tablet (768x1024, 1024x768)
- [ ] Mobile (375x667, 414x896)
- [ ] Chrome (últimas 2 versões)
- [ ] Firefox (últimas 2 versões)
- [ ] Safari (últimas 2 versões)
- [ ] Edge (últimas 2 versões)

### ♿ Acessibilidade
- [ ] Contraste adequado (WCAG 2.1 AA)
- [ ] Navegação por teclado
- [ ] Compatibilidade com leitores de tela
- [ ] Alt text em imagens
- [ ] Labels em campos de formulário
- [ ] Estados de foco visíveis

### ⚡ Performance
- [ ] Tempo de carregamento inicial < 3 segundos
- [ ] First Contentful Paint < 1.5 segundos
- [ ] Largest Contentful Paint < 2.5 segundos
- [ ] Cumulative Layout Shift < 0.1
- [ ] Otimização de imagens implementada
- [ ] Lazy loading onde aplicável

### 🧪 Testes
- [ ] Testes unitários (cobertura > 80%)
- [ ] Testes de integração
- [ ] Testes E2E nos fluxos principais
- [ ] Testes de acessibilidade
- [ ] Testes de performance
- [ ] Testes cross-browser

### 🔒 Segurança
- [ ] Validação de inputs no frontend
- [ ] Sanitização de dados
- [ ] Proteção contra XSS
- [ ] Headers de segurança configurados
- [ ] Dados sensíveis não expostos no console
- [ ] Rate limiting implementado (onde necessário)

### 📚 Documentação
- [ ] Componentes documentados
- [ ] README atualizado
- [ ] Changelog mantido
- [ ] Guia de instalação/deploy
- [ ] Documentação de APIs
- [ ] Manual do usuário

### 🚀 Deploy e Qualidade
- [ ] Code review aprovado (2+ aprovações)
- [ ] Pipeline de CI/CD passando
- [ ] Testes automatizados executados
- [ ] Deploy em ambiente de staging
- [ ] Smoke tests executados
- [ ] Aprovação do Product Owner
- [ ] Deploy em produção realizado

---

## 📊 Dashboard de Progresso

### Status Geral do Projeto
- [ ] **Fase 1**: Autenticação e Cadastro (Telas 1-3)
- [ ] **Fase 2**: Onboarding e Competências (Telas 4-5)
- [ ] **Fase 3**: Funcionalidades Admin (Telas 6-8)
- [ ] **Fase 4**: Analytics e Relatórios (Tela 9)
- [ ] **Fase 5**: Testes e Deploy Final

### Marcos do Projeto
- [ ] **MVP Beta**: Funcionalidades básicas implementadas
- [ ] **Versão 1.0**: Todas as funcionalidades core finalizadas
- [ ] **Go Live**: Deploy em produção com monitoramento

---

## 📋 Como Usar Este Documento

1. **Para cada nova feature**: Marque todos os itens DOR antes de iniciar o desenvolvimento
2. **Durante o desenvolvimento**: Use os checkboxes DOD como guia
3. **Antes do deploy**: Verifique se todos os critérios gerais foram atendidos
4. **Review semanal**: Atualize o dashboard de progresso

---

**Última atualização:** [Data da última modificação]  
**Versão:** 2.0 - Com Checkboxes Interativos
