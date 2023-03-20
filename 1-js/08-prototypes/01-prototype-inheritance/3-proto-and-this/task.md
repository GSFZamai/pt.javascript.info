importância: 5

---

# Onde é escrito?

Nós temos `rabbit` herdando de `animal`.

Se invorcarmos `rabbit.eat()`, qual objeto recebe a propriedade `full`: `animal` ou `rabbit`? 

```js
let animal = {
  eat() {
    this.full = true;
  }
};

let rabbit = {
  __proto__: animal
};

rabbit.eat();
```
