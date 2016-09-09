# Reverse a Sring

Reverta a string sendo fornecida como argumento para a função.

Talvez você precise converter a string em uma array (matriz) antes de poder revertê-la.

Seu resultado precisa ser uma string.

```js
function reverseString(str) {
  return str;
}

reverseString("hello");
```

Veja aqui alguns links úteis:

[Global String Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

[String.split()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)

[Array.reverse()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)

[Array.join()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

## Solução I

Existem várias maneiras de resolver este problema. A descrição do bonfire sugere converter a string em uma matriz para depois então revertê-la. Podemos fazer uma chamada de métodos sequenciais (method chaining) começando com o método `split()` da seguinte maneira:

```js
function reverseString(str) {
  return str.split("").reverse().join("");
}

reverseString("hello");
```

Usamos o método `split()` para separar cada letra da string `str` e guardar o resultado em uma matriz, em seguida revertemos a matriz usando `reverse()` e por fim `join()` para retornar a matriz revertida como string.

## Solução II

Esta solução apesar de simples é um pouco mais complicada. Basicamente podemos usar um laço `for` para iterar de traz para frente cada letra da string `str` e guardá-las (concatenando) em uma nova string.

```js
function reverseString(str) {
  var reverso = "";
  for (var i = str.length -1; i >= 0; i--) {
    reverso += str[i];
  }
  return reverso;
}

reverseString("hello");
```

