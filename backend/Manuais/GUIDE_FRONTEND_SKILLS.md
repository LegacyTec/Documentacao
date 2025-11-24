# 📘 Guia: Como Usar Skills Pré-definidas no Frontend

##  Objetivo

Substituir os campos de texto livre por **dropdowns/selects** que mostram apenas skills pré-definidas do banco de dados.

## 🔌 Endpoints Disponíveis

### Hard Skills (Competências Técnicas)
```
GET /api/competencia/hard
```
Retorna todas as hard skills pré-definidas (Java, React, AWS, etc.)

**Resposta:**
```json
[
  {
    "id": 1,
    "nomeCompetencia": "Java",
    "tipoHabilidade": "hard"
  },
  {
    "id": 2,
    "nomeCompetencia": "React",
    "tipoHabilidade": "hard"
  }
]
```

### Soft Skills
```
GET /api/softskill/available
```
Retorna todas as soft skills pré-definidas

**Resposta:**
```json
[
  {
    "id": 1,
    "nomeCompetencia": "Comunicação efetiva"
  },
  {
    "id": 2,
    "nomeCompetencia": "Trabalho em equipe"
  }
]
```

##  Como Implementar no Frontend

### 1. Substituir Input de Texto por Select

**ANTES (texto livre):**
```tsx
<input
  type="text"
  placeholder="Adicionar Hard Skill..."
  value={novaHardSkill}
  onChange={(e) => setNovaHardSkill(e.target.value)}
/>
```

**DEPOIS (dropdown):**
```tsx
<select
  value={novaHardSkill}
  onChange={(e) => setNovaHardSkill(e.target.value)}
>
  <option value="">Selecione uma skill...</option>
  {hardSkillsDisponiveis.map(skill => (
    <option key={skill.id} value={skill.id}>
      {skill.nomeCompetencia}
    </option>
  ))}
</select>
```

### 2. Buscar Skills Disponíveis

Adicione no início do componente:

```tsx
const [hardSkillsDisponiveis, setHardSkillsDisponiveis] = useState([]);
const [softSkillsDisponiveis, setSoftSkillsDisponiveis] = useState([]);

useEffect(() => {
  // Buscar hard skills disponíveis
  fetch(`${API_BASE_URL}/api/competencia/hard`)
    .then(res => res.json())
    .then(data => setHardSkillsDisponiveis(data));

  // Buscar soft skills disponíveis
  fetch(`${API_BASE_URL}/api/softskill/available`)
    .then(res => res.json())
    .then(data => setSoftSkillsDisponiveis(data));
}, []);
```

### 3. Ajustar Função de Adicionar

**ANTES:**
```tsx
const adicionarHardSkill = async () => {
  if (novaHardSkill.trim() && colaborador) {
    const novaSkill = {
      nomeCompetencia: novaHardSkill.trim(), //  Texto livre
      colaborador: { id: colaborador.id }
    };
    // ...
  }
};
```

**DEPOIS:**
```tsx
const adicionarHardSkill = async () => {
  if (novaHardSkill && colaborador) {
    // Buscar skill selecionada
    const skillSelecionada = hardSkillsDisponiveis.find(
      s => s.id === parseInt(novaHardSkill)
    );
    
    if (skillSelecionada) {
      const novaSkill = {
        nomeCompetencia: skillSelecionada.nomeCompetencia,
        colaborador: { id: colaborador.id },
        competencia: { id: skillSelecionada.id } // Link com a competência
      };
      // ...
    }
  }
};
```

##  Lista de Skills Pré-definidas

### Hard Skills (30+ disponíveis)
- Java, JavaScript, TypeScript, Python, C++, C#, Ruby, Go, Rust
- React, Vue.js, Angular, Next.js
- Spring Boot, Node.js, Express, Django, FastAPI
- MySQL, PostgreSQL, MongoDB, Redis
- AWS, Docker, Kubernetes, Git, CI/CD, Terraform
- React Native, Flutter, iOS (Swift), Android (Kotlin)

### Soft Skills (23 disponíveis)
- Comunicação efetiva, Trabalho em equipe, Liderança
- Resolução de problemas, Pensamento crítico
- Adaptabilidade, Gestão de tempo, Mentoria
- Criatividade, Empatia, Escuta ativa
- Negociação, Inteligência emocional, Assertividade
- Paciência, Motivação, Organização
- Proatividade, Resiliência, Colaboração
- Feedback construtivo, Autodisciplina, Visão estratégica

##  Benefícios

1. **Consistência**: Todos usam as mesmas skills
2. **Busca**: Fácil buscar pessoas por skill
3. **Analytics**: Estatísticas de skills mais procuradas
4. **UX**: Dropdown é mais rápido que digitar
5. **Sem erros**: Não permite typos

