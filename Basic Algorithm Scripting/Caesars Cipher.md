# Caesars Cipher

Um dos mais simples e bastante conhecidos `ciphers` é o `Caesar cipher`, também conhecido como `shift cipher`. Em um `shift cipher` o significado das letras são trocadas por um determinado tamanho.

Um uso moderno é o [ROT13](https://en.wikipedia.org/wiki/ROT13) cipher, onde os valores das letras são trocdas por 13 posições. Sendo assim, 'A' se torna 'N', 'B' vira 'O', e assim por diante.

Escreva uma função que pega uma string `ROT13` codificada como parâmetro de entrada e retorna uma string decodificada. Tdoas as letras estarão em maiúsculo. Não transforme nenhum caractere não-alfanumérico (ex: espaços, pontuação), mas os mesmos devem ser passados.

O código fornecido transforma a entrada (parâmetro da função) em uma matriz (array) para você, chamado `codeArr`. Coloque os valores decodificados na matriz `decodedArr` onde o código fornecido será transformado de volta para uma string.

```js
function rot13(encodedStr) {
  var codeArr = encodedStr.split("");  // String to Array
  var decodedArr = []; // Your Result goes here
  // Only change code below this line



  // Only change code above this line
  return decodedArr.join(""); // Array to String
}

// Change the inputs below to test
rot13("SERR PBQR PNZC");
```

## Solução

Antes de prosseguir, caso não saiba o que é `Caesars Cipher`, recomendo a leitura do [ROT13](https://en.wikipedia.org/wiki/ROT13) cipher no site da **Wikipédia**, o site fornece todas informações sobre o assunto, vale a pena a leitura.

O desafio fica bem simples de solucionar quando já sabemos qual será a saída de uma determinada letra codificada. Sabemos que a entrada pode ser qualquer letra do alfabeto em ordem normal e a saída é o alfabeto com as letras trocadas. Dessa forma basta descobrir a posição da letra codificada no alfabeto com as letras trocadas (saída) e pegar a letra decodificada no alfabeto normal (entrada) usando a mesma posição.

Então crie uma variável `input` que deve conter o alfabeto com todas as letras em ordem normal. E uma variável `output` com todas as letras em ordem trocada.

```js
var input = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    output = "NOPQRSTUVWXYZABCDEFGHIJKLM";
```

Em seguida, usando o método `map()` em `codeArr`, podemos testar cada letra da string fornecida, retornando o caractere em `input` usando o índice de `indexOf()` da string `outupt` (`Linha-10` a seguir).

```js
function rot13(encodedStr) {
  var codeArr = encodedStr.split("");  // String to Array
  var decodedArr = []; // Your Result goes here
  // Only change code below this line

  var input = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
      output = "NOPQRSTUVWXYZABCDEFGHIJKLM";

  decodedArr = codeArr.map(function (val) {
    return input[output.indexOf(val)] || val;
  });

  // Only change code above this line
  return decodedArr.join(""); // Array to String
}

// Change the inputs below to test
rot13("SERR PBQR PNZC");
```

Repare que `val` é o valor de cada letra da string fornecida. Utilizando o comando `return` podemos retornar o caractere decodificado, mas caso o mesmo não exista, o valor retornado será `undefined`, isso significa que é um caractere que não deve ser transformado (ex: espaços, pontuação) e o mesmo deve ser retornado normalmente. Para isso usamos o operador lógico `||`, pois `undefined` é `falsy` então `val` é retornado no lugar.

O resultado da decodificação fica salvo na matriz `decodedArr`, onde o mesmo é convertido para string utilizando `join()` (`Linha-14`).
