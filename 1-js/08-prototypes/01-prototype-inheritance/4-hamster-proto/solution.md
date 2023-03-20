Vamos observar cuidadosamente no que está acontecendo ao invocar `speedy.eat("apple")`.

1. O método `speedy.eat` é encontrado no protótipo (`=hamster`), então executado com `this=speedy` (o objeto antes do ponto).

2. Então `this.stomach.push()` precisa encontrar a propriedade `stomach` e invocar `push` nele. Ele busca por `stomach` em `this` (`=speedy`), mas nada é encontrado.

3. Então ele segue a cadeia do protótipo e encontra `stomach` em `hamster`.

4. Então ele invoca `push` nele, adicionando a comida no *the stomach of the prototype* (estômago do protótipo).

Portnanto todos os hamsters compartilham um único *stomach* (estômago)!

Ambos para `lazy.stomach.push(...)` e `speedy.stomach.push()`, a propriedade `stomach` é encontrada no protótipo (como não está no próprio objeto), então a nova informação é inserida nele.

Por favor note que que tal situção não ocorre em caso de uma simples atribuição `this.stomach=`:

```js run
let hamster = {
  stomach: [],

  eat(food) {
*!*
    // atribuir a this.stomach em vez de this.stomach.push
    this.stomach = [food];
*/!*
  }
};

let speedy = {
   __proto__: hamster
};

let lazy = {
  __proto__: hamster
};

// Speedy encontrou a comida
speedy.eat("apple");
alert( speedy.stomach ); // apple

// O *stomach* estômago do Lazy está vazio
alert( lazy.stomach ); // <nada>
```

Agora tudo funciona bem, porque `this.stomach=` não executa a busca de `stomach`. O valor é escrito diretamente no objeto `this`.

Também podemos evitar totalmnte o problema ao garantir que cara hamtser tenha seu próprio *stomach* (estômago):

```js run
let hamster = {
  stomach: [],

  eat(food) {
    this.stomach.push(food);
  }
};

let speedy = {
  __proto__: hamster,
*!*
  stomach: []
*/!*
};

let lazy = {
  __proto__: hamster,
*!*
  stomach: []
*/!*
};

// Speedy encontrou a comida
speedy.eat("apple");
alert( speedy.stomach ); // apple

// O *stomach* etômago de Lazy está vazio
alert( lazy.stomach ); // <nada>
```

Como uma solução comum, todas as propriedades que descrevem o estado de um objeto em particular, como `stomach` acima, deve ser escrito naquele objeto. Isso previne tais problemas.
