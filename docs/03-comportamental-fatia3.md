# Modelagem Comportamental — Fatia 3

# Avaliação de Hospedagens

## Justificativa da Escolha

Foi optado pelo **Diagrama de Atividades**, devido à natureza desta fatia ser um fluxograma que se divide em várias etapas e decisões de negócio.

Este processo envolve, inicialmente, a verificação de elegibilidade do cliente para realizar a avaliação, seguida pela execução desta avaliação, arquivamento de informações e atualização da pontuação da hospedagem.

Com as atividades e nós de decisão é possível descrever perfeitamente as regras de autorização e fluxos de trabalho até a publicação da avaliação.

# Diagrama de Atividades

![Diagrama](../images/comportamental-fatia3.png)

# Descrição do Fluxo

1. O cliente consulta o histórico das reservas.
2. Escolhe uma hospedagem para ser avaliada.
3. Verifica se há uma reserva concluída para essa hospedagem.
4. Em caso positivo:
   - o formulário de avaliação é apresentado;
   - o cliente informa a nota e a observação;
   - o formulário é validado.
5. Ao verificar-se que os dados são válidos:
   - o registro é efetuado;
   - a avaliação é vinculada à reserva;
   - é recolculada a nota da hospedagem;
   - a avaliação é divulgada.
6. Se a reserva ainda não for concluída, então é impedida a avaliação com justificativa apresentada para o usuário.
---

# Decisões Representadas

## D1 — Reserva concluída

O cliente somente pode avaliar uma hospedagem caso possua uma reserva finalizada associada a ela.

### Resultado positivo

Permite prosseguir para o formulário de avaliação.

### Resultado negativo

Impede a criação da avaliação.

## D2 — Dados válidos

Após o preenchimento do formulário, o sistema valida os dados informados.

Exemplos de validações:
- nota dentro do intervalo permitido (1 a 5);
- comentário dentro do limite de caracteres;
- campos obrigatórios preenchidos.

### Resultado positivo

Avaliação é registrada e publicada.

### Resultado negativo

O sistema solicita correção dos dados.

# Regras de Negócio Representadas

## RN-01 — Elegibilidade para avaliação

Somente clientes que concluíram uma reserva podem registrar avaliações para uma hospedagem.

## RN-02 — Associação à reserva

Toda avaliação deve estar vinculada a uma reserva existente e concluída.

## RN-03 — Atualização da nota média

Após o registro de uma nova avaliação, a nota média da hospedagem deve ser recalculada automaticamente.

## RN-04 — Validação dos dados

O sistema não deve permitir o registro de avaliações com dados inválidos ou incompletos.

# Atores Envolvidos

| Ator    | Responsabilidade                                                |
| ------- | --------------------------------------------------------------- |
| Cliente | Solicitar e preencher a avaliação                               |
| Sistema | Validar elegibilidade, registrar avaliação e atualizar métricas |

