# Sistema de Agendamento de Exames (SAE-HC) — Documento de Validação e Especificação de Negócio

> **Padrão Oficial SETISD / HC-UFPE (HU Brasil) — Fase 0 (Alinhamento de Negócio)**  
> **Público-alvo:** Profissionais das áreas envolvidas e Equipe de TI.  
> **Objetivo:** Descrever o processo de trabalho em **linguagem pura de negócio** (sem jargões técnicos de programação ou banco de dados) para validação, alinhamento de expectativas e tomada de decisão antes de qualquer codificação.

---

## 1. Identificação do Projeto e Contexto Institucional

| Campo | Descrição |
| :--- | :--- |
| **Nome do Sistema** | Sistema de Agendamento de Exames |
| **Área Solicitante / Cliente** | Central de Marcação de Exames |
| **Instância Superior Competente** | SETISD |
| **Líder Técnico (SETISD)** | Tiago Ferrão |
| **Objetivo Estratégico HU Brasil** | Garantir eficiência, rastreabilidade e padronização do processo de agendamento de exames no HC-UFPE |

---

## 2. O Problema que Queremos Resolver

> **Objetivo:** Dizer com clareza qual é o problema real de trabalho. Sem rodeios: o que hoje está quebrado, ineficiente ou gerando risco para o hospital?

* **A Dor Central:**  
  O processo de agendamento de exames não garante a prioridade de atendimento dos pacientes e as informações coletadas dos pacientes possuem erros demasiados.

* **Por que isso não pode continuar (Impactos Reais):**
  - **Sobrecarga de Trabalho:** As chefias e equipes perdem horas redigitando dados e conferindo manualmente tarefas que poderiam ser automáticas.
  - **Falta de Visibilidade:** A gestão não sabe em tempo real quem já entregou, quem está com pendências e onde estão os gargalos.
  - **Risco Institucional e Legal:** Falta de histórico confiável para responder a auditorias, questionamentos de órgãos de controle ou conferências internas.

---

## 3. Como o Processo Funciona Hoje (A Rotina Atual)

> **Objetivo:** Mapear a realidade crua de como as equipes se viram no dia a dia para realizar essa tarefa hoje.

* **Meios Utilizados Hoje:**
  Recebimento das solicitações de marcação de exame: Forms da Microsoft
  Armazenamento das solicitações de marcação de exame: Planilha Excel
  Marcação definitiva dos Exames: Sistema AGHUX
  Comunicação da equipe: Whatsapp

* **A Rotina Prática de Trabalho:**
  Lançamento do formulário para marcação de exames -> Exportação das respostas para planilha do Excel -> 
  Seleção dos pacientes manualmente para marcação -> Verificação dos dados preenchidos pelo paciente com os dados do AGHU -> 
  Contato com paciente para verificar disponibilidade -> Marcação do exame no sistema AGHU.

---

## 4. O Que a Nova Solução Deve Entregar (Resultado Esperado)

> **Objetivo:** Definir com clareza o que a solução digital deve trazer para eliminar a dor do processo atual.

* **A Proposta de Valor:** Integrar o processo de validação dos dados preenchidos automaticamente e priorizar os pacientes seguindo critérios predefinidos, facilitando a inclusão no backbone.
* **Ganhos Práticos Imediatos:**
  - Alerta automático de erros ou inconsistências no lançamento do formulário.
  - Assinatura eletrônica segura com registro de quem fez, quando aprovou e o que alterou.
  - Painel de controle em tempo real para a gestão acompanhar entregas e pendências.
  - Histórico guardado, inviolável e fácil de consultar a qualquer momento.
  - Redução no tempo necessário para validar os dados antes do lançamento.

---

## 5. Como Será o Trabalho no Novo Sistema (O Novo Fluxo)

> **Objetivo:** Explicar em linguagem direta como o usuário vai interagir com o sistema, resolvendo a dor do processo manual de ponta a ponta.

