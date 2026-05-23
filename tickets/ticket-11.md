## retorna sucesso mas o split não foi aplicado como esperado/charge

## Entendimento do Problema

Cliente enviou um payload JSON para criar uma cobrança com divisão de valores via split, porém os valores retornados pela API ficaram diferentes dos enviados originalmente.

Além disso, a requisição retornou status 200 OK, indicando sucesso, mesmo com divergência nos splits aplicados.

## Plano de investigação

-entender se quando o split ultrapassa o valor da cobrança há validação automática 

-confirmar se há split padrão/parceiro configurado na conta

-comparar payload enviado com a resposta final gerada pela API 

## Hipóteses 

# Hipótese 1 - Valor do split maior que a cobrança

O split enviado (510) ultrapassa o valor total da cobrança (500), então a API pode ter ajustado automaticamente os valores.

# Hipótese 2 - Split automatico configurado na conta

Pode existir configuração adicional de split/parceiro sendo aplicada automaticamente

## Resposta ao Cliente 

Oi! Analisando o payload enviado, identifiquei que o split informado 510 ficou maior que o valor total da cobrança (500).

Vou validar internamente como a API está tratando esse cenário. porque o comportamento esperado pode ser:

-rejeitar a requisição
-ou ajustar automaticamente os splits aplicados

Também vou verificar se existe alguma configuração adicional de split/parceiro ativa na conta, já que a resposta retornou um split extra (SPLIT_PARTNER) além do enviado no payload.

Retorno assim que confirmar a regra aplicada nesse caso.

## Acompanhamento interno

-validar regra de limite de split
-confirmar comportamente esperado para split
-verificar split parceiro/automático configurado

