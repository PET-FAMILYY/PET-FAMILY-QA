# 🐾 Pet Family — Backlog Atualizado (QA Sprint 3)

Este repositório centraliza a documentação, planejamento de releases e detalhamento de tarefas do projeto **Pet Family**.

---

## Épicos do Produto

### ÉPICO 1 — Gestão e Perfil do Pet
* Cadastro, perfil clínico e histórico longitudinal do animal.

### ÉPICO 2 — Alimentação Inteligente (IoT)
* Controle, agendamento e monitoramento do alimentador ESP32 via app mobile.

### ÉPICO 3 — Acompanhamento de Saúde
* Protocolos preventivos, terapêuticos e de bem-estar ao longo da vida do pet.

### ÉPICO 4 — Assistente IA
* Personalização, priorização e contato clínico via chat conversacional com IA.

---

## Release Plan

| Iteração | PBIs Alocados | Total Story Points |
| :--- | :--- | :--- |
| **Sprint 3 — Sem 1** | PBI 1, PBI 4 | 21 pts |
| **Sprint 3 — Sem 2** | PBI 6, PBI 8 | 16 pts |
| **Sprint 3 — Sem 3** | PBI 2, PBI 3, PBI 7 | 18 pts |
| **Sprint 3 — Sem 4** | PBI 5 | 13 pts |
| **Sprint 4 — Sem 1** | PBI 11 | 13 pts |
| **Sprint 4 — Sem 2** | PBI 12 | 13 pts |
| **Sprint 4 — Sem 3** | PBI 9, PBI 10 | 16 pts |
| **Sprint 4 — Sem 4-5**| Plano de testes manuais + automação | — |

---

## Features e PBIs (Product Backlog Items)

### ÉPICO 1 — Gestão e Perfil do Pet

#### Feature 1.1 — Cadastro de Pet
*   **PBI 1 — \[Cadastro\] Tutor cadastra novo pet na plataforma**
    *   **Descrição:** Como tutor, eu quero cadastrar meu pet com nome, espécie, raça, idade e peso para que eu tenha um perfil clínico centralizado e atualizado do meu animal.
    *   **Critérios de Aceite:**
        *   [ ] Campos obrigatórios: nome, espécie, raça, idade, peso
        *   [ ] Permitir upload de foto do pet
        *   [ ] Dados persistidos via API Java (Spring Boot)
        *   [ ] Exibir mensagem de sucesso após cadastro
        *   [ ] Não permitir cadastro sem nome e espécie
    *   **Métricas:** `Story Points: 8` | `Prioridade: 1` | `Sprint: 3`

*   **PBI 2 — \[Cadastro\] Tutor edita informações do pet cadastrado**
    *   **Descrição:** Como tutor, eu quero editar os dados do meu pet para que as informações clínicas estejam sempre atualizadas.
    *   **Critérios de Aceite:**
        *   [ ] Todos os campos editáveis
        *   [ ] Alterações persistidas na API
        *   [ ] Não permitir salvar nome vazio
        *   [ ] Confirmação visual após salvar
    *   **Métricas:** `Story Points: 5` | `Prioridade: 2` | `Sprint: 3`

#### Feature 1.2 — Perfil Clínico
*   **PBI 3 — \[Perfil\] Tutor visualiza perfil completo do pet**
    *   **Descrição:** Como tutor, eu quero visualizar o perfil completo do meu pet para que eu tenha acesso rápido a todas as informações clínicas e de comportamento do animal.
    *   **Critérios de Aceite:**
        *   [ ] Exibir foto, nome, espécie, raça, idade e peso
        *   [ ] Exibir histórico de vacinas e consultas
        *   [ ] Botão de edição visível e funcional
        *   [ ] Dados carregados da API Java
    *   **Métricas:** `Story Points: 5` | `Prioridade: 2` | `Sprint: 3`

---

### ÉPICO 2 — Alimentação Inteligente (IoT)

