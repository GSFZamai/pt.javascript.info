importância: 5

---

# Algoritmo de busca

A tarefa possui duas partes.

Dados os objetos a seguir:

```js
let head = {
  glasses: 1
};

let table = {
  pen: 3
};

let bed = {
  sheet: 1,
  pillow: 2
};

let pockets = {
  money: 2000
};
```

1. Use `__proto__` para atribuir protótipos de uma forma que qualquer propriedade peruisa de propriedade irá seguir o caminho: `pockets` -> `bed` -> `table` -> `head`. Por exemplo, `pockets.pen` deverá ser `3` (encontrado em `table`), e `bed.glasses` deverá ser `1` (encontrado em `head`).
2. Responda a pergunta: é mais rápido acessar `glasses` como `pockets.glasses` ou `head.glasses`? Faça um benchmark se necessário.
