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

* HOTL-003 – Busca de hospedagens
* HOTL-004 – Disponibilidade de quartos
* HOTL-005 – Realização de reservas
* HOTL-006 – Confirmação de reserva

## Justificativa

Esta fatia representa o principal fluxo de negócio da plataforma. O usuário pesquisa hospedagens, verifica a disponibilidade para um período específico, realiza o pagamento e recebe a confirmação da reserva.

Trata-se da funcionalidade mais crítica do sistema, pois é responsável pela geração de valor tanto para clientes quanto para estabelecimentos. Além disso, envolve integração com um gateway de pagamento externo e com um serviço de envio de e-mails.

## Aprendizado esperado

A modelagem desta fatia permitirá explorar:

* Integração entre múltiplos subsistemas;
* Comunicação com serviços externos;
* Fluxos alternativos e tratamento de falhas;
* Regras de disponibilidade e prevenção de reservas duplicadas.

# Fatia 2 – Cancelamento de Reserva e Aplicação de Política de Reembolso

## Histórias e requisitos cobertos

* HOTL-007 – Cancelamento de reservas

## Justificativa

Embora seja um fluxo secundário em relação à realização da reserva, o cancelamento apresenta regras de negócio relevantes. O sistema deve validar políticas de cancelamento, atualizar o estado da reserva e, quando aplicável, realizar reembolsos parciais ou integrais.

Essa funcionalidade possui um ciclo de vida bem definido e múltiplos cenários possíveis, tornando-a adequada para modelagem aprofundada.

## Aprendizado esperado

A modelagem desta fatia permitirá explorar:

* Transições de estado de uma reserva;
* Regras condicionais de negócio;
* Processos de reembolso;
* Tratamento de exceções e restrições de cancelamento.

# Fatia 3 – Avaliação de Hospedagens

## Histórias e requisitos cobertos

* HOTL-008 – Avaliação de estabelecimentos
* HOTL-009 – Exibição de avaliações
* HOTL-010 – Histórico de reservas

## Justificativa

Esta fatia foi selecionada por representar uma funcionalidade voltada à experiência do usuário e à reputação dos estabelecimentos cadastrados na plataforma.

Para que uma avaliação seja registrada, o sistema deve validar se o usuário possui uma estadia concluída associada à hospedagem avaliada. Além disso, o sistema deve calcular e exibir corretamente a nota média do estabelecimento para outros usuários.

Embora não seja uma funcionalidade crítica para a operação básica da plataforma, ela apresenta regras de negócio importantes e contribui significativamente para a qualidade das informações disponibilizadas aos clientes.

## Aprendizado esperado

A modelagem desta fatia permitirá explorar:

* Regras de autorização baseadas em histórico de reservas;
* Relacionamentos entre reservas, usuários e avaliações;
* Cálculo e atualização de métricas agregadas;
* Fluxos de interação pós-estadia.

# Cobertura dos Critérios de Seleção

| Critério                             | Fatia 1 | Fatia 2 | Fatia 3 |
| ------------------------------------ | ------- | ------- | ------- |
| Funcionalidade essencial (Must Have) | ✓       | ✓       |         |
| Múltiplos subsistemas ou integrações | ✓       | ✓       |         |
| Regras de negócio não triviais       | ✓       | ✓       | ✓       |

Os três critérios exigidos pelo trabalho estão contemplados pelo conjunto das fatias selecionadas.

# Funcionalidades Fora do Escopo

As funcionalidades abaixo não serão modeladas neste trabalho:

* HOTL-001 – Cadastro de hospedagens;
* HOTL-002 – Cadastro de tipos de quartos.

Essas funcionalidades foram consideradas predominantemente operacionais e focadas em operações de cadastro (CRUD), apresentando menor complexidade de domínio quando comparadas às fatias selecionadas. Embora sejam importantes para o funcionamento da plataforma, sua modelagem agregaria menos valor ao objetivo do trabalho, que é explorar fluxos completos, integrações e regras de negócio relevantes.

Além disso, parte das entidades criadas por essas funcionalidades (Hospedagem e TipoQuarto) já aparecerá naturalmente nos modelos das demais fatias, garantindo sua representação indireta nos artefatos produzidos.

