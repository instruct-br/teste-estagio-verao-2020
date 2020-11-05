# Teste Técnico Estágio

Neste repositório você encontra o enunciado do teste técnico para o estágio
de verão 2020 da [Instruct](https://instruct.com.br/).

## O Problema

Uma empresa começou a desenvolver um novo serviço que tem como objetivo
monitorar continuamente a qualidade de servidores de seus clientes.

Este produto vai oferecer 3 planos:

- Ouro
- Prata
- Bronze

O plano Bronze é o padrão quando um novo cliente se registra no produto e ainda
não paga pelo serviço. É o plano "freemium".

Neste sistema um cliente pode pedir a qualquer momento que um de seus
servidores seja analisado. Para atender essa demanda a empresa tem uma
_pool_ de servidores que podem atender os pedidos, cada servidor pode atender
uma quantidade limitada de pedidos por vez.

Para aproveitar melhor o uso da infraestrutura e evitar que alguns recursos
computacionais fiquem ociosos existe apenas uma _pool_ de servidores, portanto
as avaliações feitas em clientes Bronze, Prata ou Ouro partem dos mesmos
servidores.

No entanto, os clientes com planos Ouro ou Prata tem prioridade em relação aos
pedidos dos clientes Bronze, e os clientes com plano Ouro são mais prioritários
do que os clientes Prata.

No caso de múltiplos servidores com a mesma prioridade, o critério de
desempate deve ser a ordem lexicográfica dos nomes dos servidores.

Imagine o exemplo em que chegaram 4 pedidos de análise:

1. servidor Z de um cliente Bronze
2. servidor Y de um cliente Prata
3. servidor X de outro cliente Bronze
4. servidor W de um cliente Ouro

A ordem em que os servidores devem ser analisados é:

`W, Y, X, Z`

## Solução

Você deve implementar um programa em Javascript (ou Typescript) que recebe uma
sequência de comandos na entrada padrão, o programa deve interpretar esses
comandos e imprimir na saída padrão a ordem em que os servidores devem ser
analisados.

Na entrada serão passados dois comandos:
- check
- next

Uma linha que começa com `check` será seguida de um nome, representando o nome
do servidor que será checado e um número para identificar o plano, 
em que 2 = ouro, 1 = prata e 0 = bronze.

Exemplo:
```
check fuzzy-oatmeal-4419 0
```

Um cliente Bronze pediu para checar seu servidor chamado "fuzzy-oatmeal-4419".

Uma linha que começa com `next` deve imprimir na saída uma linha com o nome do 
próximo servidor que deve ser analisado, de acordo com os pedidos que chegaram
através dos comandos `check`.

Exemplo de entrada:
```
check fuzzy-oatmeal-4419 0
check gnarly-frogs-8488 2
next
check high-glove-2433 1
next
check impossible-eye-6212 2
check whimsical-interest-5905 1
check chummy-stew-6922 1
next
next
next
next
```

Saída esperada:
```
gnarly-frogs-8488
high-glove-2433
impossible-eye-6212
chummy-stew-6922
whimsical-interest-5905
fuzzy-oatmeal-4419
```

Para testar seu programa você pode chamá-lo com alguma das entradas de teste
deste repositório:
```
node main.js < samples/01-input.txt
```

A saída deve ser igual à saída do arquivo correspondente, nesse caso o
`samples/01-output.txt`.

Dica: se você estiver desenvolvendo em um ambiente Linux, pode usar esse
atalho para checar a diferença entre a saída do seu programa e a saída
esperada:
```
node main.js < samples/01-input.txt | diff samples/01-output.txt -
```

A saída ficará vazia se a saída do seu programa e a saída esperada (do arquivo
xy-output.txt) estiverem iguais.

## Regras

O seu programa pode usar qualquer módulos nativo da API do Node.js, mas não
pode usar pacotes externos ou embutir o código de pacotes externos na solução.

Sua solução deve ser executável em Node.js 12, 14 ou 15. Não vamos testar seu 
programa em outras versões.

Envie apenas um arquivo .js ou .ts com o código do seu programa anexado numa
resposta do e-mail que você recebeu com instruções sobre este teste.

Se você optar pelo uso de Typescript (arquivo .ts) informe a versão usada
durante o desenvolvimento. Independente de ter usado Javascript ou Typescript
informe a versão do Node.js que você usou durante o desenvolvimento.

---

Boa sorte!
