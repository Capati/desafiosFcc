# Falsy Bouncer

Remova todos os valores falsy de uma matriz.

Um **valor falsy** é um valor que se traduz em `falso` quando avaliado em um contexto `Boolean`. Valores falsy em javascript são `false`, `null`, `0`, `undefined`, e `NaN`.

```js
function bouncer(arr) {
  // Don't show a false ID to this bouncer.
  return arr;
}

bouncer([7, "ate", "", false, 9]);
```

Veja aqui alguns links úteis:

[Boolean Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)

[Array.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

## Solução

Utilizando o método `filter()` diretamente em `arr` fica muito fácil solucionar este problema. Para descobrir se um valor é **falsy**, é possível usar o objeto `Boolean` como **wrapper** para um *possível* valor booleano, o mesmo deve retornar `false` caso encontre um valor **falsy** (`Linha-4` a seguir).

```js
function bouncer(arr) {
  // Don't show a false ID to this bouncer.
  return arr.filter(function(valor) {
    return Boolean(valor);
  });
}

bouncer([7, "ate", "", false, 9]);
```

O método `filter()` cria uma nova matriz com todos os elementos que passaram ao teste (retornaram `true`) implementado pela função fornecida. Ou seja, a instrução na `Linha-4` deve passar todos os valores da matriz, exceto quando encontrar um valor **falsy**.
