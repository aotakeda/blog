---
title: O que são e qual a importância de testes unitários?
date: 2020-11-05 08:11:47 -03:00
description: O que são, como fazer e qual a importância de testes unitários.
---

## O que são

Os testes unitários servem para testar uma única parte do seu software (por isso chama unitário, de unidade). Ou seja, verifica o comportamento de uma unidade da aplicação, de forma `independente` de outras partes do software.

## As 3 fases 

Um teste unitário geralmente é dividido em três partes:

1. Inicializar a unidade da aplicação que vai ser testada (`SUT - System Under Test`);
2. Estimular o sistema;
3. Observar o resultado.

Essas três partes são conhecidas como `AAA` - Arrange, Act e Assert.

## Quais aspectos são verificados

Os testes unitários no geral testam dois tipos de comportamentos:

1. Baseado em estado;
2. Baseado em interações.

Se o que for testado produzir resultados ou o estado for correto, o tipo de teste unitário é `baseado em estado`.

Se o que for testado é a invocação dos métodos corretos, o tipo de teste unitário é `baseado em interações`.

## Princípios de um bom teste unitário

Alguns princípios são importantes para que um teste unitário seja de qualidade:

**Legível/fácil de entender**

Algumas coisas precisam estar claras para que o teste unitário seja legível ou de fácil entendimento:

- o que está sendo testado;
- qual o cenário do teste;
- quando o teste falhar, tem que estar claro o que deve ser endereçado;

Com isso, facilita também o debugging do código.

**Rápido**

Quanto mais lento for o teste, maior o risco de alguém pular a parte de rodá-los.

Um único teste geralmente não deixa o sistema lento, mas se for um codebase com centenas ou milhares de testes, e muitos deles não forem rápidos, o tempo fica cada vez maior.

**Confiável**

Se o teste falhar, algo realmente está errado. Quando o teste não foi feito da forma ideal, eles podem falhar mesmo quando não deviam ou vice-versa.

A ordem, quantidade de testes, qual o ambiente ou outros fatores externos não devem afetar o teste, que devem ser independentes.

## A importância dos testes unitários

Muitas pessoas desenvolvedoras de software não dão muita importância para os testes unitários, por exemplo, com motivação de "saber que o código funciona" ou de "não tenho tempo pra fazer isso".

Realmente, entre fazer testes unitário e não fazer, a primeira opção demora mais tempo. O que pode ser contraintuitivo dizer que os testes, na verdade, `te economizam tempo a longo prazo`.

Por exemplo, você pode introduzir algum bug conforme for implementando novas features, assim o seu teste pode pegar esses bugs que talvez demorariam muito mais tempo sendo debuggados pra descobrir onde que deu errado.

Outras vantagens que os testes bem feitos introduzem são a confiança no seu código e indiretamente te ajudam a separar as concerns e sobre o que cada parte do código é responsável no contexto geral.