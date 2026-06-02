# Seleção de Escopo

## Objetivo

O sistema StayHub é uma plataforma de busca e reserva de hospedagens que centraliza opções de estadia e seus preços. Considerando a quantidade de funcionalidades previstas no Documento de Requisitos, optamos por modelar apenas três fatias verticais representativas do sistema, priorizando profundidade de análise em vez de cobertura total.

A seleção foi realizada com base nos critérios estabelecidos pelo trabalho:

* Cobrir pelo menos uma funcionalidade essencial (Must Have) para o funcionamento do produto;
* Incluir pelo menos uma funcionalidade que envolva múltiplos atores ou subsistemas;
* Incluir pelo menos uma funcionalidade com regras de negócio não triviais.

As três fatias escolhidas representam os principais processos do sistema e abrangem diferentes aspectos da modelagem estrutural, comportamental e de persistência.

# Fatia 1 – Realização de Reserva com Pagamento e Confirmação

## Histórias e requisitos cobertos
- HOTL-003 – Busca de hospedagens
- HOTL-004 – Disponibilidade de quartos
- HOTL-005 – Realização de reservas
- HOTL-006 – Confirmação de reserva

## Justificativa

A fatia 1 representa o principal fluxo de negócio da plataforma. Nela, o usuário pesquisa hospedagens, verifica a disponibilidade para um período específico, realiza o pagamento e recebe a confirmação da reserva.

Nesta fatia está presente a funcionalidade mais crítica do sistema, ja que é responsável por gerar valor tanto para clientes quanto para estabelecimentos. Ademais, envolve a integração com um gateway de pagamento externo e com um serviço de envio de e-mails.

## Aprendizado esperado

Modelando esta fatia, podemos explorar:
- Integração entre múltiplos subsistemas;
- Comunicação com serviços externos;
- Fluxos alternativos e tratamento de falhas;
- Regras de disponibilidade e prevenção de reservas duplicadas.

# Fatia 2 – Cancelamento de Reserva e Aplicação de Política de Reembolso

## Histórias e requisitos cobertos
- HOTL-007 – Cancelamento de reservas

## Justificativa

Por mais que seja um fluxo secundário quando comparado a realização da reserva, o cancelamento possuí regras de negócio relevantes. O sistema tem as seguintes obrigações: validar políticas de cancelamento, atualizar o estado da reserva e, quando aplicável, realizar reembolsos parciais ou integrais.

Um ciclo de vida bem definido e mútiplos cenários possíveis torna essa funcionalidade adequada para modelagem profunda.

## Aprendizado esperado

Modelando esta fatia, podemos explorar:
- Transições de estado de uma reserva;
- Regras condicionais de negócio;
- Processos de reembolso;
- Tratamento de exceções e restrições de cancelamento.

# Fatia 3 – Avaliação de Hospedagens

## Histórias e requisitos cobertos
- HOTL-008 – Avaliação de estabelecimentos
- HOTL-009 – Exibição de avaliações
- HOTL-010 – Histórico de reservas

## Justificativa

O motivo pela seleção dessa fatia é sua funcionalidade direcionada a experiência do usuário e à reputação dos estabelecimentos cadastrados na plataforma.

Para que ocorra o registro de uma avaliação, o sistema deve verificar se o usuário possuí uma estadia concluída associada à hospedagem que ele está avaliando. Não apenas isso, o sistema também deve realizar o cálculo e a exibição da nota média do establecimento para usuários.

Por mais que não seja uma funcionalidade crítica para o funcionamento da plataforma, ela possuí regras de negócio importantes e tem uma contribuição significativa para a qualidade das informações disponibilizadas aos clientes.

## Aprendizado esperado

Modelando esta fatia, podemos explorar:
- Regras de autorização baseadas em histórico de reservas;
- Relacionamentos entre reservas, usuários e avaliações;
- Cálculo e atualização de métricas agregadas;
- Fluxos de interação pós-estadia.

# Cobertura dos Critérios de Seleção

| Critério                             | Fatia 1 | Fatia 2 | Fatia 3 |
| ------------------------------------ | ------- | ------- | ------- |
| Funcionalidade essencial (Must Have) | ✓       | ✓       |         |
| Múltiplos subsistemas ou integrações | ✓       | ✓       |         |
| Regras de negócio não triviais       | ✓       | ✓       | ✓       |

Os três aspectos solicitados pela tarefa estão incluídos no grupo de fatias escolhidas.

# Funcionalidades Fora do Escopo

As seguintes funcionalidades não serão modeladas neste trabalho:
- HOTL-001 – Cadastro de hospedagens;
- HOTL-002 – Cadastro de tipos de quartos.

Essas características foram vistas essencialmente como funcionais e centradas em processos de registro (CRUD), mostrando uma complexidade inferior em relação às partes escolhidas. Embora possuam importância para a operação da plataforma, sua modelagem traria menor contribuição ao propósito do projeto, que é investigar fluxos completos, integrações e regras comerciais pertinentes.

Além do mais, algumas das entidades geradas por essas características (Hospedagem e TipoQuarto) estarão presentes de forma natural nos modelos das outras partes, assegurando sua representação indireta nos documentos elaborados.
