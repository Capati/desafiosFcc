## Descrição

Um palíndromo é uma palavra ou sentença que é lida da mesma forma em ambos de frente e ao contrário, ignorando pontuação, case e espaço.

Para verificar se é um palíndromo você precisa remover todos os caracteres não alfanuméricos (pontuação, espaços e símbolos) e converter tudo em minúsculo.

Iremos passar strings em diferentes formatos, como em "racecar", "RaceCar" e "race CAR" além de outros.

```js
function palindrome(str) {
  // Good luck!
  return true;
}



palindrome("eye");
```

Veja aqui alguns links úteis:

[String.replace()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

[String.toLowerCase()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)

## Solução

Primeiro precisamos remover todos os caracteres não alfanuméricos por um caractere vazio mantendo os números (repare na expressão regular, estamos mantendo letras minúsculas, maiúsculas e números) e então logo converter o resultado para minúsculo:

```js
str = str.replace(/[^a-zA-Z0-9]/g, "").toLowerCase();
{% endcodeblock %}

Em seguida crie uma nova variável com o valor de `str` em reverso:

{% codeblock lang:javascript %}
var reverso = str.split("").reverse().join("");
{% endcodeblock %}

Para finalizar, retorne `true` ou `false` conforme a comparação entre as duas strings:

{% codeblock lang:javascript %}
if (str === reverso) {
  return true;
} else {
  return false;
}
```

Caso não queira usar `if else`, veja uma forma mais simples:

{% codeblock lang:javascript %}
return str === reverso;
{% endcodeblock %}

Código final:

```js
function palindrome(str) {
  // Remove caracteres não alfanuméricos
  str = str.replace(/[^a-zA-Z0-9]/g, "").toLowerCase();
  // Guarda a string em reverso em uma nova variável
  var reverso = str.split("").reverse().join("");
  // Verifica se é um palíndromo
  if (str === reverso) {
    return true;
  } else {
    return false;
  }
}

palindrome("eye");
```
