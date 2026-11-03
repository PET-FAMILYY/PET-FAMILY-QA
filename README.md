# 🐾 Pet Family — QA & Tests

> **Compliance, Quality Assurance & Tests**  
> Challenge CLYVO VET 2026 — FIAP | 2TDSPG

Repositório de planejamento, execução e evidências de testes do projeto **Pet Family — ClyvoVet Challenge**.

**Acesso rápido:** [Azure Test Plans](https://dev.azure.com/RM561810/Pet%20Family%20-%20ClyvoVet%20Challenge/_testPlans) · [GitHub](https://github.com/PET-FAMILYY/PET-FAMILY-QA)

---

## 📌 Sobre o projeto

O **Pet Family** conecta tutores, pets e clínicas veterinárias, oferecendo funcionalidades para acompanhamento dos animais, agendamento de consultas e suporte informativo com IA.

Este repositório reúne os artefatos de **Qualidade e Testes** produzidos para o Challenge CLYVO VET 2026.

### Módulos relacionados

| Módulo | Repositório |
|---|---|
| App Mobile | [PET-FAMILY-MOBILE](https://github.com/PET-FAMILYY/PET-FAMILY-MOBILE) |
| API Java | [PET-FAMILY-JAVA](https://github.com/PET-FAMILYY/PET--FAMILY-JAVA) |
| API .NET | [PET-FAMILY-.NET](https://github.com/PET-FAMILYY/PET-FAMILY-.NET) |
| DevOps / Cloud | [PET-FAMILY-CLOUD](https://github.com/PET-FAMILYY/PET-FAMILY-CLOUD) |
| IoT | [PET-FAMILY-IOT](https://github.com/PET-FAMILYY/PET-FAMILY-IOT) |
| IA | [PET-FAMILY-IA](https://github.com/PET-FAMILYY/PET-FAMILY-IA) |

---

## 🧪 Sprint 4 — Quality Assurance & Tests

A validação funcional da **API Java / Spring Boot** foi realizada no **Postman** contra o ambiente de produção (Render). O planejamento, os procedimentos e os resultados foram organizados no **Azure DevOps**.

### Ambiente de testes

| Item | Descrição |
|---|---|
| Backend | Java / Spring Boot |
| Arquitetura | API REST |
| Ferramenta de testes | Postman |
| URL base (produção) | `https://petfamily-api.onrender.com` |
| Repositório da API | [PET-FAMILY-JAVA](https://github.com/PET-FAMILYY/PET--FAMILY-JAVA) |
| Autenticação | JWT Bearer Token |
| Perfis | `TUTOR` e `VETERINARIO` |
| Gestão de testes | Azure DevOps / Test Plans |

> ⚠️ A API roda no plano gratuito do Render e "dorme" após ~15 min sem uso. A primeira requisição pode levar até 1–2 minutos (cold start). Aguarde antes de rodar os testes.

> 🔒 Não publique senhas, credenciais ou tokens JWT no GitHub.

### Como rodar os testes no Postman

1. Importe o arquivo `docs/sprint-4/Pet_Family_-_QA.postman_collection.json`
2. Importe o arquivo `docs/sprint-4/Pet_Family_-_Prod.postman_environment.json`
3. Selecione o environment **Pet Family - Prod** no canto superior direito
4. Execute primeiro **Login - Tutor** (salva o token em `{{token}}`) e **Login - Veterinário** (salva em `{{tokenVet}}`)
5. Os demais requests já usam os tokens automaticamente via environment

### Parte A — Testes manuais e Azure DevOps

**Organização:** `RM561810`  
**Projeto:** `Pet Family - ClyvoVet Challenge`  
**Plano de testes:** `Pet Family - Plano de Testes Sprint 4` (ID 58)  
**Link:** [Abrir Azure Test Plans](https://dev.azure.com/RM561810/Pet%20Family%20-%20ClyvoVet%20Challenge/_testPlans)

#### Suítes cadastradas

| Suíte | PBI | Casos |
|---|---|---:|
| Agendamento de Consultas | `#55` | 3 |
| Chat com Assistente IA Clínico | `#22` | 3 |
| **Total** | — | **6** |

#### Casos de teste

| Caso | Funcionalidade | Método | Endpoint | HTTP esperado |
|---|---|---|---|---|
| **CT13** | Agendar consulta | `POST` | `/consultas/agendar` | `201 Created` |
| **CT14** | Registrar interação com IA | `POST` | `/interacoes-ia` | `201 Created` |
| **CT15** | Listar interações com IA (Veterinário) | `GET` | `/interacoes-ia` | `200 OK` |
| **CT16** | Histórico de IA por pet (Tutor) | `GET` | `/interacoes-ia/pet/1` | `200 OK` |
| **CT17** | Interação sem autenticação (negativo) | `POST` | `/interacoes-ia` | `401 Unauthorized` |
| **CT18** | Agendar com data inválida (negativo) | `POST` | `/consultas/agendar` | `400 Bad Request` |

#### Evidências de execução

| Teste | Evidência |
|---|---|
| CT13 — Agendamento | [Visualizar](docs/sprint-4/screenshots/CT13-agendar-consulta.png) |
| CT14 — Interação IA | [Visualizar](docs/sprint-4/screenshots/CT14-interacao-ia.png) |
| CT15 — Lista de interações | [Visualizar](docs/sprint-4/screenshots/CT15-get-interacoes-vet.png) |
| CT16 — Histórico por pet | [Visualizar](docs/sprint-4/screenshots/CT16-get-interacoes-tutor.png) |
| CT17 — Sem autenticação | [Visualizar](docs/sprint-4/screenshots/CT17-interacao-sem-auth.png) |
| CT18 — Data inválida | [Visualizar](docs/sprint-4/screenshots/CT18-data-invalida.png) |

### Parte B — Automação de testes

Foram implementados testes automatizados no **Postman** com verificações JavaScript (`pm.test()` / `pm.expect()`) e execução via **Collection Runner**.

| Caso | Cenário automatizado | O que verifica |
|---|---|---|
| **AT01** | Login de tutor | Status `200`, token JWT presente, salva `{{token}}` |
| **AT02** | Login de veterinário | Status `200`, token JWT presente, salva `{{tokenVet}}` |
| **AT03** | Registrar interação com IA | Status `201`, campos `pergunta` e `resposta` no JSON |
| **AT04** | Agendar consulta | Status `201`, campo `status` igual a `AGENDADA` |

A collection completa com os scripts está em `docs/sprint-4/Pet_Family_-_QA.postman_collection.json`.

### 🎥 Vídeo de demonstração

**[Assistir ao vídeo — QA Pet Family Sprint 4](https://youtu.be/t1PxkP_zZYs)**

---

## 📂 Estrutura do repositório

```text
PET-FAMILY-QA/
├── docs/
│   ├── sprint-3/
│   │   └── backlog.md
│   └── sprint-4/
│       ├── Pet_Family_-_QA.postman_collection.json
│       ├── Pet_Family_-_Prod.postman_environment.json
│       └── screenshots/
│           ├── CT13-agendar-consulta.png
│           ├── CT14-interacao-ia.png
│           ├── CT15-get-interacoes-vet.png
│           ├── CT16-get-interacoes-tutor.png
│           ├── CT17-interacao-sem-auth.png
│           └── CT18-data-invalida.png
└── README.md
```

---

## 🔗 Links de entrega

| Item | Link |
|---|---|
| Azure Test Plans | [Plano de testes](https://dev.azure.com/RM561810/Pet%20Family%20-%20ClyvoVet%20Challenge/_testPlans) |
| Azure Boards | [Projeto Pet Family](https://dev.azure.com/RM561810/Pet%20Family%20-%20ClyvoVet%20Challenge/_workitems/recentlyupdated/) |
| GitHub | [PET-FAMILY-QA](https://github.com/PET-FAMILYY/PET-FAMILY-QA) |
| API (produção) | [petfamily-api.onrender.com](https://petfamily-api.onrender.com) |

**Branch de entrega:** `develop`.

---

## 👥 Equipe

| Nome | RM |
|---|---|
| Felipe Kirschner Modesto | RM561810 |
| João Victor Luiz de Oliveira Resende | RM565139 |
| Pedro Henrique Vaz Ferreira | RM566551 |
| Vitor Dias dos Santos | RM565422 |

## 🎓 Disciplina

**Compliance, Quality Assurance & Tests**  
**Professor:** Dr. Gustavo Molina Félix  
**Curso:** Tecnologia em Análise e Desenvolvimento de Sistemas — FIAP 2026

---

*Pet Family — Quality Assurance & Tests • Challenge CLYVO VET 2026.*
