## Pagamento FAILED com erro vazio

## Entendimento do Problema

O cliente relata que os pagamentos foram inicialmente aprovados via API, mas posteriormente receberam o webhook OPENPIX:MOVEMENT_FAILED com status FAILED.

O principal problema é que os campos error.code e providerRejectReason vieram vazios, impossibilitando identificar a causa da falha e orientar o cliente final

# Plano de Investigação

-consultar os logs dos correlation IDs informados para identificar quando o pagamento foi criado, quando virou APROVED, quando virou FAILED qual sistema retornou erro, se houve timeout, se o banco respondeu algo

-verificar o fluxo do pagamento entre aprovação inicial e falha posterior. Muitos sistemas financeiros funcionam de forma assíncrona que iniciam com uma resposta inicial e mudam o confirmação final

-entender em qual etapa falhou e quem rejeitou, quando rejeitou se foi o banco ou se foi interno

-validar se o banco reotornou o motivo de rejeição

## Hipóteses

# Hipótese 1 - Falha no repasse do motivo pelo banco

O banco/parceiro pode ter rejeitado a transação sem retornar código detalhado 

Confirmar se os logs provider também estiverem vazios

# Hipótese 2 - Problema no mapeamento do erro

O sistema pode ter recebido o motivo corretamente mas não propagado para o webhook

Confirmar se o erro existir internamente, mas não no payload enviado

## Resposta do Cliente 

Olá, boa tarde! Tudo bem?

Analisando o comportamento descrito, o APROVED recebido incialmente indica que o pagamento foi aceito para processamento mas q liquidação final acabou falhando posteriormente, por isso o webhook OPENPIX:MOVEMENT_FAILED.

O que não está correto aqui é o fato dos campos error.code e providerRejectReason terem vindo vazios, porque isso impede a classificação adequada da falha

Estamos validando internanmente se:

-o provider/banco retornou o motivo da rejeição
-ou se houve perda dessa informação durante a geração de webhook

Neste momento, ainda não conseguimos afirmar se a causa foi limite, chave inválida ou indisponibilidade do banco recebedor justamente pela ausência do código de rejeição no payload

Vou seguir investigando os correlation IDs enviados e retorno assim que tivermos a causa confirmada ou mais detalhes do provider


# Acompanhamento interno

-validar se o provider retornou código de rejeição
-verificar possível bug no mapeamento do erro para webhook
-avaliar melhoria de fallback quando motivo da falha vier vazio
-revisar documentação do fluxo assíncrono de aprovação/falha
