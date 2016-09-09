# Chunky Monkey

Escreva uma função que divide uma `matriz` (primeiro argumento) em grupos do tamanho de `size` (segundo argumento) e retorne-as como uma `matriz` multidimensional.

```js
function chunk(arr, size) {
  // Break it up.
  return arr;
}

chunk(["a", "b", "c", "d"], 2);
```

<!-- more -->

Veja aqui alguns links úteis:

[Array.push()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

## Solução I

Primeiro crie uma nova `matriz` vazia que deve guardar outras *matrizes*.

```js
var chunky = [];
```

Em seguida crie um laço `for` que deve iterar no tamanho total de `arr`. Porém, incremente a variável do laço usando o valor de `size`. Você precisa fazer isso pois estaremos usando o método `slice()` de matrizes com a variável `i` do laço como argumento para o método para determinar qual parte da matriz `arr` deve ser adicionada na matriz `chunky`;

Veja a seguir o resultado, não esqueça de retornar `chunky`.

```js
function chunk(arr, size) {
  var chunky = [];
  for (var i = 0; i < arr.length; i += size) {
    chunky.push(arr.slice(i, i+size));
  }
  return chunky;
}

chunk(["a", "b", "c", "d"], 2);
```

## Solução II

Nesta solução usei uma forma mais tradicional. Primeiro precisamos criar uma nova `matriz` que deve guardar os valores temporariamente (`Linha-3`). Em seguida crie um laço `for` que deve iterar no tamanho total de `arr` (`Linha-4`). Dentro do laço insira o valor atual de `arr` na matriz `temp` (`Linha-5`). Logo em seguida criei ma condição que verifica se o tamanho da matriz `temp` é igual à `size`, caso seja verdadeiro, esse é o momento da divisão, então adicione a matriz `temp` na matriz `chunky`, logo reinicie `temp` (`Linha-6 ao 8`).

```js
function chunk(arr, size) {
  var chunky = [];
  var temp = [];
  for (var i = 0; i < arr.length; i++) {
    temp.push(arr[i]);
    if (temp.length === size || i === arr.length - 1) {
      chunky.push(temp);
      temp = [];
    }
  }
  return chunky;
}

chunk(["a", "b", "c", "d"], 2);
```

Repare que na condição da `Linha-6` também estou verificando se `i === arr.length - 1`, isso garante que o último grupo da matriz possa ser adicionado mesmo que a mesma não possua o tamanho de `size`.
