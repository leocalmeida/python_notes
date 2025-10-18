# 🐍 Classes em Python
> Aqui está um simples exemplo de uso do Polimorfismo em Python, explicado de um jeito fácil, com exemplos para me ajudar a lembrar.
---
### 💡 Polimorfismo em Python
O Polimorfismo (do grego, "muitas formas") é o terceiro pilar fundamental da Programação Orientada a Objetos (POO), ao lado de Encapsulamento e Herança.

O polimorfismo permite que um mesmo nome (como um método ou uma função) possa ser usado para realizar ações ligeiramente diferentes, dependendo do objeto com o qual está interagindo.

Em Python, o polimorfismo é implementado de forma dinâmica e flexível, graças à tipagem dinâmica e ao conceito de Duck Typing.

###Tipos de Polimorfismo em Python
Existem dois contextos principais para entender o polimorfismo em Python:

### ✍️ Polimorfismo por Sobrescrita (Overriding)
Este é o tipo mais clássico, onde uma classe filha (subclasse) fornece uma implementação específica para um método que já foi definido em sua classe mãe (superclasse).

O método tem o mesmo nome e a mesma assinatura (parâmetros), mas o comportamento é diferente na subclasse.

```python
class Animal:
    def fazer_som(self):
        # Implementação padrão na superclasse
        return "Algum som genérico"

class Cachorro(Animal):
    def fazer_som(self):
        # Sobrescrita (Overriding): Comportamento específico do Cachorro
        return "Au Au!"

class Gato(Animal):
    def fazer_som(self):
        # Sobrescrita (Overriding): Comportamento específico do Gato
        return "Miau"

# Demonstração
animais = [Cachorro(), Gato(), Animal()]

for animal in animais:
    # A mesma chamada de método, mas resultados diferentes
    print(f"{animal.__class__.__name__}: {animal.fazer_som()}")

# Saída
# Cachorro: Au Au!
# Gato: Miau
# Animal: Algum som genérico
```

### 🦆 Polimorfismo através de Duck Typing 
Este é o polimorfismo mais "pythônico" e é a base de como o Python trata a compatibilidade de objetos.

O "Duck Typing" (Tipagem de Pato) é resumido pela frase:

"Se parece com um pato, nada como um pato e quack como um pato, então provavelmente é um pato."

No contexto de polimorfismo, significa que Python não se importa com o tipo de um objeto, mas sim com o que ele pode fazer (quais métodos ele implementa).

Se dois objetos de classes totalmente diferentes implementarem um método com o mesmo nome, eles podem ser tratados de forma polimórfica.

```python
class Patinete:
    def mover(self):
        return "O patinete desliza."

class Carro:
    def mover(self):
        return "O carro acelera."

class Barco:
    def mover(self):
        return "O barco navega."

def iniciar_movimento(veiculo):
    """
    Esta função aceita qualquer objeto que implemente o método 'mover()'.
    """
    print(veiculo.mover())

# Demonstração
iniciar_movimento(Patinete())
iniciar_movimento(Carro())
iniciar_movimento(Barco())

```
Neste caso, a função iniciar_movimento funciona corretamente para Patinete, Carro e Barco, embora eles não compartilhem uma classe base comum. 

Isso é o polimorfismo por Duck Typing em ação.

### ➕ Polimorfismo com Funções Built-in
E além disso, utilizamos muito o Polimorfismo em funções Built-in sem nos darmos conta, como por exemplos as funções:

```python

# Função len()
len('Python') # retorna o tamanho da string
len([10,20,30]) # retorna o tamanho da lista
len({1:'a',2:'b',3:'c'}) # retorna o tamanho do dicionário

# Função print()
print("Leonardo") # imprime no console o nome
print(10) # imprime no console o número 10
print([10,20,30]) # imprime no console a lista

# Operador +
1 + 1 # soma o valor
"a"+"b" # concatena os valores
[1]+[2] # soma as listas

```
---
