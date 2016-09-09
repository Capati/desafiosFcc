# Title Case a Sentence

Retorne a string fornecida com a letra de cada palavra capitalizada (em maiúsculo). Tenha certeza de que o resto da palavra esteja em minúsculo.

Para o propósito deste exercício, você deve capitalizar também palavras de conexão como "the" e "of" (ou "a" e "de").

```js
function titleCase(str) {
  return str;
}

titleCase("I'm a little tea pot");
```

Veja aqui alguns links úteis:

[String.charAt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)

## Solução

Antes de mais nada primeiro precisamos converter toda a string em minúsculo usando o método `toLowerCase()`. Em seguida separamos cada palavra da string em uma matriz usando o método `split()`.

```js
// Coloca tudo em minúsculo e separa as palavras em uma matriz
str = str.toLowerCase().split(" ");
```

Use um laço `for` para iterar entre cada palavra e selecionar a primeira letra usando o método `charAt()` para converter o mesmo  em maiúsculo usando o método `toUpperCase()`. Em seguida use o método `slice()` para concatenar o restante da palavra (a partir da primeira letra).

```js
for (var i = 0; i < str.length; i++) {
  // Coloca a primeira letra da palavra em maiúsculo
  // Em seguida concatena o restante da palavra na string
  str[i] = str[i].charAt(0).toUpperCase() + str[i].slice(1);
}
```

Para finalizar, retorne o resultado usando o método `join()` para converter a matriz de volta para string:

```js
// Retorna uma string com cada palavra separada por espaço
return str.join(" ");
```

Veja o código final:

```js
function titleCase(str) {
  // Coloca tudo em minúsculo e separa as palavras em uma matriz
  str = str.toLowerCase().split(" ");
  for (var i = 0; i < str.length; i++) {
    // Coloca a primeira letra da palavra em maiúsculo
    // Em seguida concatena o restante da palavra na string
    str[i] = str[i].charAt(0).toUpperCase() + str[i].slice(1);
  }
  // Retorna uma string com cada palavra separada por espaço
  return str.join(" ");
}

titleCase("I'm a little tea pot");
```