1. **Preenchimento e Validação Automática da Solicitação**:
O paciente ou solicitante preenche e envia o formulário digital. Logo após o envio, o sistema processa automaticamente as informações recebidas e realiza a checagem dos dados, gerando alertas e sinalizando onde estão os erros, divergências ou campos incorretos para a equipe responsável.
2. **Ordenação Automática da Fila por Prioridade**:
A solicitação é inserida em uma fila centralizada e classificada automaticamente com base nos critérios de prioridade predefinidos pelo hospital (como urgência clínica ou idade), garantindo que os casos mais graves fiquem no topo do atendimento.
3. **Conferência Unificada e Validação pelo Operador**:
O profissional da Central de Marcação acessa a fila de trabalho unificada já priorizada. Ao abrir uma solicitação, o sistema destaca automaticamente eventuais divergências entre o que foi preenchido no formulário e os dados cadastrais do paciente no sistema AGHUX. O operador realiza os ajustes necessários diretamente na tela e valida os dados com poucos cliques. Cada ação, alteração ou aprovação fica vinculada à assinatura eletrônica do operador.
4. **Confirmação e Agendamento com o Paciente**:
Com os dados conferidos e livres de erros, o operador realiza a comunicação de confirmação da data e horário com o paciente, registrando o retorno no próprio sistema para evitar contatos duplicados.
5. **Efetivação e Inclusão Facilitada no AGHUX**:
Após o aceite do paciente, o operador confirma o agendamento no AGHUX. O sistema registra o histórico completo do processo (quem solicitou, quem validou, quais alterações foram feitas e quando a marcação foi concluída), gerando uma trilha auditável inviolável.
6. **Acompanhamento e Gestão em Tempo Real**:
A gestão acessa um painel de controle central para acompanhar os indicadores operacionais em tempo real: volume de solicitações pendentes, tempo médio de validação, exames agendados e gargalos da fila, dispensando o tempo gasto na consolidação de relatórios e conferências manuais.

---

## 6. Quem Participa do Processo (Atores: Como Faz Hoje vs. Como Fará no Sistema)

| Ator / Perfil no Hospital | O que faz HOJE (Rotina Manual) | O que passará a fazer no NOVO SISTEMA | O que NÃO poderá fazer |
| --- | --- | --- | --- |
| **Área Gestora do Processo** *(Central de Marcação)* | Exporta dados do Microsoft Forms para planilhas Excel, tenta organizar prioridades manualmente e cobra pendências da equipe por WhatsApp. | Cadastra e atualiza as regras de priorização da fila, monitora o fluxo global e gerencia exceções do processo em tempo real. | Não poderá alterar a ordem da fila sem justificativa formal nem realizar agendamentos fora do fluxo auditável. |
| **Profissional do Setor / Executante** *(Operador da Central de Marcação)* | Seleciona pacientes manualmente na planilha Excel, compara dados com o AGHUX campo a campo, contata paciente por WhatsApp e agenda no AGHUX. | Trabalha na fila priorizada, analisa os alertas de erro gerados pós-envio e divergências com o AGHUX, corrige/valida os dados com assinatura eletrônica e confirma a marcação. | Não poderá alterar manualmente a prioridade dos pacientes, ignorar os alertas de inconsistência ou editar dados sem registro de sua assinatura eletrônica. |
| **Chefia Imediata / Responsável pelo Setor** *(Chefia da Central de Marcação)* | Revisa planilhas dispersas, trata erros e divergências reportados informalmente e tenta gerenciar a distribuição do trabalho sem visão do processo em tempo real. | Acompanha a produtividade da equipe e o andamento da fila em tela única, gerencia tratativas de cadastros divergentes e aprova solicitações excepcionais. | Não poderá aprovar agendamentos que permaneçam com erros ou pendências cadastrais em aberto. |
| **Gestão / Coordenação Superior** *(Gerência de Atenção à Saúde / Superintendência)* | Depende de relatórios demorados consolidados manualmente em planilhas para acompanhar gargalos, volume de exames e tempo de espera. | Acompanha o painel executivo em tempo real com indicadores de volume, taxa de erro pós-envio, tempo médio de validação e gargalos operacionais. | Acesso estritamente para visualização gerencial e acompanhamento estratégico (não realiza edições ou agendamentos operacionais). |
| **Público / Usuário do Serviço** *(Pacientes / Solicitantes do Exame)* | Preenche o Microsoft Forms, aguarda contato passivamente e precisa ligar ou ir ao hospital para obter informações. | Envia a solicitação de exame de forma estruturada pelo portal digital e consulta o status do agendamento com transparência. | Não terá acesso a informações de terceiros, dados confidenciais do hospital ou opções de alteração na fila de prioridade. |

---