#### Feature 2.1 — Controle do Alimentador
*   **PBI 4 — \[Alimentador\] Tutor aciona alimentação manual pelo app**
    *   **Descrição:** Como tutor, eu quero acionar remotamente a alimentação do meu pet pelo app para que eu possa cuidar dele mesmo à distância.
    *   **Critérios de Aceite:**
        *   [ ] Botão de acionamento visível na tela principal
        *   [ ] Comunicação com ESP32 via API REST (`/api/feed`)
        *   [ ] Feedback visual de confirmação do acionamento
        *   [ ] Horário do acionamento registrado e exibido
        *   [ ] Funciona em simulação Wokwi quando hardware indisponível
    *   **Métricas:** `Story Points: 13` | `Prioridade: 1` | `Sprint: 3`

*   **PBI 5 — \[Alimentador\] Tutor agenda horários automáticos de alimentação**
    *   **Descrição:** Como tutor, eu quero agendar horários fixos de alimentação para que meu pet seja alimentado regularmente sem intervenção manual.
    *   **Critérios de Aceite:**
        *   [ ] Até 3 horários diários configuráveis
        *   [ ] Exibir próxima alimentação agendada (`nextFeedIn`)
        *   [ ] Agendamentos persistidos no dispositivo via `AsyncStorage`
        *   [ ] Não permitir horários duplicados
    *   **Métricas:** `Story Points: 13` | `Prioridade: 1` | `Sprint: 3`

#### Feature 2.2 — Monitoramento do Alimentador
*   **PBI 6 — \[Monitoramento\] Tutor visualiza status em tempo real do alimentador**
    *   **Descrição:** Como tutor, eu quero visualizar o nível de ração e as condições do ambiente para que eu saiba quando repor e se o ambiente está adequado para meu pet.
    *   **Critérios de Aceite:**
        *   [ ] Exibir nível de ração (`foodLevel`)
        *   [ ] Exibir temperatura e umidade via DHT22
        *   [ ] Exibir último horário de alimentação (`lastFeedTime`) e contador (`feedCount`)
        *   [ ] Dados atualizados via polling na API `/api/status` do ESP32
        *   [ ] Estado da porta do alimentador (`doorState`) visível
    *   **Métricas:** `Story Points: 8` | `Prioridade: 1` | `Sprint: 3`

*   **PBI 7 — \[Monitoramento\] Tutor recebe alerta de nível baixo de ração**
    *   **Descrição:** Como tutor, eu quero ser alertado quando a ração estiver acabando para que eu possa repor antes de faltar e meu pet não fique sem comida.
    *   **Critérios de Aceite:**
        *   [ ] Alerta exibido quando `foodLevel` abaixo de 20%
        *   [ ] Notificação clara e destacada na interface
        *   [ ] Alerta desaparece após reposição detectada
    *   **Métricas:** `Story Points: 8` | `Prioridade: 2` | `Sprint: 3`

---

### ÉPICO 3 — Acompanhamento de Saúde

#### Feature 3.1 — Protocolos Preventivos
*   **PBI 8 — \[Preventivo\] Tutor registra vacinas e vermífugos do pet**
    *   **Descrição:** Como tutor, eu quero registrar vacinas e vermífugos aplicados para que eu tenha controle do calendário preventivo do meu pet e não perca nenhuma dose.
    *   **Critérios de Aceite:**
        *   [ ] Campos: tipo, data de aplicação, próxima data, observação
        *   [ ] Listar registros em ordem cronológica
        *   [ ] Exibir alerta quando próxima dose estiver se aproximando
        *   [ ] Dados persistidos via API Java
        *   [ ] Permitir excluir registro com confirmação
    *   **Métricas:** `Story Points: 8` | `Prioridade: 2` | `Sprint: 3`

*   **PBI 9 — \[Preventivo\] Tutor visualiza protocolo de check-up por espécie e raça**
    *   **Descrição:** Como tutor, eu quero ver um protocolo de check-up recomendado para a espécie e raça do meu pet para que eu possa seguir as orientações veterinárias corretas.
    *   **Critérios de Aceite:**
        *   [ ] Protocolo filtrado por espécie e raça cadastradas
        *   [ ] Exibir frequência recomendada de cada exame
        *   [ ] Dados baseados em tabela da API Java
    *   **Métricas:** `Story Points: 8` | `Prioridade: 3` | `Sprint: 4`

