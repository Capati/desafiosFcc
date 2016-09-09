## Factorialize a Number

Retorne o fatorial de um número inteiro.

Se o inteiro é representado com a letra `n`, um fatorial é o produto de todos os números positivos menos que ou igual que `n`.

Fatoriais geralmente são representados com a notação abreviada `n!`

Por exemplo: `5! = 1 * 2 * 3 * 4 * 5 = 120`

```js
function factorialize(num) {

  return num;
}

factorialize(10);
{% endcodeblock %}
```

Veja aqui alguns links úteis:

[Arithmetic Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators)

## Solução I

Podemos usar um laço `for` para iterar entre cada número inteiro até `num`. Veja na `Linha-8` a seguir:

```js
function factorialize(num) {
  var fatorial = 1;
  // Se o número for negativo, rejeita
  if (num < 0) {
    return -1;
  } else {
  // Realiza a multiplicação para gerar o produto de todos os números
    for (var i = 1; i <= num; i++) {
      fatorial *= i;
    }
  }
  return fatorial;
}

factorialize(5);
```

Repare que o valor de `fatorial` começa em 1, isso garante que ao tentar descobrir o fatorial de 1 ou 0, o valor retornado sempre será 1.

## Solução II

Nesta solução usei `recursão`, veja a seguir na `Linha-9`.

```js
function factorialize(num) {
  // Se o número for negativo, rejeita
  if (num < 0) {
      return -1;
      // Se for igual a zero, seu fatorial é 1
    } else if (num === 0) {
      return 1;
    } else {
      return (num * factorialize(num - 1));
    }
}

factorialize(5);
```
