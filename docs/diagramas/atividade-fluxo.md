# Fluxo do Processo de Cobrança (Diagrama de Atividades)

O processo de cobrança é modelado para maximizar os pontos de contato com o devedor antes de recorrer a medidas judiciais/protestos.

### Descrição dos Caminhos Principais:

1. **Fluxo de Sucesso Inicial:**
   - O título entra no sistema -> Disparo da 1ª Carta + Fila de Call Center -> Negociação -> Pagamento -> Repasse à Contratante -> Fim.

2. **Fluxo de Escalonamento (Insucesso):**
   - Falha na 1ª Carta e Falha no Call Center -> Emissão da 2ª Carta -> Se permanecer sem retorno -> Acionamento de Cobrador Externo.

3. **Fluxo de Recuperação Externa:**
   - Cobrador localiza devedor -> Interesse em negociar -> Acordo feito -> Pagamento -> Fim.

4. **Fluxo de Inadimplência Crítica (Protesto):**
   - Devedor não localizado ou recusa acordo -> Título Protestado -> Se pagar pós-protesto (Fim com Sucesso) -> Se não pagar (Devolução do Título e Fim).

### Decisões Críticas (Gateways):
- **Interesse do Devedor:** Define se o fluxo segue para Negociação ou Protesto.
- **Retorno de Carta/Telefone:** Define se o sistema avança para a 2ª via ou aciona o cobrador externo.