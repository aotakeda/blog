---
title: O que é escalabilidade?
date: 2020-11-05 08:11:47 -03:00
description: O que faz um software ser considerado escalável, como lidar com escala?
---

Mesmo o sistema sendo confiável hoje não quer dizer que ele será amanhã. A razão da degradação do sistema é um aumento de carga, digamos que o sistema antes tinha 10000 usuários concorrentes e agora possui 500000. Isso é um problema de escalabilidade.

Escalabilidade é o termo usado pra descrever a capacidade do sistema de suportar uma carga cada vez maior. Não faz sentido discutir se um sistema X é escalável e o Y não e sim fazer perguntas do tipo "se o sistema crescer de tal forma, quais são as opções pra aguentar o crescimento?", "como podemos adicionar recursos pra suportar a carga adicional?".

**Carga**

Carga pode ser descrita de forma numérica com base em alguns `parâmetros` dependendo do contexto da arquitetura do sistema. Por exemplo, se for um servidor web, esse parâmetro pode ser o número de requests por segundo, num banco de dados a taxa de leitura/escrita, número de usuários simultâneos num chat, a taxa de hit num cache...

**Performance**

A partir do momento que você definiu a carga no sistema, precisamos definir como seria a questão de performance.

Em sistemas de processamento em batches como Hadoop, o primeiro parâmetro seria `throughput` (número de registros processados por segundo ou o tempo que leva pra rodar um job num dataset de tal tamanho). Já em sistemas online, geralmente a performance é medida pelo tempo de resposta do sistema, ou seja, quanto tempo demora no intervalo entre o cliente enviar um request e receber uma resposta.

Mesmo fazendo o mesmo request várias vezes, o tempo de resposta vai sempre variar um pouco. Então, é necessário pensar não como um número único mas sim uma `distribuição` dos valores (outliers que demoram mais são porque processam mais dados?).

A média pode ser uma forma de medir o tempo de resposta esperado mas é melhor utilizar percentis ou medianas (50% demoram Y, os outros 50% demoram Z).

Para verificar quão ruim estão os outlier você pode olhar os percentis mais altos como 95 (p95), 99 (p99), 99.9 (p999). Por exemplo, se em p95 o tempo de resposta é de 1.5 segundos, isso significa que de 95 requests entre 100 duram menos que isso e 5 de 100 duram 1.5s ou mais.

Esses percentis altos de tempo de resposta são conhecidos como `tail latencies`.

Reduzir tempo de resposta em percentis altos é difícil por eles serem facilmente afetados por eventos aleatórios fora do nosso controle e os benefícios vão diminuindo quanto maior o percentil.

É necessário só uma chamada lenta pra fazer todo o request do usuário final lento. Mesmo se só uma pequena porcentagem das chamadas pro backend forem lentas, a chance de uma chamada ser lenta aumenta se o request do usuário final precisa fazer várias chamadas pro backend. Então, uma maior proporção de requests dos usuários finais acabam sendo lentas (um efeito chamado `tail latency amplification`).

**Latência e tempo de resposta**

Geralmente, são usados como sinônimos, mas não são. O tempo de resposta é o que o cliente "enxerga" incluindo o tempo pra processar o request (tempo de serviço) além de incluir atrasos de rede e de filas.

Latência é a duração que um request espera pra ser processado (esperando serviço).

**Maneiras de lidar com carga**

Sempre comentam sobre a dicotomia entre escalar verficalmente (mudar para uma máquina mais poderosa) e escalar horizontalmente (distribuir a carga por várias máquinas menores). Distribuir a carga por várias máquinas é conhecido por ser uma arquitetura `shared-nothing`. Um sistema pode rodar numa máquina única pode ser mais simples, mas máquinas com grande desempenho podem custar muito dinheiro o que faz com que seja inevitável escalar horizontalmente com cargas muito intensas.

Uma boa arquitetura geralmente envolve uma mistura pragmática entre as duas maneiras: por exemplo, usar várias máquinas boas pode ser mais simples e barato do que um grande número de pequenas máquinas virtuais.

Alguns sistemas são `elásticos`, o que significa que automaticamente adicionam recursos computacionais quando detectam um aumento de carga, enquanto outros sistemas são escalados manualmente (uma pessoa analisa a capacidade e decide adicionar mais máquinas para o sistema). Um sistema elástico pode ser útil se a carga for altamente imprevisível, por outro lado, sistemas escalados manualmente são mais simples e podem ter menor surpresas operacionais.

As arquiteturas de sistemas que operam em grande escala são geralmente muito específicas para cada caso de uso - não existe uma arquitetura genérica, que serve para qualquer caso e seja escalável. O problema a ser enfrentado pode de volume de leituras, de escritas, de dados a serem armazenados, complexidade desses dados, os requisitos de tempo de resposta, padrões de acesso ou uma mistura desses e outros desafios (o que geralmente é o caso).

Uma arquitetura que escala bem para um caso específico, é criada levando em consideração as operações que serão mais comuns e as que serão mais raras (os parâmetros de carga). Se essas considerações estiverem erradas, o esforço de engenharia pra escalar é no mínimo desperdiçado ou no pior caso, contraproducente.