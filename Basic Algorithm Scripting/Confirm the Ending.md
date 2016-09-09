# Confirm the Ending

Verifique se uma `string` (primeiro argumento) termina com a `string` alvo sendo fornecida (segundo argumento).

```js
function end(str, target) {
  // "Never give up and good luck will find you."
  // -- Falcor
  return str;
}

end("Bastian", "n");
```

Veja aqui alguns links úteis:

[String.substr()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substr)

## Solução

Podemos resolver este problema tudo em apenas uma linha. Utilizando o método `substr()` de `strings` podemos verificar se o final de `str` é igual a variável `target`, retornando `true` ou `false` dependendo da condição.

```js
function end(str, target) {
  return str.substr(-target.length) === target ? true : false;
}

end("Bastian", "n");
```

Repare como usamos o método `substr()`, ele retorna os caracteres em uma `string` iniciando pelo local especificado até o número especificado de caracteres. No nosso caso usei o operador `-` em `-target.length` para converter o tamanho da *string* alvo para um valor negativo. Quando o método `substr()` usa um valor negativo, ele começa a contar o índice a partir do fim da `string` de traz para frente.
