importância: 5

---

# Por que ambos os hamters estão *full* (cheios)?

Nós temos dois hamsters: `speedy` e `lazy` herdando do objeto genérico `hamster`. 

Quando alimentamos um eles, o outro também está *full* (cheio). Por quê? Como podemos arrumar isso?

```js run
let hamster = {
  stomach: [],

  eat(food) {
    this.stomach.push(food);
  }
};

let speedy = {
  __proto__: hamster
};

let lazy = {
  __proto__: hamster
};

// Esse encontrou a comida
speedy.eat("apple");
alert( speedy.stomach ); // apple

// E esse também a possui, por quê? Arrume por favor.
alert( lazy.stomach ); // apple
```

