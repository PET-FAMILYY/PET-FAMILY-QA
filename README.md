---

## Sprint 4 — Quality Assurance & Tests

Nesta Sprint, foram realizados testes funcionais na API Java do projeto **Pet Family — ClyvoVet Challenge**, utilizando o **Postman** para validar as funcionalidades desenvolvidas.

O trabalho contempla o planejamento dos testes, a documentação no Azure Boards, a verificação das respostas da API e a preparação dos testes automatizados, conforme os requisitos da disciplina.

---

## Parte A — Testes Manuais de Software

Os testes manuais foram realizados utilizando o **Postman**, com requisições HTTP para os endpoints da aplicação.

Foram documentados **17 casos de teste**, abrangendo autenticação, gerenciamento de tutores, pets, consultas veterinárias, inteligência artificial e dashboard.

### Ambiente de Testes

| Tecnologia | Descrição |
|---|---|
| Backend | Java / Spring Boot |
| API | REST |
| Ferramenta de Testes | Postman |
| URL Base | `http://localhost:9090` |
| Gerenciamento | Azure DevOps / Azure Boards |
| Autenticação | JWT Bearer Token |
| Perfis de Acesso | TUTOR e VETERINARIO |

### Azure Boards

Os casos de teste estão sendo organizados no Azure DevOps, incluindo objetivos, dados de entrada, procedimentos de execução e resultados esperados.

**Organização:** RM561810

**Projeto:** Pet Family - ClyvoVet Challenge

