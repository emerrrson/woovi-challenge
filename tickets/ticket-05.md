## Boleto pago via Pix continua em aberto no DDA

## Entendimento do problema

O cliente informa que boletos emitidos pela WOOVI foram pagos via pix utilizando o QR CODE do boleto, e os pagamentos aparecem corretamente como COMPLETED no painel.

Porém, os boletos continuam aparecendo em aberto no DDA do banco das pagadores, Isso levou um cliente final a realizar o pagamento do mesmo boleto duas vezes

O cliente quer entendero o por que que o boleto não foi baixado no DDA após o primeiro pagamento via PIX e como evitar novos pagamentos duplicados

## Plano de investigação

-Validar o vínculo entre pagamento pix e a baixa do boleto
-verificar se a liquidação via pix está atualizando corretamente o status registral do boleto
-confirmar se houve falha de comunicação com o banco registrado/DDA 
-analisar o caso do pagamento duplicado para validar possibilidade de estorno

## Hipóteses

# Hipótese 1 - Falha na baixa registral do boleto
O pix foi liquidado, mas o boleto não foi marcado como pago no sistema bancário/DDA

Confirmar se o pagamento existe internamente 

# Hipótese 2 - Delay na atualização da DDA 
Pode ter ocorrido atraso entre o pagamento e a atualização do status no banco do pagador

Confirmar se o boleto foi baixado posteriormente

# HIpótese 3 - Inconsistência entre qr code Pix e boleto registrado

O pagamento pix pode não ter acionado corretamente o fluxo de baixa automática do boleto

confirmar se outros casos semelhantes apresentam o mesmo problema

## Resposta ao Cliente

Olá, boa tarde! Tudo bem? 

O pagamento via pix foi liquidado corretamente, mas a baixa do boleto no DDA aparentemente não foi refletida no banco do pagador. Isso explica o boleto continuar aparecendo como "em aberto" e o pagamento duplicado.

Vamos validar;

-o fluxo de baixa registral do boleto;
-possível atraso/falha na atualização do DDA
- e o caso do pagamento duplicado para orientar o estorno

Retorno assim que confirmar os detalhes desses boletos

## Acompanhamento interno

-validar integração de baixa do boleto após pagamento pix
-verificar status registral no banco emissor/DDA
-confirmar fluxo de prevenção de pagamento duplicado
-avaliar necessidade de alerta adicional no painel para cobranças já liquidadas via pix