#### Feature 3.2 — Acompanhamento Terapêutico
*   **PBI 10 — \[Terapêutico\] Tutor registra medicamentos em uso pelo pet**
    *   **Descrição:** Como tutor, eu quero registrar os medicamentos que meu pet está tomando para que eu mantenha a adesão ao tratamento e não perca nenhuma dose.
    *   **Critérios de Aceite:**
        *   [ ] Campos: nome do medicamento, dose, frequência, início e fim do tratamento
        *   [ ] Exibir próxima dose a tomar
        *   [ ] Marcar dose como administrada
        *   [ ] Dados persistidos via API
    *   **Métricas:** `Story Points: 8` | `Prioridade: 3` | `Sprint: 4`

---

### ÉPICO 4 — Assistente IA

#### Feature 4.1 — Chat Conversacional
*   **PBI 11 — \[IA\] Tutor conversa com assistente sobre saúde e bem-estar do pet**
    *   **Descrição:** Como tutor, eu quero conversar com um assistente inteligente sobre a saúde do meu pet para que eu receba orientações personalizadas sem precisar buscar informações em outras fontes.
    *   **Critérios de Aceite:**
        *   [ ] Chat funcional integrado ao Gemini 1.5 Flash
        *   [ ] System prompt dinâmico com perfil do pet (nome, espécie, raça, idade, peso)
        *   [ ] Respostas contextualizadas ao perfil cadastrado
        *   [ ] Histórico da conversa visível na tela
        *   [ ] Dados do perfil carregados do `AsyncStorage`
    *   **Métricas:** `Story Points: 13` | `Prioridade: 1` | `Sprint: 4`

*   **PBI 12 — \[IA\] Assistente incorpora dados do alimentador IoT nas recomendações**
    *   **Descrição:** Como tutor, eu quero que o assistente conheça os dados reais do alimentador para que as recomendações nutricionais sejam baseadas no consumo real do meu pet.
    *   **Critérios de Aceite:**
        *   [ ] Dados do ESP32 (`temperatura`, `foodLevel`, `lastFeedTime`) injetados no prompt
        *   [ ] Assistente capaz de comentar sobre alimentação e ambiente
        *   [ ] Integração entre `geminiService.ts` e API IoT funcional
    *   **Métricas:** `Story Points: 13` | `Prioridade: 2` | `Sprint: 4`

---

## Detalhamento das Tasks (Sprint 3)

### PBI 4 — Acionamento manual do alimentador
- [ ] **Task 1:** Mapear endpoint `/api/feed` do ESP32 e testar via Postman `[3 pts]` *(Sem dependência)*
- [ ] **Task 2:** Implementar chamada HTTP no app React Native `[5 pts]` *(Depende da Task 1)*
- [ ] **Task 3:** Criar componente de botão de acionamento na tela principal `[3 pts]` *(Depende da Task 2)*
- [ ] **Task 4:** Adicionar feedback visual e registrar horário na interface `[2 pts]` *(Depende da Task 3)*

### PBI 6 — Monitoramento em tempo real
- [ ] **Task 1:** Conectar app à API `/api/status` do ESP32 `[3 pts]` *(Sem dependência)*
- [ ] **Task 2:** Criar componente de dashboard de status (`foodLevel`, `temp`, `umidade`) `[5 pts]` *(Depende da Task 1)*
- [ ] **Task 3:** Implementar polling automático a cada 30s `[3 pts]` *(Depende da Task 1)*
- [ ] **Task 4:** Testar exibição correta de todos os campos `[2 pts]` *(Depende das Tasks 2 e 3)*

### PBI 8 — Registro de vacinas
- Task 1: Criar endpoint de vacinas na API Java (se não existir) [3 pts] (Sem dependência)
- Task 2: Criar tela de registro de vacinas no app [5 pts] (Depende da Task 1)
- Task 3: Implementar listagem cronológica de vacinas [3 pts] (Depende da Task 2)
- Task 4: Adicionar confirmação de exclusão [2 pts] (Depende da Task 3)
