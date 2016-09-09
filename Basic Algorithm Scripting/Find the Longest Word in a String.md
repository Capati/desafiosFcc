# Find the Longest Word in a String

Retorne o tamanho da maior palavra em uma `string`.

Sua resposta precisa ser um número

```js
function findLongestWord(str) {

  return str.length;
}

findLongestWord("The quick brown fox jumped over the lazy dog");
```

Veja aqui alguns links úteis:

[String.split()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)

[String.length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length)

## Solução

Primeiro separe as palavras em uma matriz usando o método `split()`.

```js
// Separa as palavras em uma matriz
var palavras = str.split(" ");
```

Crie uma nova variável para guardar o tamanho a ser retornado.

```js
// Guarda o tamanho da maior palavra
var maior = 0;
```

Em seguida use um laço `for` para iterar entre cada palavra da matriz de palavras e verifique o tamanho das palavras comparando com a variável `maior` que deve guardar o maior tamanho atualmente encontrado.

Veja a seguir o código final:

```js
function findLongestWord(str) {
  // Separa as palavras em uma matriz
  var palavras = str.split(" ");
  // Guarda o tamanho da maior palavra
  var maior = 0;
  // Itera entre cada palavra da matriz de palavras
  for (var i in palavras) {
    // Verifica se o tamanho da palavra na matriz é maior que a atual "maior"
    if (palavras[i].length > maior) {
      maior = palavras[i].length;
    }
  }
  return maior;
}

findLongestWord("The quick brown fox jumped over the lazy dog");
```

