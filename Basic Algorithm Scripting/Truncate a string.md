# Truncate a string

Separe uma `string` (primeiro argumento) se não for maior que o máximo permitido para a `string` (segundo argumento). Retorne a `string` truncada com "`...`" no final.

Repare que os três pontos no final faz parte do tamanho total da `string`.

Se `num` for menor ou igual que 3, então o tamanho dos três pontos não deve ser adicionado no tamanho da `string`.

```js
function truncate(str, num) {
  // Clear out that junk in your trunk
  return str;
}

truncate("A-tisket a-tasket A green and yellow basket", 11);
```

<!-- more -->

Veja aqui alguns links úteis:

[String.slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
## Solução

Basta usar `if` `else if` e `else` para determinar as condições. Então use o método `slice()` para truncar a `string`.

Veja a seguir o resultado com alguns comentários:

```js
function truncate(str, num) {
  // Não separa a string caso o tamanho da mesma seja menor ou igual que num
  if (str.length <= num) {
    return str;
  } else if (num <= 3) {
    // O tamanho dos três pontos não deve ser adicionado no tamanho da string.
    // Isso garante que pelo menos um caractere seja exibido
    return str.slice(0, num) + "...";
  } else {
    // Separa a string truncando com os três ponto como parte do seu tamanho total
    return str.slice(0, num - 3) + "...";
  }
}

truncate("A-tisket a-tasket A green and yellow basket", 11);
```
