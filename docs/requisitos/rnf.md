# Requisitos Não Funcionais (RNF)

| ID | Categoria | Descrição |
|:---|:---|:---|
| RNF01 | Segurança | Os dados dos devedores devem ser criptografados em repouso (AES-256) seguindo a LGPD. |
| RNF02 | Desempenho | O sistema deve suportar até 10.000 requisições simultâneas no Portal do Devedor. |
| RNF03 | Disponibilidade | O serviço deve estar disponível 99.9% do tempo (SLA). |
| RNF04 | Auditabilidade | Toda alteração no status de um título deve gerar um log de histórico (quem, quando e o quê). |
| RNF05 | Interface | O portal do devedor deve ser "Mobile First" (focado em celulares). |