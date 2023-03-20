
1. Vamos adicionar `__proto__`:

    ```js run
    let head = {
      glasses: 1
    };

    let table = {
      pen: 3,
      __proto__: head
    };

    let bed = {
      sheet: 1,
      pillow: 2,
      __proto__: table
    };

    let pockets = {
      money: 2000,
      __proto__: bed
    };

    alert( pockets.pen ); // 3
    alert( bed.glasses ); // 1
    alert( table.money ); // undefined
    ```

2. Nas *engines* modernas, em termos de desempenho, não há diferença se acessarmos uma propriedade de um objeto ou seu protótipo. Elas se lembram onde a propriedade foi encontrada e reutilizam na próxima requisição.

    Por exemplo, para `pockets.glasses` elas se lembram onde encontraram `glasses` (em `head`), e na próxima vez irá buscar exatamente lá. Elas também são inteligentes o suficiente para atuliazar o *cache* interno se algo mudar, então essa otimização é segura.
