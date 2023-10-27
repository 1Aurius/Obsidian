---
type:
---

## Arrays
```js
const numbers = new Array(1,2,3,4);
const fruits  = ['apples','oranges','pear'];


```
## Mudar valores
```js
const fruits  = ['apples','oranges','pear'];

  

fruits[0]= 'grapes';

// + grapes[0] | -apples[0]

  

fruits.push('azul');

// + azul[4]

  

fruits.unshift('strawberries');

// + strawberries[0]

  

fruits.pop();

// - azul

  

console.log(fruits.indexOf('pear'))

// 3

  

console.log(fruits)

// ['strawberries', 'grapes', 'oranges', 'pear']
```