**A resposta: `rabbit`.**

Isso porque `this` é um objeto antes do ponto, então `rabbit.eat()` modifica `rabbit`.

Busca e execução de propeirdade são duas coisas diferentes.

O método `rabbit.eat` é primeiramente encontrado no protótipo, e então executado com `this=rabbit`.
