# Repeat a string repeat a string

Repita uma determinada `string` (primeiro argumento) `n` vezes (segundo argumento). Retorne uma `string` vazia se `n` for um número negativo.

```js
function repeat(str, num) {
  // repeat after me
  return str;
}

repeat("abc", 3);
```

<!-- more -->

Veja aqui alguns links úteis:

[Global String Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

## Solução

Crie uma variável que deve guardar a repetição das strings.

```js
var repetido = "";
```

Em seguida crie uma condição que verifica se o total de repetição é um valor negativo, caso seja verdadeiro, retorne uma `string` vazia.

```js
if (num < 0) {
  return "";
}
```

Agora crie um laço `for` para iterar `n` vezes (valor de `num`). Dessa forma podemos concatenar `str` (primeiro argumento da função) `n` vezes na `string` `repetido`.

```js
for (var i = 0; i < num; i++) {
  // Concatena a mesma string n vezes
  repetido += str;
}
```

Para finalizar, retorne a variável `repetido`.

Veja a seguir o código final:

```js
function repeat(str, num) {
  var repetido = "";
  if (num < 0) {
    return "";
  }
  for (var i = 0; i < num; i++) {
    // Concatena a mesma string n vezes
    repetido += str;
  }
  return repetido;
}

repeat("abc", 3);
```