## 7. Regras de Negócio Inegociáveis (RNs)

* **RN-01 (Identificação Funcional Única):** O profissional é identificado exclusivamente pela sua matrícula funcional (SIAPE). Para preservar a privacidade e evitar riscos de vazamento, dados pessoais sensíveis desnecessários (como CPF) não são coletados nem expostos no sistema.
* **RN-02 (Prevenção de Duplicidade e Choques):** O sistema impede e bloqueia que a mesma pessoa seja alocada em dois setores, turnos ou atendimentos conflitantes no mesmo horário, eliminando de raiz o risco das planilhas paralelas manuais.
* **RN-03 (Preservação e Imutabilidade do Histórico):** O fechamento de um período ou a abertura de um novo ciclo nunca apaga, altera ou sobrescreve informações passadas. Registros homologados tornam-se imutáveis para garantir respaldo em auditorias e consultas futuras.
* **RN-04 (Homologação em Bloco / Entrega Completa):** A chefia de unidade só pode homologar e encaminhar para a gestão central o lote 100% completo de todos os seus setores subordinados. O sistema bloqueia entregas parciais ou com pendências não resolvidas.
* **RN-05 (Autenticação Institucional Obrigatória):** O acesso interno para preenchimento, conferência e aprovação exige login institucional com a conta de rede do hospital, vinculando a autoria e data/hora de cada ação realizada.
* **RN-06 (Transparência Ativa com Privacidade):** Na consulta pública ou da equipe, o sistema exibe apenas o nome completo, identificação funcional e a informação oficial aprovada, garantindo publicidade dos atos administrativos em conformidade com as diretrizes de privacidade.

---

## 8. Painel de Gestão e Indicadores Estratégicos (KPIs)

O sistema deve disponibilizar painel gerencial hierárquico (cada chefia enxerga o seu escopo) com os seguintes indicadores de negócio:
1. **Taxa de Cumprimento de Prazos:** Acompanhamento percentual e quantitativo em tempo real de quais setores e unidades já concluíram suas entregas dentro do calendário oficial, eliminando a necessidade de cobranças manuais por telefone.
2. **Mapa de Pendências e Atrasos:** Listagem imediata de unidades ou setores que ainda estão com preenchimento aberto, rascunho pendente ou com prazo vencido, permitindo atuação pontual da liderança.
3. **Detecção de Inconsistências:** Alerta visual automático para profissionais ativos que não possuem alocação ou registro no ciclo vigente, evitando esquecimentos ou desvios de planejamento.

---

## 9. Matriz de Pontos de Decisão (Gabinete / Gestão do Negócio)

> *Itens que dependem de confirmação dos gestores do hospital antes da conclusão:*

| # | Ponto a Decidir | Impacto no Processo | Quem deve decidir? | Status / Definição |
| :-: | :--- | :--- | :--- | :--- |
| **1** | **Data Limite Oficial:** Até qual dia do período os setores devem fechar o preenchimento e assinar? | Define a regra do sistema para disparar alertas preventivos e travar edições intempestivas. | Gestão Central / Chefias | 🟡 Em definição |
| **2** | **Substituição de Chefia:** Qual o critério para assinatura quando a chefia titular estiver de férias ou afastada? | Evita o travamento da homologação em bloco da unidade inteira por ausência de um único responsável. | Gestão da Área | 🟡 Em definição |
| **3** | **Retificação pós-Homologação:** Qual é o rito formal para reabrir e corrigir dados já aprovados oficialmente? | Define se haverá solicitação formal de reabertura com justificativa gravada ou ajuste restrito à gestão central. | Gestão Central | 🟡 Em definição |

---
---

# 📘 GUIA METODOLÓGICO: COMO ESTE DOCUMENTO SE INTERLIGA AOS DEMAIS ARQUIVOS DO PROJETO

> **Apresentação Executiva para a Chefia:**  
> Esta seção explica a lógica de engenharia e governança adotada pelo SETISD para conectar as necessidades de negócio da ponta à construção do software.

### A Linha do Tempo: A Separação entre "Fase de Negócio" e "Fase de Engenharia"

