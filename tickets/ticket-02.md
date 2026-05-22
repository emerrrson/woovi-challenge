## Entendimento do Problema

O cliente identificou inconsistência entre o painel e a API

No painel, a frequência "trimestral" aparece normalmente e o fluxo funciona sem erros. Porém, ao tentar usar QUARTERLY via API a requisição retorna 400 invalid enum value (valor que não existe na lista permitida)

O cliente quer entender qual comportamente está correto para conseguir finalizar a integração

# Plano de Investigação

-Validar quais enums são aceitos atualmente pela API (lista de valores permitidos) 

-Comparar a implementação do painel(código/frontend) com a documentação pública e entender o que aconteceu

Talvez alguém  adicionou no frontend mas esqueceu backend/API/doc

Verificar oque: 

Frontend mostra, backend aceita e documentação diz

# Verificar se trimestral está em rollout parcial ou feature flag 

As vezes a funcionalidade trimestral está sendo liberadas aos poucos para os clientes

# Confirmar com o time responsável se existe divergÊncia conhecida entre frontend e API 

Perguntar internamente se já sabem desse problema

## Hipóteses 

# Hipótese 1 - O painel possui opção ainda não liberada na API ?

Confirmaria se o frontend aceitar QUARTERLY mas o backend ainda rejeita o enum

# Hipótese 2 - Doucmentação desatualizada

A API pode já suportar o enum, mas a documentação ainda não foi atualizada

Confirmaria se os testes internos aceitam QUARTERLY

# Hipótese 3 - Feature flag ou rollout parcial

A opção pode estar habilitada apenas no painel 

Confirmaria se houve liberação parcial da funcionalidade

## Resposta ao Cliente

Olá, boa tarde! Obrigado pelo contexto detalhado

No momento, o backend está rejeitando QUARTERLY, então o comportamento válido hoje via API continua sendo apenas os enums documentados.

Vamos validar internamente se a opção "Trimestral" do painel já deveria estar disponível publicamente ou se ainda está em liberação parcial.

Para não bloquear sua integração até sexta, a recomendação no momento é utilizar uma das frequências atualmente aceitas pela API. Assim que eu confirmar o comportamento esperado com o time responsável te atualizo sobre suporte oficial ao QUARTERLY.
