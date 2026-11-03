Compliance, Quality Assurance & Tests
Challenge CLYVO VET 2026 — FIAP | 2TDSPG

Repositório de planejamento, execução e evidências de testes do projeto Pet Family — ClyvoVet Challenge.

Acesso rápido: Azure Test Plans · Vídeo da Sprint 4 · GitHub
📌 Sobre o projeto
O Pet Family conecta tutores, pets e clínicas veterinárias, oferecendo funcionalidades para acompanhamento dos animais, agendamento de consultas e suporte informativo.

Este repositório reúne os artefatos de Qualidade e Testes produzidos para o Challenge CLYVO VET 2026.
Módulos relacionados
Módulo	Repositório
App Mobile	PET-FAMILY-MOBILE
API Java	PET-FAMILY-JAVA
API .NET	PET-FAMILY-.NET
DevOps / Cloud	PET-FAMILY-CLOUD
IoT	PET-FAMILY-IOT
IA	PET-FAMILY-IA


🧪 Sprint 4 — Quality Assurance & Tests
A validação funcional da API Java / Spring Boot foi realizada no Postman. O planejamento, os procedimentos e os resultados esperados foram organizados no Azure DevOps.

Este README destaca quatro testes manuais (CT13 a CT16). No Azure, o plano contém duas suítes com seis casos cadastrados. Os quatro cenários de automação (AT01 a AT04) são descritos separadamente.
Ambiente de testes
Item	Descrição
Backend	Java / Spring Boot
Arquitetura	API REST
Ferramenta de testes	Postman
URL base local	http://localhost:9090
Autenticação	JWT Bearer Token, conforme o endpoint
Perfis	TUTOR e VETERINARIO
Gestão de testes	Azure DevOps / Test Plans


Para reproduzir os testes, a API precisa estar executando localmente. Não publique senhas, credenciais ou tokens JWT no GitHub.

Parte A — Testes manuais e Azure DevOps
Organização: RM561810
Projeto: Pet Family - ClyvoVet Challenge
Plano de testes: Pet Family - Plano de Testes Sprint 4 (ID 58)
Link: Abrir Azure Test Plans
Suítes cadastradas
Suíte	PBI	Casos
Agendamento de Consultas	#55	3
Chat com Assistente IA Clínico	#22	3
Total	—	6


Os casos registrados no Azure utilizam Step Action e Step Expected Result para documentar o procedimento e o resultado esperado de cada etapa.
Quatro testes apresentados
Caso	Funcionalidade	Método	Endpoint	HTTP observado
CT13	Agendar consulta	POST	/consultas/agendar	201 Created
CT14	Registrar interação com IA	POST	/interacoes-ia	201 Created
CT15	Listar interações com IA	GET	/interacoes-ia	200 OK
CT16	Histórico de IA por pet	GET	/interacoes-ia/pet/1	200 OK


Os códigos HTTP acima foram observados nos testes manuais do Postman. A validação também considera o conteúdo JSON e as regras de autenticação e autorização da API.
CT13 — Agendar consulta veterinária
Objetivo: verificar a criação de uma consulta para um pet cadastrado.
Requisição: POST http://localhost:9090/consultas/agendar
{
  "petId": 1,
  "tipoConsulta": "Vacinação",
  "data": "2026-12-10",
  "horario": "14:00",
  "observacoes": "V10 + antirrábica"
}
Esperado: 201 Created, com a consulta criada e status AGENDADA.
CT14 — Registrar interação com IA
Objetivo: verificar o registro de pergunta e resposta do assistente.
Requisição: POST http://localhost:9090/interacoes-ia
{
  "pergunta": "Meu cachorro está tossindo muito, o que pode ser?",
  "categoria": "Sintomas",
  "petId": 1
}
Esperado: 201 Created, com identificação da interação e resposta do assistente.
CT15 — Listar interações com IA
Requisição: GET http://localhost:9090/interacoes-ia
Esperado: 200 OK, com os registros de interações em JSON.
CT16 — Consultar histórico de IA do pet
Requisição: GET http://localhost:9090/interacoes-ia/pet/1
Esperado: 200 OK, com as interações associadas ao pet de ID 1 (Thor nos dados do teste).
📸 Evidências no Postman
As imagens devem ser publicadas em docs/sprint-4/evidencias/ na mesma branch deste README.
Teste	Evidência
CT13 — Agendamento	[Visualizar](docs/sprint-4/evidencias/CT13_POST__consultas_agendar.png)
CT14 — Interação IA	[Visualizar](docs/sprint-4/evidencias/CT14_POST__interacoes-ia.png)
CT15 — Lista de interações	[Visualizar](docs/sprint-4/evidencias/CT15_GET__interacoes-ia.png)
CT16 — Histórico por pet	[Visualizar](docs/sprint-4/evidencias/CT16_GET__interacoes-ia_pet_1.png)


Atenção: os links funcionam somente após o envio dos arquivos para os caminhos indicados.

Parte B — Automação de testes
Foram selecionados quatro cenários para automação no Postman, com verificações JavaScript (pm.test() / pm.expect()) e execução no Collection Runner.
Caso	Cenário automatizado	O que verificar
AT01	Login de tutor	Código HTTP, token JWT e perfil TUTOR
AT02	Controle de acesso	Restrições de endpoints conforme o perfil
AT03	Registro de interação com IA	Criação e dados de resposta JSON
AT04	Agendamento de consulta	Código HTTP e dados da consulta criada


Critérios: status HTTP, campos JSON, autenticação JWT, permissões de acesso e registro dos resultados do Runner.

Situação: cenários documentados; o resultado final de aprovação dos quatro testes automatizados deve ser confirmado pela execução real. Os casos cadastrados no Azure, isoladamente, não comprovam a automação.
🎥 Vídeo de demonstração
Assistir ao vídeo — QA Pet Family

Para comprovar a Parte B, o vídeo deve apresentar a configuração dos scripts de teste, a execução dos quatro cenários e os resultados no Postman.
📂 Organização das evidências
Estrutura esperada para os arquivos destacados neste README:
PET-FAMILY-QA/
├── docs/
│   ├── sprint-3/
│   │   └── backlog.md
│   └── sprint-4/
│       └── evidencias/
│           ├── CT13_POST__consultas_agendar.png
│           ├── CT14_POST__interacoes-ia.png
│           ├── CT15_GET__interacoes-ia.png
│           └── CT16_GET__interacoes-ia_pet_1.png
└── README.md
Confira a existência dos arquivos antes de entregar; esta estrutura é uma referência, não uma confirmação de que já foram publicados.
🔗 Links de entrega
Item	Link
Azure Test Plans	Plano de testes
Azure Boards	Projeto Pet Family
GitHub	PET-FAMILY-QA
Vídeo	Demonstração QA — YouTube


Branch de entrega: develop. Antes de finalizar, confirme o acesso do professor ao Azure, os arquivos de evidência e a execução dos quatro testes automatizados.
👥 Equipe
Integrante	RM
Felipe Kirschner Modesto	RM561810
João Victor Luiz de Oliveira Resende	RM565139
Pedro Henrique Vaz Ferreira	RM566551
Vitor Dias dos Santos	RM565422


🎓 Disciplina
Compliance, Quality Assurance & Tests
Professor: Dr. Gustavo Molina Félix
Curso: Tecnologia em Análise e Desenvolvimento de Sistemas — FIAP 2026