Em qualquer projeto de software hospitalar existem dois mundos que precisam se comunicar com perfeição:
1. **O Mundo do Negócio (Chefias, Áreas Solicitantes, Governança, Direção):** Não devem ser expostos a termos técnicos de TI (bancos de dados, endpoints, JSON, status HTTP, docker, etc.). Eles precisam discutir *processos, dores reais, prazos, responsabilidades e regras*.
2. **O Mundo da Engenharia (Desenvolvedores e Testes):** Precisam de tabelas relacionais, tipos de dados estritos, rotas de API seguras e casos de uso testáveis.

Este documento (`00-validacao-negocio.md`) funciona como a **Ponte Oficial** entre esses dois mundos:

```text
               ┌────────────────────────────────────────────────────────┐
               │         00-VALIDAÇÃO E FLUXO DE NEGÓCIO (ESTE ARQUIVO)  │
FASE 1         │   Linguagem humana, fluxos e regras reais de negócio.  │
(Negócio)      │   Validado e assinado pelas Chefias e Direção do HC.   │
               └───────────────────────────┬────────────────────────────┘
                                           │
                 ┌─────────────────────────┴─────────────────────────┐
                 ▼ (Uma vez aprovado, a TI desdobra tecnicamente)     ▼
               ┌────────────────────────────────────────────────────────┐
FASE 2         │            ARTEFATOS DE ESPECIFICAÇÃO TÉCNICA           │
(Engenharia)   │   01-visao.md  →  02-requisitos.md  →  03-casos-uso.md │
               │   04-modelo-dados.md  →  05-interfaces  →  SPEC.md     │
               └────────────────────────────────────────────────────────┘
```

---

### Como cada seção deste documento alimenta a documentação técnica:

| Seção deste Documento de Negócio | O que ela entrega para a documentação técnica? | Arquivo de Destino |
| :--- | :--- | :--- |
| **Seção 2 (O Problema que Queremos Resolver)** | Define a motivação institucional, os riscos do modelo atual e a justificativa do projeto. | [01-visao.md](01-visao.md) *(Problema e Escopo)* |
| **Seção 3 (Como o Processo Funciona Hoje)** | Serve de base para mapear os processos manuais que serão substituídos e os dados legados. | [01-visao.md](01-visao.md) *(Cenário Atual)* |
| **Seção 4 (O Que a Nova Solução Deve Entregar)** | Define os objetivos do produto e os ganhos práticos que orientam a entrega de valor. | [01-visao.md](01-visao.md) *(Visão de Futuro)* |
| **Seção 5 (Como Será o Trabalho no Novo Sistema)** | Detalha as etapas práticas do usuário na tela, que viram os fluxos e cenários de uso do sistema. | [02-requisitos.md](02-requisitos.md) e [03-casos-uso.md](03-casos-uso.md) *(Casos de Uso e Fluxos)* |
| **Seção 6 (Quem Participa do Processo)** | Define os perfis de acesso, permissões de cada papel e o modelo de autorização local. | [02-requisitos.md](02-requisitos.md) e [03-casos-uso.md](03-casos-uso.md) *(Atores e RBAC)* |
| **Seção 7 (Regras de Negócio Inegociáveis)** | É convertida diretamente em requisitos funcionais estritos e validações de backend. | [02-requisitos.md](02-requisitos.md) *(Requisitos Funcionais - RFs)* |
| **Seção 8 (Painel de Gestão e Indicadores)** | Dá origem às consultas analíticas de acompanhamento, relatórios e telas gerenciais. | [05-interfaces.md](05-interfaces.md) *(Protótipos e Dashboards)* |
| **Seção 9 (Matriz de Pontos de Decisão)** | Orienta os parâmetros de configuração e regras que alimentam as tarefas de implementação. | [SPEC.md](SPEC.md) *(Definições e Tarefas)* |

---

### A Regra de Ouro do Processo no SETISD:

1. **Início do Projeto (Fase de Negócio):** O profissional de TI preenche este documento junto com os responsáveis pela área de negócio em reuniões de alinhamento, validando o problema real, os fluxos práticos e as decisões pendentes.
2. **Desenvolvimento (Fase de Engenharia):** Com este documento aprovado pelas partes envolvidas, a equipe de desenvolvimento tem total clareza técnica para elaborar os artefatos de `01` a `06` e programar a solução com segurança e sem retrabalho.

**Resultado:** O cliente hospitalar participa ativamente sem ser sobrecarregado com termos técnicos, e a equipe de TI constrói exatamente o que o hospital precisa.
