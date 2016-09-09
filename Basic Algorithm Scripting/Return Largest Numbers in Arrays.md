# Return Largest Numbers in Arrays

Retorne uma matriz contendo o maior número de cada sub-matriz sendo fornecida. Por questão de simplicidade, a matriz fornecida terá exatamente 4 sub-matrizes.

Lembre-se, você pode iterar entre uma matriz com um simples laço `for` e acessar cada membro com a sintaxe de matriz: `arr[i]`.

```js
function largestOfFour(arr) {
  // You can do this!
  return arr;
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
```

Veja aqui alguns links úteis:

[Comparison Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)

## Solução I

Crie uma matriz que deve guardar o maior número de cada sub-matriz.

```js
// Contem o maior número das matrizes
var maiores = [];
```

Em seguida crie dois laços `for`, um vai iterar entre cada sub-matriz da matriz e o interno deve iterar entre cada valor da sub-matriz.

```js
for (var i in arr) {
  for (var j in arr[i]) {
  }
}
```

Dentro do laço externo, crie uma variável temporária que deve guardar o maior número da sub-matriz que iremos verificar. Isso é importante pois o valor temporário precisa ser reiniciado para zero novamente a cada nova iteração, caso contrário, se a variável estivesse declarada fora do laço o último valor seria usado na próxima sub-matriz para comparar o maior número, gerando um bug, pois o último valor não pertence a atual sub-matriz sendo verificada.

```js
for (var i in arr) {
  // Valor temporário que guarda o maior número da sub-matriz
  var maior = 0;
  for (var j in arr[i]) {
  }
}
```

Dentro do laço interno, use um `if` (`Linha-6` a seguir) para verificar e rastrear o maior número da sub-matriz.

```js
for (var i in arr) {
  // Valor temporário que guarda o maior número da sub-matriz
  var maior = 0;
  for (var j in arr[i]) {
    // Verifica por um número maior
    if (arr[i][j] > maior) {
      maior = arr[i][j];
    }
  }
}
```

Logo depois da saída do laço interno, ainda no laço externo, use o método `push()` para inserir o maior número encontrado na matriz `maiores` (`Linha-11` a seguir).

```js
for (var i in arr) {
  // Valor temporário que guarda o maior número da sub-matriz
  var maior = 0;
  for (var j in arr[i]) {
    // Verifica por um número maior
    if (arr[i][j] > maior) {
      maior = arr[i][j];
    }
  }
  // Insere o número maior na matriz de números maiores
  maiores.push(maior);
}
```

Para finalizar, não esqueça de retornar a matriz `maiores`. Veja o código final:

```js
function largestOfFour(arr) {
  // Contem o maior número das matrizes
  var maiores = [];
  // Itera entre cada sub-matriz da matriz
  for (var i in arr) {
    // Valor temporário que guarda o maior número da sub-matriz
   var maior = 0;
    for (var j in arr[i]) {
      // Verifica por um número maior
      if (arr[i][j] > maior) {
        maior = arr[i][j];
      }
    }
    // Insere o número maior na matriz de números maiores
    maiores.push(maior);
  }
  return maiores;
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
```

## Solução II

Esta solução é um pouco mais simples e sofisticada. Apesar de não ter sido comentado na descrição do bonfire, iremos usar o método `reduce()` (`Linha-5` a seguir) de matrizes dentro de um laço `for`.

Veja a seguir como implementei:

```js
function largestOfFour(arr) {
  var maiores = [];
  for (var i in arr) {
    var maior = 0;
    maior = arr[i].reduce(function(a, b) {
      return a >= b ? a : b;
    });
    maiores.push(maior);
  }
  return maiores;
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
```

O método `reduce()` aplica uma função sobre um acumulador e cada valor da matriz (da esquerda para direita, no nosso caso `a` e `b`), deve reduzí-lo a um único valor (que será retornado para a variável `maior`). Dessa forma podemos verificar e retornar o maior número (`Linha-6` acima).
