
# Desafio de Programação Orientada a Objetos em Python

## Instruções

1. Crie uma classe base chamada `Pagamento`:
   - A classe deve ter um método chamado `processar_pagamento` que não faz nada (use `pass`).

2. Crie subclasses de `Pagamento` para diferentes métodos de pagamento:
   - **PagamentoCartaoCredito**
     - Deve ter um atributo `numero_cartao` para armazenar o número do cartão.
     - O método `processar_pagamento` deve exibir uma mensagem indicando que o pagamento com cartão de crédito foi processado.
   - **PagamentoBoleto**
     - Deve ter um atributo `codigo_boleto` para armazenar o código do boleto.
     - O método `processar_pagamento` deve exibir uma mensagem indicando que o pagamento com boleto foi processado.
   - **PagamentoPix**
     - Deve ter um atributo `chave_pix` para armazenar a chave Pix.
     - O método `processar_pagamento` deve exibir uma mensagem indicando que o pagamento via Pix foi processado.

3. Crie uma função `processar` que aceita um objeto do tipo `Pagamento` e chama o método `processar_pagamento` desse objeto:
   - A função deve ser capaz de lidar com qualquer tipo de pagamento que herda da classe `Pagamento`.

4. Crie objetos das subclasses `PagamentoCartaoCredito`, `PagamentoBoleto` e `PagamentoPix` e teste o polimorfismo:
   - Crie pelo menos um objeto de cada subclasse e passe-os para a função `processar` para verificar se o polimorfismo está funcionando corretamente.
