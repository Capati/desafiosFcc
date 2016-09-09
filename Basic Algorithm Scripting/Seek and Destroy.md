# Seek and Destroy

Você será provido de uma matriz inicial (o primeiro argumento da função `destroyer`), seguido de um ou mais argumentos. Remova todos os elementos da matriz inicial que são do mesmo valor que esses argumentos.

```js
function destroyer(arr) {
  // Remove all the values
  return arr;
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```

Veja aqui alguns links úteis:

[Arguments object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments)

[Array.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

## Solução

Primeiro precisamos descobrir quantos argumentos (números que serão removidos da matriz `arr`) foram passados para a função `destroyer`. Toda função possuí um objeto `arguments`. O objeto `arguments` é uma variável local disponível dentro de todas as funções, é como um objeto de matriz (mas não exatamente uma matriz) correspondendo aos argumentos passados para uma função.

Veja uma breve descrição do site **Mozilla Developer Network**:

*"O objeto argumentos não é um Array. É similar a um Array, mas não tem nenhuma propriedade de Array, exceto `length`. Por exemplo, ele não possui o método `push()`. Porém, ele pode ser convertido em um Array real:*

*`var args = Array.prototype.slice.call(arguments);`"*

Mas por questões de performance, não é recomendável usar o método `slice()` em `arguments`.

Então comece criando uma nova matriz com o tamanho de `arguments` menos `1`, pois estaremos descartando `arr` como parte do tamanho total da nova matriz de argumentos. Em seguida vamos usar um laço `for` para iterar entre os argumentos e guardá-los na nova matriz:

```js
// Cria uma matriz com os parâmetros da função
var params = new Array(arguments.length-1);
for (var i = 0; i < params.length; i++) {
  params[i] = arguments[i+1];
}
```

Repare que na `Linha-4` em `arguments[i+1]`, usei `i+1` para evitar pegar a matriz `arr` que já conhecemos, queremos apenas o restante dos argumentos. Poderíamos ter iniciado o laço `for` em `i = 1`, mas isso iria pular o índice `0` da matriz `params`, não queremos isso.

Em seguida use o método `filter()` com um laço `for` para retornar apenas os elementos que escaparam da morte certa, veja a seguir como implementei:

```js
function destroyer(arr) {
  // Cria uma matriz com os parâmetros da função
  var params = new Array(arguments.length-1);
  for (var i = 0; i < params.length; i++) {
    params[i] = arguments[i+1];
  }
  // Remove todos os valores especificados
  return arr.filter(function(valor) {
    for (var i = 0; i < params.length; i++) {
      if (valor === params[i]) {
        return false;
      }
    }
    return valor;
  });
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);
```

Dessa forma estaremos testando cada valor da matriz `arr` contra os argumentos (valores) que guardamos em `params`, recusado os que estiverem no mesmo.

Antes de finalizar, vale ressaltar que ao invés de um laço `for`, podemos usar `indexOf()` da seguinte maneira:

```js
...
return arr.filter(function(valor) {
  if (params.indexOf(valor) !== -1) {
    return false;
  }
  return valor;
});
```
