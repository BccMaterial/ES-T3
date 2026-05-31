# Diagrama de Classes

## Objetivo

Este diagrama modela as principais entidades envolvidas nas três fatias selecionadas:

1. Realização de reserva com pagamento e confirmação;
2. Cancelamento de reserva com aplicação de política de reembolso;
3. Avaliação de hospedagens após estadia.

Foram modeladas apenas as classes necessárias para representar essas funcionalidades, evitando incluir elementos que não participam diretamente das fatias selecionadas.

## Decisões de Modelagem

- A classe `Usuario` foi definida como abstrata, permitindo futuras especializações, como por exemplo "Administrador";
- A integração com pagamento e envio de e-mails foi representada através de interfaces, uma vez que correspondem a serviços externos;
- A relação entre `Reserva` e `Pagamento` foi modelada como composição, pois um pagamento não existe sem uma reserva associada;
- A relação entre `Reserva` e `Avaliacao` foi modelada como composição, pois uma avaliação não existe sem uma reserva associada;
- A política de cancelamento foi separada em uma classe própria para encapsular as regras de negócio.

## Diagrama (PlantUML)

![Diagrama](../images/classes.png)

## Principais Classes

### Cliente

Representa o usuário responsável por buscar hospedagens, realizar reservas, cancelar reservas e registrar avaliações.

### Hospedagem

Representa uma estadia na qual pode ter um tipo de quarto, e diversas reservas, além de informações gerais daquela hospedagem e suas avaliações.

### TipoQuarto

Representa uma categoria de acomodação disponível em uma hospedagem.

### Reserva

Entidade central do sistema. Controla o processo de reserva, seu ciclo de vida e sua associação com pagamento.

### Pagamento

Responsável por registrar transações financeiras associadas às reservas.

### PoliticaCancelamento

Encapsula as regras de negócio relacionadas a cancelamentos e reembolsos.

### Avaliacao

Representa a opinião de um cliente sobre uma hospedagem após a conclusão da estadia.

## Justificativa das Relações

| Relação                       | Tipo        | Justificativa                                                       |
| ----------------------------- | ----------- | ------------------------------------------------------------------- |
| TipoQuarto -> Hospedagem      | Associação  | Uma hospedagem possui um tipo de quarto                             |
| Reserva -> Pagamento          | Composição  | O pagamento está diretamente associado a uma reserva específica.    |
| Cliente -> Reserva            | Associação  | Um cliente pode realizar várias reservas ao longo do tempo.         |
| Hospedagem -> Avaliação       | Associação  | Uma hospedagem pode possuir diversas avaliações.                    |
| Reserva -> Avaliação          | Composição  | Uma avaliação só pode ser criada a partir de uma reserva concluída. |
| Pagamento -> GatewayPagamento | Dependência | O processamento financeiro depende de um serviço externo.           |
| Reserva -> ServicoEmail       | Dependência | O envio da confirmação ocorre através de um serviço externo.        |

