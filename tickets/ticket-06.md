## Reembolso Pix sem identificação no extrato

## Entendimento do problema

O cliente relata dificuldade para conciliar reembolsos pix no extrato porque algumas linhas aparecem apenas como "Reembolso pix,", sem informações importantes como:

-destinatário
-cpf
-endToEndId;
correlationID;

Como é o terceiro contato sobre o tema, existe um problema recorrente de rastreabilidade/conciliação

## Plano de investigação

-validar quais campos estão disponíveis internamente para esse reembolso
-verificar por que essas informações não aparecem no extrato exportado/exibido
-confirmar se existe limitação atual do produto ou falha no payload do extrato
-avaliar possibilidade de incluir endToEndId e dados do destinatário no extrato

## Hipóteses 

# Hipótese 1 - O extrato não exibe todos os metadados disponíveis
As informações podem existir internamente, mas não serem exibidas ao cliente

# Hipótese 2 - Alguns reembolsos não persistem corretamente os identificadores
O endToEndId pode não estar sendo salvo/vinculado corretamente

## Resposta ao cliente 

Olá, boa tarde! Tudo bem?

Vamos validar internamente por que esses reembolsos estão sendo exibidos sem identificadores como endToEndId e dados do destinatário, porque essas informações são importantes para rastreabilidade no extrato

Enquanto isso, consigo usar o valor + horário do lançamento para localizar a transação internamente e cruzar com o reembolso original.

Também vou registrar esse caso como melhoria de conciliação, já que você comentou que existem várias linhas nesse formato

# Acompanhamento interno

-validar disponibilidade dos metadados do reembolso
-verificar ausência de endToEndId no extrato
-avaliar melhoria de conciliação/exportação
-registrar feedback recorrente do cliente sobre rastreabilidade

