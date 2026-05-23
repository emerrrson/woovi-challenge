## BaaS: saldo travado em subcontas, operação parada

## Entendimento do problema

CLiente informa que dentro das subcontas há valores que estão aparentemente disponiveis, porém quando inicia a transferência o sistema barra informando que o mesmo não está liberada para saque

Cliente também informa que endpoint aponta como saldo da conta insuficiente

## Plano de investigação

-validar se há diferença entre saldo disponível e extrato das subcontas 
-verificar se há retenções ou saldo bloqueado
-verificar por que endpoint está retornando que saldo da conta está insuficiente mesmo com saldo registrado
-validar internamente se há possibilidade de movimentação para conta master o valor disponível


## Hipóteses 

# Hipótese 1 - Possibilidade de retenção de algum valor

-pode ser que tenha algum valor retido ou bloqueado 

# Hipótese 2 - Saldo ainda não liberado para saque

-os valores podem estar contabilizados no extrato, mas ainda pendentes de liberação operacional

## Resposta ao cliente

Bom dia! Tudo bem?

Obrigado por detalhar o cenário e enviar as informações.

Inicialmente vou validar os saldos das subcontas afetadas para confirmar se existe alguma divergência entre o saldo disponível e o saldo exibido no extrato, já que o endpoint de saque está retornando INSUFFICIENT_BALANCE.

Também vamos verificar se parte desses valores ainda está pendente de liberação operacional ou em processo de conciliação.

Vou seguir com a análise e retorno ainda hoje com mais detalhes.