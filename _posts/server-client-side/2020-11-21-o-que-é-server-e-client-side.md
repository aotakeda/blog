---
title: O que é client e server-side?
date: 2020-11-21 16:50:47 -03:00
description: Quais as diferenças e vantagens de client e server-side?
---

# Client-side (lado do cliente)

`Client-side` se refere a tudo que mostra ou acontece no lado do cliente (dispositivo do usuário final), geralmente é ligado ao `frontend` da aplicação. 

Isso inclui tudo o que o usuário vê (texto, imagens, toda a interface gráfica) assim como qualquer ação que uma aplicação faz dentro do browser do usuário.

HTML e CSS são interpretados pelo browser no `client-side`. Muitas pessoas engenheiras estão incluindo processos `client-side` na arquitetura da aplicação e não deixando tudo `server-side`. Páginas dinâmicas por exemplo geralmente rodam no cliente numa aplicação web moderna. Esses processos são quase sempre feitos em JavaScript.

Um exemplo de processo `client-side` é quando você passar o mouse em cima (`hover`) de uma série no Netflix: a imagem aumenta e as `thumbnails` (miniaturas de imagens) ao lado diminuem. Isso acontece no `client-side` já que o código que criou esse comportamento roda no browser sem qualquer interação com o servidor.

# Server-side (lado do servidor)

`Server-side` se refere a tudo que acontece no servidor, ao invés do cliente. Antigamente, quase toda a lógica de negócio rodava no `server-side` e isso incluía renderização de páginas dinâmicas, interação com banco de dados, autenticação de identidade e notificações push.

O lado negativo de fazer todos os processos `server-side` é que cada request tem que passar do `client-side` para o servidor, toda vez. Isso faz com que a latência aumente. Por isso, aplicações mais modernas rodam bastante código no `client-side`.

`Backend` é o termo geralmente ligado ao `server-side`, mas é importante lembrar que `backend` é o tipo de processo e `server-side` é onde os processos rodam.

[**Fonte**](https://www.cloudflare.com/learning/serverless/glossary/client-side-vs-server-side/)
