# Trabalho 3 — Modelagem

## Engenharia de Software

### Integrantes do Grupo

- Caio Troiano Collino
- Thiago Pereira Lins
- Vinicius Vianna Egydio

## Sobre o Projeto

O presente repositório contém a entrega do **Trabalho 3 — Modelagem**, da disciplina de Engenharia de Software.

O objetivo deste trabalho é aprofundar a modelagem de um subconjunto representativo do sistema desenvolvido nos Trabalhos 1 e 2, utilizando técnicas de modelagem estrutural, comportamental e de banco de dados.

O sistema modelado é o **StayHub**, uma plataforma para busca, reserva e avaliação de hospedagens.

## Fatias Selecionadas

Foram selecionadas três fatias verticais representativas do domínio:

### Fatia 1 — Realização de Reserva com Pagamento e Confirmação

Fluxo completo de reserva de hospedagem, incluindo:
- consulta de disponibilidade;
- criação da reserva;
- processamento do pagamento;
- envio de confirmação ao cliente.

### Fatia 2 — Cancelamento de Reserva e Aplicação de Política de Reembolso

Fluxo responsável por:
- solicitação de cancelamento;
- validação das regras de cancelamento;
- cálculo e processamento de reembolso.

### Fatia 3 — Avaliação de Hospedagens

Fluxo que permite:
- registro de avaliações;
- validação da elegibilidade do cliente;
- atualização da nota média da hospedagem.

## Estrutura do Repositório

```text
docs/
├── 00-selecao-de-escopo.md
├── 01-diagrama-de-classes.md
├── 02-mer.md
├── 03-comportamental-fatia1.md
├── 03-comportamental-fatia2.md
├── 03-comportamental-fatia3.md
├── 04-casos-de-teste.md
└── 05-rastreabilidade.md

images/
└── diagramas

references.md
```

---

## Documentação

| Documento                                                       | Descrição                               |
| --------------------------------------------------------------- | --------------------------------------- |
| [00 - Seleção de Escopo](docs/00-selecao-de-escopo.md)          | Justificativa das fatias escolhidas     |
| [01 - Diagrama de Classes](docs/01-diagrama-de-classes.md)      | Modelagem estrutural das classes        |
| [02 - MER](docs/02-mer.md)                                      | Modelo Entidade-Relacionamento          |
| [03 - Comportamental Fatia 1](docs/03-comportamental-fatia1.md) | Diagrama de Sequência                   |
| [03 - Comportamental Fatia 2](docs/03-comportamental-fatia2.md) | Diagrama de Estados                     |
| [03 - Comportamental Fatia 3](docs/03-comportamental-fatia3.md) | Diagrama de Atividades                  |
| [04 - Casos de Teste](docs/04-casos-de-teste.md)                | Casos de teste baseados no padrão IEEE  |
| [05 - Rastreabilidade](docs/05-rastreabilidade.md)              | Matriz de rastreabilidade dos artefatos |

## Tecnologias de Modelagem

Os diagramas foram desenvolvidos utilizando:
- PlantUML
- UML 2.x
- Modelo Entidade-Relacionamento (MER)
- Markdown (GitHub Flavored Markdown)

## Cobertura dos Critérios do Trabalho

| Critério                                 | Atendido |
| ---------------------------------------- | :------: |
| Fatia Must Have                          |     ✅    |
| Fatia com múltiplos atores/subsistemas   |     ✅    |
| Fatia com regras de negócio não triviais |     ✅    |
| Diagrama de Classes                      |     ✅    |
| MER                                      |     ✅    |
| Modelagem Comportamental                 |     ✅    |
| Casos de Teste                           |     ✅    |
| Rastreabilidade                          |     ✅    |

