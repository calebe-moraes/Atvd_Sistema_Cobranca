# Relatório de Projeto: Sistema Integrado de Recuperação de Crédito (SIRC)

**Data:** 02 de Abril de 2026  
**Status:** Proposta de Modelagem e Otimização de Sistemas  
**Responsável:** Calebe Moraes (CC)
**RA:** 2400974

---

## 1. Introdução
Este relatório apresenta a proposta de modernização e automação do fluxo de cobrança de títulos. O objetivo principal é substituir processos manuais e sequenciais por uma abordagem tecnológica integrada, visando reduzir o tempo de recuperação de crédito (DSO) e os custos operacionais com postagens físicas e mão de obra humana.

## 2. Visão Geral da Solução
A solução proposta, denominada **SIRC**, foca na transição para o modelo **Digital-First**. Em vez de depender exclusivamente de cartas e ligações manuais, o sistema utiliza réguas de cobrança automatizadas e múltiplos canais de contato simultâneos.

### Principais Melhorias:
* **Comunicação Omnichannel:** Substituição de cartas físicas por notificações via WhatsApp API, E-mail e SMS.
* **Paralelismo de Ações:** Execução simultânea de notificações e inclusão na fila de discagem do Call Center.
* **Portal do Devedor:** Ambiente de autoatendimento para negociação e geração de boletos 24/7.

---

## 3. Especificação de Requisitos

### 3.1 Requisitos Funcionais (RF)
O sistema deve ser capaz de realizar as seguintes funções:

| ID | Requisito | Descrição |
|:---|:---|:---|
| **RF01** | Importação de Títulos | Permitir a entrada de dados de dívidas via API ou carga de arquivos CSV/Excel. |
| **RF02** | Automação de Réguas | Disparar a 1ª e 2ª notificação automaticamente conforme prazos configurados. |
| **RF03** | Fila de Call Center | Disponibilizar dados de contato para operadores de forma sincronizada com o envio da 1ª carta. |
| **RF04** | Motor de Cálculo | Calcular juros, multas e correções monetárias em tempo real durante a negociação. |
| **RF05** | Gestão de Protesto | Enviar títulos não negociados automaticamente para cartórios parceiros. |
| **RF06** | Conciliação e Repasse | Identificar pagamentos e agendar a transferência de valores para a empresa contratante. |

### 3.2 Requisitos Não Funcionais (RNF)
Critérios de qualidade e restrições técnicas:

| ID | Categoria | Descrição |
|:---|:---|:---|
| **RNF01** | Segurança/LGPD | Criptografia de dados sensíveis e conformidade com a Lei Geral de Proteção de Dados. |
| **RNF02** | Disponibilidade | O sistema deve garantir 99.9% de uptime para evitar paradas no Call Center e Portal. |
| **RNF03** | Performance | O tempo de resposta para geração de propostas de acordo deve ser inferior a 2 segundos. |
| **RNF04** | Escalabilidade | Capacidade de processar grandes volumes de títulos em datas de pico (ex: início de mês). |

---

## 4. Regras de Negócio (RN)
As diretrizes que regem a lógica do sistema são:

1.  **Regra de Início:** O processo de cobrança deve ser iniciado imediatamente após a inserção do título no banco de dados.
2.  **Simultaneidade:** Ações de notificação digital e cobrança telefônica não são excludentes e devem ocorrer em paralelo.
3.  **Escalonamento Crítico:** O acionamento de um cobrador externo só é permitido após o insucesso confirmado da 2ª notificação e do contato telefônico.
4.  **Inviolabilidade do Acordo:** O descumprimento de um acordo firmado leva o título automaticamente para a fase de **Protesto**.
5.  **Finalização:** O processo só é encerrado com a confirmação do repasse financeiro ou a devolução do título por impossibilidade de recebimento pós-protesto.

---

## 5. Modelagem de Processo (UML)
O fluxo foi desenhado utilizando um **Diagrama de Atividades**, priorizando a clareza nas tomadas de decisão.

* **Ponto de Decisão 1:** Retorno da 1ª Carta / Sucesso no Telefone.
* **Ponto de Decisão 2:** Interesse do devedor em negociar com o cobrador externo.
* **Ponto de Decisão 3:** Pagamento do acordo ou pagamento pós-protesto.

*(O diagrama visual correspondente pode ser visualizado no arquivo `README.md` via código Mermaid).*

---

## 6. Conclusão
A implementação do SIRC representa um salto de maturidade digital para a operação de cobrança. Ao centralizar as regras de negócio em um motor automatizado, a empresa reduz erros humanos, aumenta a taxa de recuperação e garante uma trilha de auditoria completa para cada título processado.
