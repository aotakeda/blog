---
title: O que são e qual a importância de testes unitárioS?
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

## A importância dos testes unitários

Muitas pessoas desenvolvedoras de software não dão muita importância para os testes unitários, por exemplo, com motivação de "saber que o código funciona" ou de "não tenho tempo pra fazer isso".

Realmente, entre fazer testes unitário e não fazer, a primeira opção demora mais tempo. O que pode ser contraintuitivo dizer que os testes, na verdade, `te economizam tempo a longo prazo`.

