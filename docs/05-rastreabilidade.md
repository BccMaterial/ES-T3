# Rastreabilidade

## Objetivo

A rastreabilidade permite verificar a consistência entre os artefatos produzidos ao longo do trabalho de modelagem. Por meio dela, é possível identificar quais casos de uso originaram cada elemento do modelo, quais entidades foram persistidas, quais diagramas comportamentais representam cada fatia selecionada e quais casos de teste validam os requisitos modelados.

Essa relação garante que todas as decisões de modelagem estejam alinhadas aos requisitos definidos no Trabalho 2 e permite avaliar a cobertura dos artefatos produzidos.

---

## Tabela de Rastreabilidade

| Fatia                                                                      | Casos de Uso (T2)                                                    | Classes Envolvidas                                                                                           | Entidades MER                                        | Diagrama Comportamental            | Casos de Teste             |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------- | ---------------------------------- | -------------------------- |
| **Fatia 1 – Realização de Reserva com Pagamento e Confirmação**            | HOTL-005 (Realização de reservas), HOTL-006 (Confirmação de reserva) | Usuario, Cliente, Hospedagem, TipoQuarto, Reserva, Pagamento, ReservaService, GatewayPagamento, ServicoEmail | cliente, hospedagem, tipo_quarto, reserva, pagamento | Diagrama de Sequência (Seção 3.1)  | TC-FATIA1-01, TC-FATIA1-02 |
| **Fatia 2 – Cancelamento de Reserva e Aplicação de Política de Reembolso** | HOTL-007 (Cancelamento de reservas)                                  | Cliente, Reserva, Pagamento, PoliticaCancelamento                                                            | reserva, pagamento, politica_cancelamento            | Diagrama de Estados (Seção 3.2)    | TC-FATIA2-01, TC-FATIA2-02 |
| **Fatia 3 – Avaliação de Hospedagens**                                     | HOTL-008 (Avaliação de estabelecimento)                              | Cliente, Reserva, Hospedagem, Avaliacao                                                                      | cliente, hospedagem, reserva, avaliacao              | Diagrama de Atividades (Seção 3.3) | TC-FATIA3-01, TC-FATIA3-02 |

---

## Cobertura das Fatias Selecionadas

As três fatias escolhidas na Seção 0 encontram-se completamente rastreadas ao longo dos artefatos produzidos:

* **Diagrama de Classes**: representa a estrutura estática necessária para suportar os fluxos das três fatias.
* **MER**: modela as entidades persistentes derivadas das classes de domínio.
* **Diagramas Comportamentais**: representam o comportamento principal de cada fatia utilizando diferentes perspectivas da UML.
* **Casos de Teste**: validam tanto os fluxos principais quanto cenários de exceção e fronteira.

Dessa forma, cada requisito funcional selecionado possui correspondência explícita com elementos estruturais, comportamentais e de validação, garantindo consistência entre os modelos produzidos e o escopo definido para o trabalho.

---

## Matriz Resumida de Cobertura

| Artefato               | Fatia 1 | Fatia 2 | Fatia 3 |
| ---------------------- | :-----: | :-----: | :-----: |
| Seleção de Escopo      |    ✅    |    ✅    |    ✅    |
| Diagrama de Classes    |    ✅    |    ✅    |    ✅    |
| MER                    |    ✅    |    ✅    |    ✅    |
| Diagrama de Sequência  |    ✅    |    ❌    |    ❌    |
| Diagrama de Estados    |    ❌    |    ✅    |    ❌    |
| Diagrama de Atividades |    ❌    |    ❌    |    ✅    |
| Casos de Teste         |    ✅    |    ✅    |    ✅    |

---

## Conclusão

A matriz de rastreabilidade demonstra que todas as fatias selecionadas possuem cobertura completa nos modelos produzidos. Cada requisito funcional escolhido pode ser acompanhado desde sua origem nos casos de uso até sua representação estrutural, comportamental e validação por meio de testes, garantindo coerência entre os artefatos e justificando o recorte adotado para o trabalho.
