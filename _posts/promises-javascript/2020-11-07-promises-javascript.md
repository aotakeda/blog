---
title: O que são promises no JavaScript e como funcionam?
date: 2020-11-07 16:05:47 -03:00
description: Promises em JavaScript, como funcionam?
---

Promises em inglês quer dizer `promessas` em português, e é isso que elas propõem: "prometo cumprir algo, mas posso não conseguir".

Quando a Promise consegue cumprir a promessa, ela `cumpre (resolve)` e quando não consegue, ela `rejeita (reject)`.

Vamos ver como isso funciona na prática.

Digamos que quero aprender a programar em JavaScript, isso ficaria assim:

```javascript
const prometoAprenderJavascript = () => {
    return new Promise((resolve, reject) => {
        resolve(console.log('Promessa de aprender JavaScript cumprida.'));
    })
}

prometoAprenderJavascript().then(console.log('Aprendeu JS.'))
```

Agora vamos fazer duas promessas, a segunda depende da primeira ser cumprida.

Primeiro, vamos definir a segunda `promise` e juntar com a primeira.

```javascript
const prometoAprenderJavascript = () => {
    return new Promise((resolve, reject) => {
        resolve(console.log('Promessa de aprender JavaScript cumprida.'));
    })
}

const prometoAprenderNode = () => {
    return new Promise((resolve, reject) => {
        resolve(console.log('Promessa de aprender Node cumprida.'));
    })
}
```

Agora, vamos primeiro aprender JavaScript para **depois** aprender Node.

```javascript
prometoAprenderJavascript().then(() => {
    prometoAprenderNode()
    console.log('Aprendi os dois.')
)}
```

Imagine que não precisaríamos aprender JavaScript antes de Node e poderíamos aprender os dois concorrentemente.

Podemos utilizar o `Promise.all()`:

```javascript
Promise.all([prometoAprenderJavascript(), prometoAprenderNode()]).then(() => {
    console.log('Aprendi os dois concorrentemente.')
})
```

Se você quiser que assim que uma das promises for resolvida, aconteça algo, você pode usar o `Promise.race()`.

```javascript
Promise.race([prometoAprenderJavascript(), prometoAprenderNode()]).then(() => {
    console.log('Assim que alguma das promises terminar, eu aviso.')
})
```

Espero que seja útil!

Até o próximo post.