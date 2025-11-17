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
# 3. Dicionário de Dados (Estrutura das Tabelas)

Com base no diagrama (que fornece nomes de campos, tipos e chaves), podemos detalhar a estrutura.

**Observação:** O diagrama mostra os tipos de dados e tamanhos (ex: `varchar(60)`, `int`, `date`), que são cruciais para a documentação.

## 3.1. Tabela: Colaborador (Entidade Principal)

| Coluna | Tipo de Dados | Chave/Restrição | Descrição |
|--------|---------------|-----------------|-----------|
| `id_colaborador` | `int` | PK | Identificador único do colaborador. |
| `nome` | `varchar(60)` | - | Nome completo do colaborador. |
| `email` | `varchar(60)` | - | E-mail do colaborador. |
| `id_colaborador` | `int` | - | Um identificador adicional de colaborador. (Verificar se é necessário). |
| `cpf` | `numeric(10,10)` | - | CPF do colaborador. |
| `apresentacao` | `varchar(100)` | - | Uma breve apresentação ou resumo. |
| `id_perfil` | `varchar(100)` | - | Perfil de acesso/sistema. |
| `id_perfil_temperamen` | `varchar(100)` | - | Resultado do perfil de temperamento. |
| `foto_perfil` | `varchar(255)` | - | URL ou caminho para a foto de perfil. |

## 3.2. Tabela: Certificacao

| Coluna | Tipo de Dados | Chave/Restrição | Descrição |
|--------|---------------|-----------------|-----------|
| `nome_certific` | `varchar(60)` | - | Nome da certificação. |
| `string_instituicao` | `varchar(60)` | - | Instituição que emitiu a certificação. |
| `id_certificacao` | `int` | - | Identificador da certificação. |
| `Colaborador_id_cola` | `int` | FK | Chave estrangeira ligando ao Colaborador. |

## 3.3. Tabela: Experiencia

| Coluna | Tipo de Dados | Chave/Restrição | Descrição |
|--------|---------------|-----------------|-----------|
| `string_cargo` | `varchar(60)` | - | Cargo ocupado. |
| `string_empresa` | `varchar(60)` | - | Nome da empresa. |
| `data_data_inici` | `date` | - | Data de início da experiência. |
| `data_data_fim` | `date` | - | Data de fim da experiência. |
| `id_Experiencia` | `int` | PK | Identificador da experiência. |
| `Colaborador_id_int` | `int` | FK | Chave estrangeira ligando ao Colaborador. |


---

## 4. Relacionamentos entre Entidades

Os relacionamentos definem como as informações estão conectadas. Todos os relacionamentos abaixo são **Um para Muitos (1:N)**, onde um Colaborador pode ter **Muitos** itens nas tabelas relacionadas.

| Tabela Principal (1) | Tabela Relacionada (N) | Tipo de Relacionamento | Campo de Ligação (FK) |
|---------------------|------------------------|------------------------|----------------------|
| Colaborador | Certificacao | 1:N | `Colaborador_id_cola` |
| Colaborador | Experiencia | 1:N | `Colaborador_id_int` |
| Colaborador | Cargo | 1:N | `Colaborador_id_colabora` |
| Colaborador | Comentario | 1:N | `Colaborador_id_c_int` |
| Colaborador | Soft_Skill | 1:N | `Colaborador_id_c_int` |
| Colaborador | Hard_Skill | 1:N | `Colaborador_id_col_int` |
| Colaborador | Competencia | 1:N | `Colaborador_id_colab` |
| Colaborador | Hierarquia | 1:N | `Colaborador_id_int` |
| Colaborador | teste_temperamento | 1:N | `Colaborador_id_int` |

---

## 5. Configuração de Hospedagem (Railway)

- **SGBD:** MySQL
- **Ambiente:** Nuvem (Railway)
- **Acesso:** As credenciais de acesso (hostname, porta, nome do banco, usuário e senha) estão disponíveis na aba "Credentials" do serviço de banco de dados no painel do Railway.
