# Modelagem Comportamental — Fatia 1

# Realização de Reserva com Pagamento e Confirmação

## Justificativa da Escolha

Optou-se pelo uso de um **Diagrama de Sequência**, pois esta fatia envolve a interação entre múltiplos componentes do sistema e serviços externos.

O fluxo de reserva atravessa diferentes responsabilidades: consulta de disponibilidade, criação da reserva, processamento do pagamento e envio da confirmação ao cliente. Além disso, existem cenários alternativos relevantes, como indisponibilidade de quartos ou falha no pagamento, que podem ser representados através de fragmentos condicionais da UML (`alt`).

# Diagrama de Sequência

![Diagrama](../images/comportamental-fatia1.png)

# Descrição do Fluxo

1. O cliente solicita a realização de uma reserva informando datas de check-in, check-out e o tipo de quarto desejado.
2. O sistema consulta a disponibilidade para o período solicitado.
3. Caso exista disponibilidade, uma reserva é criada em estado inicial.
4. O sistema inicia o processamento do pagamento através do gateway externo.
5. Se o pagamento for aprovado:
   - a reserva é confirmada;
   - um e-mail de confirmação é enviado;
   - o cliente recebe a confirmação da reserva.
6. Se o pagamento for recusado:
   - a reserva não é confirmada;
   - o cliente é informado sobre a falha.
7. Caso não exista disponibilidade para o período solicitado, o sistema informa imediatamente a indisponibilidade ao cliente.

# Cenários Alternativos Modelados

## A1 — Quarto indisponível

Durante a verificação de disponibilidade, o sistema identifica que não existem vagas para o período solicitado.

Resultado:
- Reserva não é criada;
- Pagamento não é processado;
- Cliente recebe mensagem de indisponibilidade.

## A2 — Pagamento recusado

O gateway retorna uma resposta de rejeição da transação.

Resultado:
- Reserva permanece não confirmada;
- Nenhum e-mail de confirmação é enviado;
- Cliente recebe mensagem de erro de pagamento.
