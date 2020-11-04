---
title: O que é confiabilidade ou reliability?
date: 2020-11-04 12:20:47 -03:00
description: O que faz um software ser considerado confiável, quais falhas são aceitáveis?
---

Alguns dos fatores para um software ser considerado `confiável` (reliable) são:

- A aplicação performa sua função como o usuário espera;
- Consegue tolerar que o usuário cometa erros ou use o software de maneiras inesperadas;
- A performance é boa o suficiente pro caso de uso, suportando o volume esperado de dados;
- O sistema previne qualquer abuso ou acesso não-autorizado.

Resumindo, significa que o software continua a funcionar corretamente mesmo quando as coisas dão errado.

Essas coisas que podem dar errado são as chamadas `falhas` (faults), e sistemas que conseguem se antecipar a essas falhas são chamados de `tolerante a falhas` ou `resilientes`. É importante destacar que essas falhas não significam que o sistema pare de proporcionar o serviço ao usuário e que nenhum sistema consegue ser tolerante a todos os tipos de falhas, mas sim a alguns. Muitas dessas falhas são causadas por má gestão de erros.

Nesse quesito é importante aumentar a taxa de falhas de propósito, assim você garante que o sistema é tolerante a falhas e aumenta sua confiança que serão gerenciadas de forma correta quando ocorrerem de fato. [Ver Chaos Monkey](https://github.com/Netflix/chaosmonkey).

Tipos de falhas mais comuns são:

**Falha de hardware**

Exemplos: HD queimou, RAM não está funcionando direito.

Como mitigar: adicionar redundância nos componentes individuais pra reduzir a taxa de falhas no sistema.

Outra maneira de mitigar essas falhas são, adicionalmente ao aumento de redundância, utilizar técnicas de tolerância a falhas como `rolling upgrade` (fazer um patch de segurança, por exemplo, sem ser necessário o downtime).

**Falha de software**

Esse tipo de falha causa muito mais problemas do que as de hardware (que geralmente são pontuais) porque são menos previsíveis e por ter potencial muito maior de causar falha total nos sistemas. Um exemplo de falha de software é de um serviço que o sistema depende começa a ficar mais lento ou para de retornar o que é esperado, ou falhas em cascatas que uma pequena falha em um componente faz acontecer outra em outro componente e vira uma bola de neve.

As falhas de software são mais silenciosas e acontecem quando alguma suposição do sistema deixa de ser verdade (por algum motivo).

As maneiras de evitar esse problema são:

- pensar bem sobre as suposições e interações do sistema;
- bastante cuidado na parte de testes;
- isolamento de processos;
- permitir que os processos que caem sejam reiniciados;
- medir, monitorar e analisar o comportamento do sistema em produção.

**Falhas humanas**

Os sistemas são criados por pessoas e todas erram eventualmente. Pra evitar ao máximo que isso aconteça existem algumas formas:

- Desenhar sistemas de uma forma que minimize oportunidades pra erro. Por exemplo, desenhar abstrações/APIs/interfaces que facilitem fazer a coisa certa e desencoraje o erro. Mas tem a chance de se a interface for muito restritiva, as pessoas podem começar a procurar formas de evitá-la.
- Dissociar os lugares que as pessoas cometem a maior parte das falhas dos lugares que possam causá-las. Fornecer ambientes `sandbox` que as pessoas consigam explorar e experimentar sem qualquer perigo, usando dados reais sem afetar os usuários reais.
- Testar com muito cuidado em todos os níveis, desde testes unitários a testes de integração com outros sistemas, testes automatizados ajudam bastante a cobrir corner-cases, além dos testes manuais.
- Permitir que rollbacks sejam facilmente feitos.
- Monitorar de forma detalhada e clara métricas de perfomance e taxa de erros. Monitoramento pode nos avisar cedo quando alguma coisa tá dando errado e ajuda a diagnosticar o problema.
- Treinamento e gerenciamento de equipe.