
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


from abc import ABC, abstractmethod

# Classe base abstrata Pagamento
class Pagamento(ABC):
    @abstractmethod
    def processar_pagamento(self):
        pass 

class PagamentoCartaoCredito(Pagamento):
    def __init__(self, numero_cartao: int):
        self.numero_cartao = numero_cartao  

    def processar_pagamento(self):
        print(f"O pagamento do cartão {self.numero_cartao} foi processado com sucesso!")

class PagamentoBoleto(Pagamento):
    def __init__(self, codigo_boleto: int):
        self.codigo_boleto = codigo_boleto  

    def processar_pagamento(self):
        print(f"O pagamento do boleto {self.codigo_boleto} foi processado com sucesso!") 

class PagamentoPix(Pagamento):
    def __init__(self, chave_pix: str):
        self.chave_pix = chave_pix  

    def processar_pagamento(self):
        print(f"O pagamento via Pix com chave {self.chave_pix} foi processado com sucesso!")  

def processar(pagamento: Pagamento):
    pagamento.processar_pagamento()  

# Testando o polimorfismo com instâncias das subclasses
pagamento_cartao = PagamentoCartaoCredito(1234567890123456)
pagamento_boleto = PagamentoBoleto(987654321)
pagamento_pix = PagamentoPix("chave@pix.com")

processar(pagamento_cartao)
processar(pagamento_boleto)
processar(pagamento_pix)
```

## Perguntas para Reflexão

1. **O que acontece se você adicionar um novo método de pagamento sem modificar a função `processar`?**  
   **Resposta**: O código continua funcionando normalmente desde que a nova subclasse implemente o método `processar_pagamento`.

2. **Como o polimorfismo ajuda a manter o código flexível e extensível?**  
   **Resposta**: O polimorfismo permite que os métodos específicos de cada subclasse sejam chamados, mantendo o código flexível. Novas classes de pagamento podem ser adicionadas sem precisar alterar a função `processar`, tornando o código extensível.

3. **Qual é a diferença entre a função `processar` e os métodos `processar_pagamento` nas subclasses?**  
   **Resposta**: Os métodos `processar_pagamento` são implementações específicas de cada forma de pagamento, enquanto `processar` é uma função externa que recebe qualquer objeto do tipo `Pagamento` e chama seu método `processar_pagamento`.

4. **Como você pode garantir que todos os métodos de pagamento implementem o método `processar_pagamento` corretamente?**  
   **Resposta**: Para garantir que todas as subclasses implementem `processar_pagamento`, podemos transformar `Pagamento` em uma classe abstrata usando o módulo `abc`. Assim, `processar_pagamento` se torna um método abstrato, e cada subclasse é obrigada a implementá-lo, evitando omissões e garantindo consistência no código.
