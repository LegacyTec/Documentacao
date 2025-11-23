# Manual de Programação - Backend Altave

## Sumário

1. [Visão Geral do Sistema](#1-visão-geral-do-sistema)
2. [Arquitetura e Stack Tecnológica](#2-arquitetura-e-stack-tecnológica)
3. [Configuração do Ambiente](#3-configuração-do-ambiente)
4. [Estrutura do Projeto](#4-estrutura-do-projeto)
5. [Camadas da Aplicação](#5-camadas-da-aplicação)
6. [Modelos de Dados](#6-modelos-de-dados)
7. [Endpoints da API](#7-endpoints-da-api)
8. [Padrões de Desenvolvimento](#8-padrões-de-desenvolvimento)
9. [Segurança](#9-segurança)
10. [Banco de Dados e Migrações](#10-banco-de-dados-e-migrações)
11. [Otimização de Performance](#11-otimização-de-performance)
12. [Deploy e Ambientes](#12-deploy-e-ambientes)
13. [Testes](#13-testes)
14. [Troubleshooting](#14-troubleshooting)

## 1. Visão Geral do Sistema

O Backend Altave é uma aplicação REST API desenvolvida para a Plataforma de Mapeamento de Competências, permitindo gerenciar perfis profissionais de colaboradores, incluindo habilidades técnicas, soft skills, certificações, experiências e projetos.

### Objetivos do Sistema

- Gerenciamento completo de perfis de colaboradores
- Mapeamento de competências técnicas e comportamentais
- Sistema de hierarquia organizacional (diretores, supervisores, colaboradores)
- Dashboard com métricas e estatísticas
- Sistema de notificações por email
- Avaliação de perfil DISC

### Principais Funcionalidades

- CRUD completo de colaboradores
- Gestão de hard skills, soft skills e certificações
- Upload e gerenciamento de fotos de perfil
- Sistema de comentários
- Hierarquia organizacional
- Notificações automáticas
- Dashboard analítico

## 2. Arquitetura e Stack Tecnológica

### Arquitetura

A aplicação segue o padrão MVC (Model-View-Controller) adaptado para APIs REST, organizada em camadas:

```
Controller -> Service -> Repository -> Database
```

### Stack Tecnológica

#### Core

- **Java 17**: Linguagem de programação principal
- **Spring Boot 3.2.0**: Framework principal
- **Maven**: Gerenciador de dependências

#### Persistência

- **Spring Data JPA**: Abstração de persistência
- **Hibernate**: ORM (Object-Relational Mapping)
- **MySQL 8.0**: Banco de dados de produção
- **H2 Database**: Banco de dados para desenvolvimento local
- **Flyway**: Versionamento de banco de dados

#### Segurança e Configuração

- **Spring Security**: Segurança e autenticação
- **BCrypt**: Criptografia de senhas

#### Utilitários

- **Lombok**: Redução de boilerplate
- **Bean Validation**: Validação de dados
- **OkHttp**: Cliente HTTP para integração com APIs externas
- **JSON (org.json)**: Processamento de JSON
- **Bucket4j**: Rate limiting

#### Infraestrutura

- **Docker**: Containerização
- **Railway**: Plataforma de deploy

## 3. Configuração do Ambiente

### Pré-requisitos

```bash
- Java JDK 17
- Maven 3.6+
- MySQL 8.0 (para produção)
- Git
- IDE (IntelliJ IDEA, Eclipse, VS Code)
```

### Instalação

#### 1. Clonar o Repositório

```bash
git clone https://github.com/pedromattos11/backend-altave.git
cd backend-altave
```

#### 2. Configurar Variáveis de Ambiente

Crie o arquivo `application-local.properties` em `src/main/resources/`:

```properties
# Banco de Dados Local
spring.datasource.url=jdbc:mysql://localhost:3306/altave_db
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha

# Email (opcional para desenvolvimento)
EMAIL_API_KEY=sua_chave_resend
EMAIL_FROM=seu_email@dominio.com
```

#### 3. Executar a Aplicação

##### Via Maven Wrapper

```bash
./mvnw spring-boot:run
```

##### Via IDE

Execute a classe principal `BackendAltaveApplication.java`

#### 4. Verificar o Funcionamento

A aplicação estará disponível em: `http://localhost:8080`

### Configuração do Banco de Dados

#### Desenvolvimento Local (H2)

Por padrão, a aplicação usa H2 em memória. Nenhuma configuração adicional necessária.

#### Produção (MySQL)

Configure no `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://host:porta/database
spring.datasource.username=usuario
spring.datasource.password=senha
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```

## 4. Estrutura do Projeto

```
backend-altave/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── br/com/altave/backend_altave/
│   │   │       ├── BackendAltaveApplication.java
│   │   │       ├── config/
│   │   │       │   ├── CacheConfig.java
│   │   │       │   ├── CorsConfig.java
│   │   │       │   ├── FlywayConfig.java
│   │   │       │   ├── JpaConfig.java
│   │   │       │   ├── RateLimitFilter.java
│   │   │       │   ├── SecurityConfig.java
│   │   │       │   ├── SecurityHeadersFilter.java
│   │   │       │   └── TransactionConfig.java
│   │   │       ├── controller/
│   │   │       │   ├── ColaboradorController.java
│   │   │       │   ├── HardSkillController.java
│   │   │       │   ├── SoftSkillController.java
│   │   │       │   ├── CertificacaoController.java
│   │   │       │   ├── ExperienciaController.java
│   │   │       │   ├── ProjetoController.java
│   │   │       │   ├── CargoController.java
│   │   │       │   ├── UsuarioController.java
│   │   │       │   ├── DashboardController.java
│   │   │       │   ├── DISCController.java
│   │   │       │   └── ...
│   │   │       ├── dto/
│   │   │       │   ├── ColaboradorListDTO.java
│   │   │       │   ├── ColaboradorBasicDTO.java
│   │   │       │   ├── HardSkillDTO.java
│   │   │       │   ├── SoftSkillDTO.java
│   │   │       │   └── ...
│   │   │       ├── model/
│   │   │       │   ├── Colaborador.java
│   │   │       │   ├── HardSkill.java
│   │   │       │   ├── SoftSkill.java
│   │   │       │   ├── Certificacao.java
│   │   │       │   ├── Experiencia.java
│   │   │       │   ├── Projeto.java
│   │   │       │   ├── Cargo.java
│   │   │       │   ├── Usuario.java
│   │   │       │   └── ...
│   │   │       ├── repository/
│   │   │       │   ├── ColaboradorRepository.java
│   │   │       │   ├── HardSkillRepository.java
│   │   │       │   └── ...
│   │   │       └── service/
│   │   │           ├── ColaboradorService.java
│   │   │           ├── HardSkillService.java
│   │   │           ├── EmailService.java
│   │   │           ├── FileService.java
│   │   │           └── ...
│   │   └── resources/
│   │       ├── application.properties
│   │       └── db/
│   │           └── migration/
│   │               ├── V1__create-table-usuarios.sql
│   │               ├── V2__create_tables.sql
│   │               └── ...
│   └── test/
│       └── java/
├── pom.xml
├── Dockerfile
└── README.md
```

## 5. Camadas da Aplicação

### Controller (Controladores)

Responsáveis por receber as requisições HTTP, validar dados de entrada e retornar respostas.

**Exemplo:**

```java
@RestController
@RequestMapping("/api/colaborador")
public class ColaboradorController {
    
    private final ColaboradorService service;
    
    @GetMapping("/{id}")
    public ResponseEntity<Colaborador> getById(@PathVariable Integer id) {
        return service.findById(id)
            .map(ResponseEntity::ok)
            .orElse(ResponseEntity.notFound().build());
    }
    
    @PostMapping
    public Colaborador create(@RequestBody Colaborador obj) {
        return service.save(obj);
    }
}
```

**Boas Práticas:**

- Use `@RestController` para APIs REST
- Prefixe rotas com `/api/`
- Retorne `ResponseEntity` para melhor controle de status HTTP
- Use DTOs para evitar expor entidades diretamente
- Implemente validação com Bean Validation (`@Valid`)

### Service (Serviços)

Contém a lógica de negócio da aplicação.

**Exemplo:**

```java
@Service
public class ColaboradorService {
    
    private final ColaboradorRepository repo;
    
    public Optional<Colaborador> update(Integer id, Colaborador newData) {
        return repo.findById(id)
            .map(existing -> {
                if (newData.getNome() != null) {
                    existing.setNome(newData.getNome());
                }
                existing.setUltimaAtualizacao(LocalDateTime.now());
                return repo.save(existing);
            });
    }
}
```

**Boas Práticas:**

- Anote com `@Service`
- Use injeção de dependências via construtor
- Retorne `Optional` quando o resultado pode não existir
- Não exponha repositórios nos controllers
- Mantenha a lógica de negócio centralizada

### Repository (Repositórios)

Interface com o banco de dados usando Spring Data JPA.

**Exemplo:**

```java
@Repository
public interface ColaboradorRepository extends JpaRepository<Colaborador, Integer> {
    
    Optional<Colaborador> findByEmail(String email);
    
    @Query("SELECT c FROM Colaborador c LEFT JOIN FETCH c.cargo WHERE c.id = :id")
    Optional<Colaborador> findByIdWithRelations(@Param("id") Integer id);
    
    @Query("SELECT COUNT(DISTINCT c.id) FROM Colaborador c")
    long countTotalColaboradores();
}
```

**Boas Práticas:**

- Anote com `@Repository`
- Estenda `JpaRepository<Entity, ID>`
- Use method naming para queries simples
- Use `@Query` para queries complexas
- Use `JOIN FETCH` para evitar N+1 queries

### Model (Entidades)

Representam as tabelas do banco de dados.

**Exemplo:**

```java
@Entity
@Table(name = "colaborador")
@Getter
@Setter
@NoArgsConstructor
@AllArgsConstructor
public class Colaborador {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;
    
    @Column(length = 60, nullable = false)
    private String nome;
    
    @Column(length = 60, nullable = false, unique = true)
    private String email;
    
    @ManyToOne
    @JoinColumn(name = "cargo_id")
    private Cargo cargo;
    
    @OneToMany(mappedBy = "colaborador", cascade = CascadeType.ALL)
    private Set<HardSkill> hardSkills = new HashSet<>();
}
```

**Boas Práticas:**

- Use `@Entity` e `@Table`
- Use Lombok para reduzir boilerplate
- Configure relacionamentos corretamente
- Use `FetchType.LAZY` por padrão
- Configure cascades com cuidado

### DTO (Data Transfer Objects)

Objetos usados para transferir dados entre camadas.

**Exemplo:**

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class ColaboradorListDTO {
    private Integer id;
    private String nome;
    private String email;
    private String cargoNome;
    private Integer totalHardSkills;
    private Integer totalSoftSkills;
}
```

**Quando Usar:**

- Para listagens otimizadas
- Para não expor dados sensíveis
- Para evitar problemas de serialização com entidades JPA

## 6. Modelos de Dados

### Colaborador

Entidade principal do sistema.

**Atributos:**

- `id`: Identificador único
- `nome`: Nome completo
- `email`: Email (único)
- `cpf`: CPF (único)
- `apresentacao`: Texto de apresentação
- `profilePicturePath`: Caminho da foto de perfil
- `perfil`: Tipo de perfil (admin, usuário)
- `ultimaAtualizacao`: Data da última atualização
- `cargo`: Cargo do colaborador
- `supervisor`: Supervisor direto
- `diretor`: Diretor da área
- `subordinados`: Colaboradores subordinados

**Relacionamentos:**

- `ManyToOne` com Cargo
- `ManyToOne` com Supervisor (Colaborador)
- `ManyToOne` com Diretor (Colaborador)
- `OneToMany` com HardSkill
- `ManyToMany` com SoftSkill
- `ManyToMany` com Certificacao
- `OneToMany` com Experiencia
- `OneToMany` com Projeto

### HardSkill

Habilidades técnicas específicas.

**Atributos:**

- `id`: Identificador único
- `nomeCompetencia`: Nome da competência
- `nivelConhecimento`: Nível (1-5)
- `categoria`: Categoria da skill
- `colaborador`: Colaborador associado

### SoftSkill

Competências comportamentais.

**Atributos:**

- `id`: Identificador único
- `nomeCompetencia`: Nome da competência

### Certificacao

Certificações profissionais.

**Atributos:**

- `id`: Identificador único
- `nomeCertificacao`: Nome da certificação
- `instituicao`: Instituição emissora
- `dataObtencao`: Data de obtenção

### Experiencia

Experiências profissionais.

**Atributos:**

- `id`: Identificador único
- `cargo`: Cargo exercido
- `empresa`: Nome da empresa
- `dataInicio`: Data de início
- `dataFim`: Data de término
- `descricao`: Descrição das atividades
- `colaborador`: Colaborador associado

### Projeto

Projetos desenvolvidos.

**Atributos:**

- `id`: Identificador único
- `nomeProjeto`: Nome do projeto
- `descricao`: Descrição
- `dataInicio`: Data de início
- `dataFim`: Data de término
- `tecnologias`: Tecnologias utilizadas
- `colaborador`: Colaborador associado

### Usuario

Usuário do sistema.

**Atributos:**

- `id`: Identificador único
- `nomeCompleto`: Nome completo
- `dataNascimento`: Data de nascimento
- `cpf`: CPF (único)
- `email`: Email (único)
- `senha`: Senha criptografada
- `role`: Papel (USER, ADMIN)

## 7. Endpoints da API

### Colaboradores

#### Listar Todos (Leve)

```
GET /api/colaborador/list
```

Retorna lista otimizada de colaboradores (DTO).

#### Buscar por ID

```
GET /api/colaborador/{id}
```

#### Buscar por Email

```
GET /api/colaborador/by-email/{email}
```

#### Criar Colaborador

```
POST /api/colaborador
Content-Type: application/json

{
  "nome": "João Silva",
  "email": "joao@example.com",
  "cpf": 12345678900,
  "apresentacao": "Desenvolvedor Full Stack",
  "cargo": {
    "id": 1
  }
}
```

#### Atualizar Colaborador

```
PUT /api/colaborador/{id}
Content-Type: application/json

{
  "nome": "João Silva Santos",
  "apresentacao": "Senior Full Stack Developer"
}
```

#### Deletar Colaborador

```
DELETE /api/colaborador/{id}
```

#### Upload de Foto

```
POST /api/colaborador/{id}/foto
Content-Type: multipart/form-data

foto: [arquivo de imagem]
```

#### Gerenciar Certificações

```
POST /api/colaborador/{colaboradorId}/certificacao/{certificacaoId}
DELETE /api/colaborador/{colaboradorId}/certificacao/{certificacaoId}
```

#### Gerenciar Soft Skills

```
POST /api/colaborador/{colaboradorId}/softskill
Content-Type: application/json

{
  "nomeCompetencia": "Trabalho em equipe"
}

DELETE /api/colaborador/{colaboradorId}/softskill/{softSkillId}
```

### Hard Skills

#### Listar Todas

```
GET /api/hardskill
```

#### Buscar por ID

```
GET /api/hardskill/{id}
```

#### Buscar por Colaborador

```
GET /api/hardskill/colaborador/{colaboradorId}
```

#### Criar Hard Skill

```
POST /api/hardskill
Content-Type: application/json

{
  "nomeCompetencia": "Java",
  "nivelConhecimento": 4,
  "categoria": "Backend",
  "colaborador": {
    "id": 1
  }
}
```

#### Atualizar Hard Skill

```
PUT /api/hardskill/{id}
```

#### Deletar Hard Skill

```
DELETE /api/hardskill/{id}
```

### Soft Skills

#### Listar Todas

```
GET /api/softskill
```

#### Criar Soft Skill

```
POST /api/softskill
Content-Type: application/json

{
  "nomeCompetencia": "Liderança"
}
```

### Certificações

#### Listar Todas

```
GET /api/certificacao
```

#### Criar Certificação

```
POST /api/certificacao
Content-Type: application/json

{
  "nomeCertificacao": "AWS Solutions Architect",
  "instituicao": "Amazon Web Services",
  "dataObtencao": "2024-01-15"
}
```

### Experiências

#### Listar por Colaborador

```
GET /api/experiencia/colaborador/{colaboradorId}
```

#### Criar Experiência

```
POST /api/experiencia
Content-Type: application/json

{
  "cargo": "Desenvolvedor Backend",
  "empresa": "TechCorp",
  "dataInicio": "2020-01-01",
  "dataFim": "2023-12-31",
  "descricao": "Desenvolvimento de APIs REST",
  "colaborador": {
    "id": 1
  }
}
```

### Projetos

#### Listar por Colaborador

```
GET /api/projeto/colaborador/{colaboradorId}
```

#### Criar Projeto

```
POST /api/projeto
Content-Type: application/json

{
  "nomeProjeto": "Sistema de E-commerce",
  "descricao": "Plataforma completa de vendas online",
  "dataInicio": "2023-01-01",
  "dataFim": "2023-06-30",
  "tecnologias": "Java, Spring Boot, React",
  "colaborador": {
    "id": 1
  }
}
```

### Dashboard

#### Obter Estatísticas

```
GET /api/dashboard/stats
```

Retorna métricas do sistema:
- Total de colaboradores
- Colaboradores com soft skills
- Total de soft skills mapeadas
- Total de hard skills mapeadas

### Usuários

#### Login

```
POST /api/usuarios/login
Content-Type: application/json

{
  "email": "usuario@example.com",
  "senha": "senha123"
}
```

#### Registrar

```
POST /api/usuarios/register
Content-Type: application/json

{
  "nomeCompleto": "Maria Santos",
  "dataNascimento": "1990-05-15",
  "cpf": "12345678900",
  "email": "maria@example.com",
  "senha": "senha123"
}
```

## 8. Padrões de Desenvolvimento

### Convenções de Código

#### Nomenclatura

- **Classes**: PascalCase (`ColaboradorService`)
- **Métodos**: camelCase (`findById`)
- **Constantes**: UPPER_SNAKE_CASE (`MAX_FILE_SIZE`)
- **Pacotes**: lowercase (`br.com.altave.backend_altave`)

#### Estrutura de Métodos

```java
// Ordem recomendada
public class ExemploService {
    // 1. Constantes
    private static final int MAX_RESULTS = 100;
    
    // 2. Atributos
    private final ExemploRepository repository;
    
    // 3. Construtor
    public ExemploService(ExemploRepository repository) {
        this.repository = repository;
    }
    
    // 4. Métodos públicos
    public List<Exemplo> findAll() {
        return repository.findAll();
    }
    
    // 5. Métodos privados
    private void validate(Exemplo obj) {
        // validação
    }
}
```

### Tratamento de Erros

#### Controller

```java
@GetMapping("/{id}")
public ResponseEntity<Colaborador> getById(@PathVariable Integer id) {
    return service.findById(id)
        .map(ResponseEntity::ok)
        .orElse(ResponseEntity.notFound().build());
}
```

#### Service

```java
public Optional<Colaborador> findById(Integer id) {
    return repository.findById(id);
}
```

#### Exception Handling Global

Crie um `@ControllerAdvice` para tratar exceções globalmente:

```java
@ControllerAdvice
public class GlobalExceptionHandler {
    
    @ExceptionHandler(EntityNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleNotFound(EntityNotFoundException ex) {
        ErrorResponse error = new ErrorResponse(404, ex.getMessage());
        return ResponseEntity.status(404).body(error);
    }
}
```

### Validação

Use Bean Validation:

```java
@Entity
public class Colaborador {
    
    @NotBlank(message = "Nome é obrigatório")
    @Size(max = 60, message = "Nome deve ter no máximo 60 caracteres")
    private String nome;
    
    @Email(message = "Email inválido")
    @NotBlank(message = "Email é obrigatório")
    private String email;
}
```

No controller:

```java
@PostMapping
public ResponseEntity<Colaborador> create(@Valid @RequestBody Colaborador obj) {
    return ResponseEntity.ok(service.save(obj));
}
```

### Logging

Use SLF4J com Logback:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

@Service
public class ColaboradorService {
    
    private static final Logger log = LoggerFactory.getLogger(ColaboradorService.class);
    
    public Colaborador save(Colaborador obj) {
        log.info("Salvando colaborador: {}", obj.getNome());
        return repository.save(obj);
    }
}
```

## 9. Segurança

### Configuração Spring Security

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {
    
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http.csrf(csrf -> csrf.disable())
            .cors(cors -> cors.configurationSource(corsConfigurationSource()))
            .authorizeHttpRequests(authz -> authz
                .anyRequest().permitAll()
            );
        return http.build();
    }
}
```

### CORS

Configuração para permitir requisições do frontend:

```java
@Configuration
public class CorsConfig {
    
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                    .allowedOriginPatterns(
                        "http://localhost:5173",
                        "https://*.vercel.app"
                    )
                    .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
                    .allowedHeaders("*")
                    .allowCredentials(true);
            }
        };
    }
}
```

### Criptografia de Senhas

```java
@Service
public class UsuarioService {
    
    private final PasswordEncoder passwordEncoder;
    
    public Usuario register(Usuario usuario) {
        String senhaCriptografada = passwordEncoder.encode(usuario.getSenha());
        usuario.setSenha(senhaCriptografada);
        return repository.save(usuario);
    }
    
    public boolean authenticate(String email, String senha) {
        return repository.findByEmail(email)
            .map(usuario -> passwordEncoder.matches(senha, usuario.getSenha()))
            .orElse(false);
    }
}
```

### Rate Limiting

Implementado com Bucket4j:

```java
@Component
public class RateLimitFilter extends OncePerRequestFilter {
    
    private final Bucket bucket = Bucket.builder()
        .addLimit(Limit.of(100, Duration.ofMinutes(1)))
        .build();
    
    @Override
    protected void doFilterInternal(HttpServletRequest request, 
                                    HttpServletResponse response, 
                                    FilterChain filterChain) {
        if (bucket.tryConsume(1)) {
            filterChain.doFilter(request, response);
        } else {
            response.setStatus(429); // Too Many Requests
        }
    }
}
```

## 10. Banco de Dados e Migrações

### Flyway

Gerenciamento de versões do banco de dados.

#### Estrutura de Migrations

```
src/main/resources/db/migration/
├── V1__create-table-usuarios.sql
├── V2__create_tables.sql
├── V3__insert_pedro_mattos_data.sql
└── V21__create_perfil_disc_table.sql
```

#### Nomenclatura

- Prefixo: `V` (versionada)
- Número: sequencial (`1`, `2`, `3`)
- Separador: `__` (dois underscores)
- Descrição: snake_case

#### Exemplo de Migration

```sql
-- V22__add_column_exemplo.sql
ALTER TABLE colaborador 
ADD COLUMN nova_coluna VARCHAR(100);

UPDATE colaborador 
SET nova_coluna = 'valor_padrao' 
WHERE nova_coluna IS NULL;
```

#### Boas Práticas

- Nunca altere uma migration já aplicada
- Sempre crie uma nova migration para correções
- Use migrations para dados de inicialização
- Teste migrations em ambiente de desenvolvimento primeiro

### Configuração Flyway

```properties
spring.flyway.enabled=true
spring.flyway.baseline-on-migrate=true
spring.flyway.validate-on-migrate=true
spring.flyway.out-of-order=false
```

### JPA Configuration

```properties
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
spring.jpa.properties.hibernate.format_sql=true
```

**Importante:** Em produção, use `ddl-auto=validate` ou `none`.

## 11. Otimização de Performance

### Problema N+1

Evite carregar relacionamentos em loops:

**Ruim:**

```java
List<Colaborador> colaboradores = repository.findAll();
for (Colaborador c : colaboradores) {
    System.out.println(c.getCargo().getNome()); // N+1!
}
```

**Bom:**

```java
@Query("SELECT c FROM Colaborador c LEFT JOIN FETCH c.cargo")
List<Colaborador> findAllWithCargo();
```

### DTOs para Listagens

Use DTOs em vez de entidades completas:

```java
@Query("""
    SELECT new br.com.altave.backend_altave.dto.ColaboradorListDTO(
        c.id, 
        c.nome, 
        c.email, 
        COALESCE(ca.nomeCargo, 'Não definido'),
        c.profilePicturePath,
        (SELECT COUNT(h) FROM HardSkill h WHERE h.colaborador.id = c.id),
        (SELECT COUNT(s) FROM Colaborador co JOIN co.softSkills s WHERE co.id = c.id),
        (SELECT COUNT(cert) FROM Colaborador co JOIN co.certificacoes cert WHERE co.id = c.id)
    )
    FROM Colaborador c
    LEFT JOIN c.cargo ca
    """)
List<ColaboradorListDTO> findAllOptimized();
```

### Lazy Loading

Use `FetchType.LAZY` por padrão:

```java
@OneToMany(mappedBy = "colaborador", fetch = FetchType.LAZY)
private Set<HardSkill> hardSkills;
```

### Cache

Configure cache para queries frequentes:

```java
@Configuration
@EnableCaching
public class CacheConfig {
    
    @Bean
    public CacheManager cacheManager() {
        return new ConcurrentMapCacheManager("colaboradores", "cargos");
    }
}
```

Use em métodos:

```java
@Cacheable("colaboradores")
public Optional<Colaborador> findById(Integer id) {
    return repository.findById(id);
}

@CacheEvict(value = "colaboradores", key = "#id")
public void deleteById(Integer id) {
    repository.deleteById(id);
}
```

### Paginação

Para grandes volumes de dados:

```java
@GetMapping
public Page<Colaborador> list(Pageable pageable) {
    return repository.findAll(pageable);
}
```

Requisição:

```
GET /api/colaborador?page=0&size=20&sort=nome,asc
```

## 12. Deploy e Ambientes

### Ambientes

#### Desenvolvimento Local

```properties
# application-local.properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
```

#### Produção (Railway)

```properties
# application.properties
spring.datasource.url=${DATABASE_URL}
spring.jpa.hibernate.ddl-auto=validate
```

### Docker

#### Dockerfile

```dockerfile
FROM maven:3.9-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline -B
COPY src ./src
RUN mvn clean package -DskipTests -B

FROM eclipse-temurin:17-jre
WORKDIR /app
COPY --from=build /app/target/backend-altave-0.0.1-SNAPSHOT.jar app.jar
RUN mkdir -p /app/uploads && chmod 755 /app/uploads
EXPOSE 8080
ENV JAVA_OPTS="-Xmx512m -Xms256m"
CMD ["java", "-jar", "app.jar"]
```

#### Build e Run

```bash
# Build
docker build -t backend-altave .

# Run
docker run -p 8080:8080 \
  -e DATABASE_URL=jdbc:mysql://host:3306/db \
  backend-altave
```

### Railway

#### railway.toml

```toml
[build]
builder = "dockerfile"
dockerfilePath = "Dockerfile"

[deploy]
startCommand = "java -jar app.jar"
healthcheckPath = "/api/colaborador/count"
healthcheckTimeout = 100
restartPolicyType = "on_failure"
restartPolicyMaxRetries = 10
```

### Variáveis de Ambiente

Configure no Railway:

```
DATABASE_URL=jdbc:mysql://host:port/database
DATABASE_USER=usuario
DATABASE_PASSWORD=senha
EMAIL_API_KEY=chave_resend
EMAIL_FROM=notificacoes@altave.com.br
```

## 13. Testes

### Estrutura de Testes

```
src/test/java/
└── br/com/altave/backend_altave/
    ├── controller/
    │   └── ColaboradorControllerTest.java
    ├── service/
    │   └── ColaboradorServiceTest.java
    └── repository/
        └── ColaboradorRepositoryTest.java
```

### Testes Unitários

```java
@SpringBootTest
class ColaboradorServiceTest {
    
    @Mock
    private ColaboradorRepository repository;
    
    @InjectMocks
    private ColaboradorService service;
    
    @Test
    void deveBuscarColaboradorPorId() {
        Colaborador colaborador = new Colaborador();
        colaborador.setId(1);
        colaborador.setNome("João");
        
        when(repository.findById(1)).thenReturn(Optional.of(colaborador));
        
        Optional<Colaborador> result = service.findById(1);
        
        assertTrue(result.isPresent());
        assertEquals("João", result.get().getNome());
    }
}
```

### Testes de Integração

```java
@SpringBootTest
@AutoConfigureMockMvc
class ColaboradorControllerIntegrationTest {
    
    @Autowired
    private MockMvc mockMvc;
    
    @Test
    void deveListarColaboradores() throws Exception {
        mockMvc.perform(get("/api/colaborador/list"))
            .andExpect(status().isOk())
            .andExpect(content().contentType(MediaType.APPLICATION_JSON));
    }
}
```

### Executar Testes

```bash
# Todos os testes
./mvnw test

# Testes específicos
./mvnw test -Dtest=ColaboradorServiceTest

# Com coverage
./mvnw test jacoco:report
```

## 14. Troubleshooting

### Problemas Comuns

#### LazyInitializationException

**Erro:**

```
org.hibernate.LazyInitializationException: could not initialize proxy
```

**Solução:**

Use `JOIN FETCH` ou ative a transação:

```java
@Transactional(readOnly = true)
public Optional<Colaborador> findById(Integer id) {
    return repository.findById(id);
}
```

#### N+1 Queries

**Sintoma:** Muitas queries para buscar dados relacionados.

**Solução:** Use DTOs com queries otimizadas ou `JOIN FETCH`.

#### Problema de Encoding UTF-8

**Sintoma:** Caracteres especiais aparecem incorretamente.

**Solução:**

```properties
spring.datasource.url=jdbc:mysql://host:3306/db?useUnicode=true&characterEncoding=UTF-8
server.servlet.encoding.charset=UTF-8
server.servlet.encoding.enabled=true
server.servlet.encoding.force=true
```

#### Flyway Checksum Failed

**Erro:**

```
FlywayException: Validate failed: Migration checksum mismatch
```

**Solução:**

```bash
# Reparar migrations
./mvnw flyway:repair

# Ou reconstruir banco de dados
./mvnw flyway:clean
./mvnw flyway:migrate
```

#### Port Already in Use

**Erro:**

```
Port 8080 is already in use
```

**Solução:**

```properties
# Mudar porta no application.properties
server.port=8081
```

Ou matar processo:

```bash
# Linux/Mac
lsof -ti:8080 | xargs kill -9

# Windows
netstat -ano | findstr :8080
taskkill /PID [PID] /F
```

### Logs e Debug

#### Habilitar SQL Logs

```properties
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
logging.level.org.hibernate.SQL=DEBUG
logging.level.org.hibernate.type.descriptor.sql.BasicBinder=TRACE
```

#### Habilitar Debug do Spring

```properties
logging.level.org.springframework=DEBUG
logging.level.br.com.altave.backend_altave=DEBUG
```

#### Arquivo de Log

```properties
logging.file.name=backend.log
logging.pattern.file=%d{yyyy-MM-dd HH:mm:ss} [%thread] %-5level %logger{36} - %msg%n
```

### Performance

#### Monitorar Queries

Use p6spy:

```xml
<dependency>
    <groupId>com.github.gavlyukovskiy</groupId>
    <artifactId>p6spy-spring-boot-starter</artifactId>
    <version>1.9.0</version>
</dependency>
```

#### Profile da Aplicação

Use Spring Actuator:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

Acesse: `http://localhost:8080/actuator/health`

### Backup e Restore

#### Backup MySQL

```bash
mysqldump -u usuario -p database > backup.sql
```

#### Restore MySQL

```bash
mysql -u usuario -p database < backup.sql
```

## Conclusão

Este manual fornece uma visão completa da arquitetura, desenvolvimento e manutenção do Backend Altave. Para dúvidas ou contribuições, consulte a documentação oficial do Spring Boot e as issues do repositório.

### Recursos Adicionais

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- [Flyway Documentation](https://flywaydb.org/documentation/)
- [MySQL Reference Manual](https://dev.mysql.com/doc/)
- [Railway Documentation](https://docs.railway.app/)

### Contato

Para suporte técnico, entre em contato com a equipe de desenvolvimento.