**Link:** [Acessar Azure Boards — Pet Family](https://dev.azure.com/RM561810/Pet%20Family%20-%20ClyvoVet%20Challenge/_workitems/recentlyupdated/)

### Casos de Teste Realizados

| ID | Descrição do Teste | Resultado HTTP |
|---|---|---|
| CT01 | Consultar tutor por ID válido | 200 OK |
| CT02 | Login com credenciais válidas | 200 OK |
| CT03 | Listar todos os tutores | 200 OK |
| CT04 | Buscar tutor pelo nome | 200 OK |
| CT05 | Listar todos os pets | 200 OK |
| CT06 | Consultar pet por ID | 200 OK |
| CT07 | Filtrar pets pelo tutor | 200 OK |
| CT08 | Filtrar pets por espécie | 200 OK |
| CT09 | Verificar método HTTP não permitido | 405 Method Not Allowed |
| CT10 | Listar consultas cadastradas | 200 OK |
| CT11 | Filtrar consultas por status | 200 OK |
| CT12 | Listar consultas futuras | 200 OK |
| CT13 | Agendar consulta veterinária | 201 Created |
| CT14 | Registrar interação com IA | 201 Created |
| CT15 | Listar interações com IA | 200 OK |
| CT16 | Consultar histórico de IA por pet | 200 OK |
| CT17 | Consultar resumo do dashboard | 200 OK |

Os resultados apresentados correspondem às respostas HTTP observadas durante os testes manuais.

O teste CT09 verifica a rejeição de um método HTTP não suportado, sendo esperado o retorno `405 Method Not Allowed`.

A validação completa de cada caso também considera os dados retornados e as regras de autorização definidas pela API Java.

### Evidências dos Testes

As evidências foram capturadas durante a execução das requisições no Postman e organizadas por caso de teste.

Os arquivos estão disponíveis no diretório:

`docs/sprint-4/evidencias/`

| Teste | Evidência |
|---|---|
| CT01 — Consultar tutor | [Visualizar](docs/sprint-4/evidencias/CT01_GET__tutores_1.png) |
| CT02 — Login | [Visualizar](docs/sprint-4/evidencias/CT02_POST__auth_login.png) |
| CT03 — Listar tutores | [Visualizar](docs/sprint-4/evidencias/CT03_GET__tutores.png) |
| CT04 — Buscar tutor | [Visualizar](docs/sprint-4/evidencias/CT04_GET__tutores_nome-Maria.png) |
| CT05 — Listar pets | [Visualizar](docs/sprint-4/evidencias/CT05_GET__pets.png) |
| CT06 — Consultar pet | [Visualizar](docs/sprint-4/evidencias/CT06_GET__pets_1.png) |
| CT07 — Pets por tutor | [Visualizar](docs/sprint-4/evidencias/CT07_GET__pets_tutorId-1.png) |
| CT08 — Pets por espécie | [Visualizar](docs/sprint-4/evidencias/CT08_GET__pets_especie-Cachorro.png) |
| CT09 — Método não permitido | [Visualizar](docs/sprint-4/evidencias/CT09_POST__tutores.png) |
| CT10 — Listar consultas | [Visualizar](docs/sprint-4/evidencias/CT10_GET__consultas.png) |
| CT11 — Filtrar consultas | [Visualizar](docs/sprint-4/evidencias/CT11_GET__consultas_status-AGENDADA.png) |
| CT12 — Consultas futuras | [Visualizar](docs/sprint-4/evidencias/CT12_GET__consultas_futuras.png) |
| CT13 — Agendar consulta | [Visualizar](docs/sprint-4/evidencias/CT13_POST__consultas_agendar.png) |
| CT14 — Registrar interação IA | [Visualizar](docs/sprint-4/evidencias/CT14_POST__interacoes-ia.png) |
| CT15 — Listar interações IA | [Visualizar](docs/sprint-4/evidencias/CT15_GET__interacoes-ia.png) |
| CT16 — Histórico IA por pet | [Visualizar](docs/sprint-4/evidencias/CT16_GET__interacoes-ia_pet_1.png) |
| CT17 — Dashboard | [Visualizar](docs/sprint-4/evidencias/CT17_GET__dashboard_resumo.png) |

---

## Parte B — Automação de Testes

A automação dos testes funcionais utiliza o **Postman**, por se tratar de uma aplicação baseada em APIs REST.

Os testes automatizados utilizam scripts JavaScript para verificar códigos HTTP, dados retornados em JSON e regras de autenticação e autorização.

### Funcionalidades Selecionadas

| Caso | Funcionalidade | Validação |
|---|---|---|
| AT01 | Login de Tutor | Autenticação JWT e perfil TUTOR |
| AT02 | Controle de Acesso | Restrição de funcionalidades por perfil |
| AT03 | Interação com Assistente IA | Registro e validação de resposta |
| AT04 | Agendamento de Consulta | Criação e validação de agendamento |

### Critérios de Validação

- Verificação dos códigos HTTP esperados.
- Validação do conteúdo das respostas JSON.
- Autenticação utilizando Bearer Token.
- Verificação das permissões dos perfis TUTOR e VETERINARIO.
- Execução dos testes utilizando o Collection Runner.
- Registro dos resultados de execução.

**Status:** Automação em preparação. Os resultados serão incluídos após a execução e validação dos quatro casos.

### Vídeo de Demonstração

A demonstração apresentará a configuração do Postman, os scripts de automação, a execução dos testes e os resultados obtidos.

**Link do vídeo:** [ADICIONAR LINK]

---

## Links de Entrega — 4ª Sprint

| Plataforma | Link |
|---|---|
| Azure Boards | [Pet Family — Azure DevOps](https://dev.azure.com/RM561810/Pet%20Family%20-%20ClyvoVet%20Challenge/_workitems/recentlyupdated/) |
| GitHub | [PET-FAMILY-QA](https://github.com/PET-FAMILYY/PET-FAMILY-QA) |
| Vídeo dos Testes | [ADICIONAR LINK] |

A entrega será disponibilizada em um repositório público do GitHub, na branch `develop`, com os links necessários para avaliação.

O acesso do professor à organização e ao projeto Azure DevOps também deverá ser confirmado.

---

*Documentação da 4ª Sprint — Compliance, Quality Assurance & Tests — FIAP 2026.*
