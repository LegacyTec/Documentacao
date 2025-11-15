# 📄 Estrutura da Documentação do Banco de Dados

## 1. Visão Geral

* **Objetivo do Banco de Dados:** Gerenciar dados relacionados a Colaboradores (funcionários ou membros da equipe), incluindo suas competências, experiências, certificações, cargos e avaliações internas (comentários, testes de temperamento e hierarquia).
* **Tecnologia Utilizada:**
   * **SGBD:** MySQL
   * **Hospedagem:** Railway
 
## 2. Modelo de Dados

* **O banco de dados segue um modelo relacional, conforme o Diagrama Entidade-Relacionamento (DER) abaixo.**

* **Principais Entidades (Tabelas):**

* **Colaborador: A entidade central, contendo os dados pessoais.**

* **Certificacao, Experiencia, Cargo: Detalhes profissionais do Colaborador.**

* **Soft_Skill, Hard_Skill, Competencia: Detalhes sobre as habilidades do Colaborador.**

* **Comentario, Hierarquia, teste_temperamento: Dados de relacionamento e avaliação interna.**
