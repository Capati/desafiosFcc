# Mutations

Retorne `true` se a string no primeiro elemento da matriz contém todas as letras da string no segundo elemento da matriz.

Por exemplo, `["hello", "Hello"]`, deve retornar `true` porque todas as letras na segunda string estão presentes na primeira, ignorando case.

Os argumentos `["hello", "hey"]` deve retornar `falso` porque a string `hello` não contém a letra `y`.

Por fim, `["Alien", "line"]`, deve retornar `true` pois todas as letras em `line` estão presentes em `Alien`.

```js
function mutation(arr) {
  return arr;
}

mutation(["hello", "hey"]);
```

Veja aqui alguns links úteis:

[String.indexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf){:target="_blank"}

## Solução

Pegue as duas palavras da matriz e converta para minúsculo (`Linha-3 e 4`). Em seguida crie um laço `for` (`Linha-7`) para iterar cada letra da palavra de teste (segundo elemento da matriz ou `palavraTeste`). Dentro do laço, crie uma condição que verifica a existência das letras na palavra, retornando `false` caso não exista.

```js
function mutation(arr) {
  // Separa as duas palavras da matriz e converte para minúsculo
  var palavra = arr[0].toLowerCase();
  var palavraTeste = arr[1].toLowerCase();

  // Itera na palavraTeste
  for (var i = 0; i < palavraTeste.length; i++) {
    // Verifica a existência das letras na palavra
    if (palavra.indexOf(palavraTeste[i]) === -1) {
      return false;
    }
  }

  return true;
}

mutation(["hello", "hey"]);
```

Repare que o método `indexOf()` retorna o valor `-1` caso o item (letra) não seja encontrado. Caso a condição não seja verdadeira para retornar `false`, o programa então deve retornar `true` (`Linha-14`).
