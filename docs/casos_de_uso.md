# Casos de Uso (Use Cases) - SIRC

Os casos de uso descrevem as interações entre os atores (Usuários/Sistemas) e o SIRC para atingir objetivos específicos.

## Atores
* **Operador de Call Center:** Profissional que realiza o contato telefônico.
* **Devedor:** Pessoa física ou jurídica com título pendente.
* **Cobrador Externo:** Profissional que realiza visitas presenciais.
* **Sistema de Cartório:** Sistema externo integrado para recebimento de protestos.
* **Administrador:** Gestor da empresa contratante que acompanha os repasses.

---

## UC01: Realizar Negociação de Título (Via Call Center)
**Objetivo:** Registrar o acordo feito entre o operador e o devedor via telefone.

* **Atores:** Operador de Call Center, Devedor.
* **Pré-condições:** Título disponível na fila de discagem e contato estabelecido.
* **Fluxo Principal:**
    1. O Operador localiza o devedor no sistema.
    2. O Sistema exibe o valor atualizado com juros e multas (RN01).
    3. O Operador propõe as opções de parcelamento.
    4. O Devedor aceita uma das opções.
    5. O Sistema gera o termo de acordo e o primeiro boleto.
* **Fluxo Alternativo (Recusa):**
    - Se o devedor não aceitar o acordo, o Operador marca como "Sem Interesse" e o sistema agenda a 2ª Carta ou Cobrador Externo.

---

## UC02: Autoatendimento de Negociação (Portal do Devedor)
**Objetivo:** Permitir que o devedor negocie sua dívida sem interação humana.

* **Atores:** Devedor.
* **Pré-condições:** Devedor acessa o portal via link enviado por WhatsApp/E-mail.
* **Fluxo Principal:**
    1. O Devedor realiza login com CPF/CNPJ e código do título.
    2. O Sistema apresenta o valor da dívida e simulações de desconto para pagamento à vista.
    3. O Devedor seleciona a forma de pagamento (Pix ou Boleto).
    4. O Sistema confirma o acordo e emite o comprovante.
* **Pós-condição:** O título é retirado da fila do Call Center automaticamente.

---

## UC03: Acionar Cobrança Externa
**Objetivo:** Escalar o processo para visita presencial quando os meios remotos falham.

* **Atores:** Sistema (Automático), Cobrador Externo.
* **Pré-condições:** Ausência de retorno da 2ª Carta e insucesso no Call Center.
* **Fluxo Principal:**
    1. O Sistema identifica títulos que atendem aos critérios de falha remota.
    2. O Sistema gera uma Ordem de Serviço (OS) com o último endereço confirmado.
    3. O Cobrador Externo recebe a OS em seu aplicativo móvel.
    4. O Cobrador registra o resultado da visita (Localizado/Não Localizado).

---

## UC04: Automação de Protesto
**Objetivo:** Encaminhar o título para cartório em caso de esgotamento de tentativas.

* **Atores:** Sistema, Sistema de Cartório.
* **Pré-condições:** Recusa de acordo ou quebra de promessa de pagamento.
* **Fluxo Principal:**
    1. O Sistema consolida os dados do título e as tentativas de cobrança frustradas.
    2. O Sistema envia o arquivo digital de protesto para o Cartório.
    3. O Cartório confirma o recebimento e o protocolo.
* **Pós-condição:** Status do título alterado para "Em Protesto".
