# Casos de Teste

## Fatia 1 — Realização de Reserva com Pagamento e Confirmação

### TC-FATIA1-01

| Campo                           | Conteúdo                                                                                                                                                               |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ID**                          | TC-FATIA1-01                                                                                                                                                           |
| **Fatia / Caso de uso**         | Fatia 1 — HOTL-005 (Realização de reservas) e HOTL-006 (Confirmação de reserva)                                                                                        |
| **Pré-condições**               | Cliente autenticado; hospedagem cadastrada; tipo de quarto disponível para o período solicitado.                                                                       |
| **Dados de entrada**            | Check-in: 10/07/2026; Check-out: 15/07/2026; Tipo de quarto: Suíte Standard; Cartão válido.                                                                            |
| **Passos**                      | 1. Cliente busca hospedagem. <br> 2. Seleciona datas e tipo de quarto. <br> 3. Clica em "Reservar". <br> 4. Informa dados de pagamento. <br> 5. Confirma a operação.   |
| **Resultado esperado**          | Reserva criada com sucesso; pagamento aprovado; reserva marcada como CONFIRMADA; e-mail de confirmação enviado ao cliente.                                             |
| **Critério de aprovação**       | (a) Registro da reserva criado no banco; (b) Status da reserva = CONFIRMADA; (c) Registro de pagamento criado com status APROVADO; (d) Confirmação enviada ao cliente. |
| **Severidade em caso de falha** | Crítica                                                                                                                                                                |

---

### TC-FATIA1-02 (Caso de Fronteira – Pagamento Recusado)

| Campo                           | Conteúdo                                                                                                                        |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **ID**                          | TC-FATIA1-02                                                                                                                    |
| **Fatia / Caso de uso**         | Fatia 1 — HOTL-005 (Realização de reservas)                                                                                     |
| **Pré-condições**               | Cliente autenticado; quarto disponível; gateway configurado para simular pagamento recusado.                                    |
| **Dados de entrada**            | Cartão inválido ou mock retornando PAYMENT_DENIED.                                                                              |
| **Passos**                      | 1. Cliente inicia reserva. <br> 2. Seleciona quarto disponível. <br> 3. Informa forma de pagamento. <br> 4. Confirma pagamento. |
| **Resultado esperado**          | Sistema informa falha no pagamento; reserva não é confirmada; e-mail não é enviado.                                             |
| **Critério de aprovação**       | (a) Mensagem de erro exibida; (b) Reserva não fica com status CONFIRMADA; (c) Nenhum e-mail de confirmação enviado.             |
| **Severidade em caso de falha** | Crítica                                                                                                                         |

---

# Fatia 2 — Cancelamento de Reserva e Aplicação de Política de Reembolso

### TC-FATIA2-01

| Campo                           | Conteúdo                                                                                                     |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **ID**                          | TC-FATIA2-01                                                                                                 |
| **Fatia / Caso de uso**         | Fatia 2 — HOTL-007 (Cancelamento de reservas)                                                                |
| **Pré-condições**               | Reserva CONFIRMADA; cancelamento solicitado dentro do prazo de reembolso integral.                           |
| **Dados de entrada**            | Solicitação de cancelamento realizada 72 horas antes do check-in.                                            |
| **Passos**                      | 1. Cliente acessa a reserva. <br> 2. Solicita cancelamento. <br> 3. Sistema valida política de cancelamento. |
| **Resultado esperado**          | Reserva cancelada; reembolso integral processado; status alterado para CANCELADA.                            |
| **Critério de aprovação**       | (a) Status CANCELADA; (b) Reembolso de 100% do valor pago; (c) Registro de reembolso criado.                 |
| **Severidade em caso de falha** | Alta                                                                                                         |

---

### TC-FATIA2-02 (Caso de Fronteira – Reserva Concluída)

| Campo                           | Conteúdo                                                                                                                  |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **ID**                          | TC-FATIA2-02                                                                                                              |
| **Fatia / Caso de uso**         | Fatia 2 — HOTL-007 (Cancelamento de reservas)                                                                             |
| **Pré-condições**               | Reserva com status CONCLUIDA.                                                                                             |
| **Dados de entrada**            | Solicitação de cancelamento após realização do check-out.                                                                 |
| **Passos**                      | 1. Cliente acessa reserva concluída. <br> 2. Solicita cancelamento.                                                       |
| **Resultado esperado**          | Sistema bloqueia operação e informa que reservas concluídas não podem ser canceladas.                                     |
| **Critério de aprovação**       | (a) Nenhuma alteração no status da reserva; (b) Nenhum reembolso processado; (c) Mensagem informativa exibida ao usuário. |
| **Severidade em caso de falha** | Alta                                                                                                                      |

---

# Fatia 3 — Avaliação de Hospedagens

### TC-FATIA3-01

| Campo                           | Conteúdo                                                                                                                            |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| **ID**                          | TC-FATIA3-01                                                                                                                        |
| **Fatia / Caso de uso**         | Fatia 3 — HOTL-008 (Avaliação de estabelecimento)                                                                                   |
| **Pré-condições**               | Cliente possui reserva concluída na hospedagem avaliada.                                                                            |
| **Dados de entrada**            | Nota: 5; Comentário: "Excelente hospedagem e atendimento."                                                                          |
| **Passos**                      | 1. Cliente acessa histórico de reservas. <br> 2. Seleciona hospedagem. <br> 3. Preenche nota e comentário. <br> 4. Envia avaliação. |
| **Resultado esperado**          | Avaliação registrada e publicada; nota média da hospedagem atualizada.                                                              |
| **Critério de aprovação**       | (a) Avaliação persistida no banco; (b) Avaliação vinculada à reserva; (c) Nota média recalculada corretamente.                      |
| **Severidade em caso de falha** | Média                                                                                                                               |

---

### TC-FATIA3-02 (Caso de Fronteira – Usuário Sem Reserva Concluída)

| Campo                           | Conteúdo                                                                                                           |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **ID**                          | TC-FATIA3-02                                                                                                       |
| **Fatia / Caso de uso**         | Fatia 3 — HOTL-008 (Avaliação de estabelecimento)                                                                  |
| **Pré-condições**               | Cliente não possui reserva concluída para a hospedagem.                                                            |
| **Dados de entrada**            | Nota: 5; Comentário: "Muito boa hospedagem."                                                                       |
| **Passos**                      | 1. Cliente acessa página da hospedagem. <br> 2. Tenta registrar avaliação.                                         |
| **Resultado esperado**          | Sistema impede o cadastro da avaliação e informa que apenas hóspedes com estadia concluída podem avaliar.          |
| **Critério de aprovação**       | (a) Nenhuma avaliação criada; (b) Mensagem de bloqueio exibida; (c) Nenhuma alteração na nota média da hospedagem. |
| **Severidade em caso de falha** | Alta                                                                                                               |

---

# Resumo dos Casos de Teste

| Fatia   | Caso         | Tipo                             |
| ------- | ------------ | -------------------------------- |
| Fatia 1 | TC-FATIA1-01 | Caminho feliz                    |
| Fatia 1 | TC-FATIA1-02 | Caminho de erro                  |
| Fatia 2 | TC-FATIA2-01 | Caminho feliz                    |
| Fatia 2 | TC-FATIA2-02 | Transição crítica de estado      |
| Fatia 3 | TC-FATIA3-01 | Caminho feliz                    |
| Fatia 3 | TC-FATIA3-02 | Regra de autorização (fronteira) |

