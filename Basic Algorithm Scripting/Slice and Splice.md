# Slice and Splice

Será fornecido para você duas matrizes e um índice.

Use os métodos de matrizes `slice` e `splice` para copiar cada elemento da primeira matriz para a secunda matriz, seguindo a ordem.

Comece inserindo os elementos no índice `n` da segunda matriz.

Retorne a matriz resultante. As matrizes de entrada devem permanecer o mesmo após a execução da função.

## Solução

Comece criando uma nova matriz `newArr` que deve guardar os elementos da segunda matriz, use o método `slice`. Esse procedimento é necessário para que `arr2` não seja modificada quando formos usar `splice` em breve.

```js
var newArr = arr2.slice(0);
```

Em seguida utilize um laço `for` para iterar entre os elementos de `arr1`, dentro do laço atualize `newArr` com os novos elementos utilizando o método `splice` de matrizes, respeitando a posição de `n`.

```js
for (var i = 0; i < arr1.length; i++) {
  newArr.splice(n++, 0, arr1[i]);
}
```

Repare que usamos `n++` para garantir que a cada iteração a posição atual do elementos seja atualizada. Para finalizar, retorne a matriz `newArr` (**Linha-6** a seguir).

```js
function frankenSplice(arr1, arr2, n) {
  var newArr = arr2.slice(0);
  for (var i = 0; i < arr1.length; i++) {
    newArr.splice(n++, 0, arr1[i]);
  }
  return newArr;
}

frankenSplice([1, 2, 3], [4, 5, 6], 1);
```
