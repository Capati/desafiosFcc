# Where do I belong

Retorne o menor índice em que um valor (segundo argumento) deve ser inserido em uma matriz (primeiro argumento) assim que for reordenada.

Por exmplo, `where([1,2,3,4], 1.5)` deve retornar `1` porque o mesmo é maior que `1` (índice 0), mas menor que `2` (índice 2).

Da mesma forma, `where([20,3,5], 19)` deve retornar `2` pois assim que a matriz for reordenada ela deve ficar parecida com `[3,5,20]`, sendo assim, `19` é menor que `20` (índice 2) e maior que `5` (índice 1).

```js
function where(arr, num) {
  // Find my place in this sorted array.
  return num;
}

where([40, 60], 50);
```

Veja aqui alguns links úteis:

[Array.sort()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

## Solução

Esta bonfire é até simples de resolver. Primeiro precisamos inserir `num` em `arr` usando o método `push()`. Em seguida basta reordenar a matriz usando `sort()` e `indexOf` para descobrir onde foi parar `num` na matriz já reordenada.

```js
function where(arr, num) {
  // Find my place in this sorted array.
  arr.push(num);
  arr.sort(function(a, b) {
    return a - b;
  });
  return arr.indexOf(num);
}

where([40, 60], 50);
```

Repare na `Linha-4`, para comparar os números, implementei uma função de comparação que simplesmente retorna a subtração de `a` com `b`. Dessa forma é possível retornar uma matriz com os valores em ordem crescente.
