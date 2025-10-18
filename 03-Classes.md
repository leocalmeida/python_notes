# 🐍 Classes em Python
> Aqui está um simples exemplo de uso de classes em Python, explicado de um jeito fácil, com exemplos para me ajudar a lembrar.
---

### 🏗️ O que é uma classe (class)?
É um molde (ou blueprint) para criar objetos.
Define atributos (características) e métodos (ações).

```python
# classe Bicicleta criada em aula
class Bicicleta:
    def __init__(self, cor, modelo, ano, valor):
        self.cor = cor
        self.modelo = modelo
        self.ano = ano
        self.valor = valor

    def buzinar(self):
        print("Plim plim...")

    def parar(self):
        print("Parando bicicleta ...")
        print("Bicicleta parada!")

    def correr(self):
        print("Vrumummmm...")

    def __str__(self):
        return f"{self.__class__.__name__}: " + ', '.join([f"{chave}={valor}" for chave, valor in self.__dict__.items()])
```

### 📐 Estrutura mínima:
```python
# Classe sem inicializador
class NomeDaClasse:
    def metodo(self):
        # ação que o objeto pode executar
```
```python
class NomeDaClasse:
    def __init__(self, atributos...):
        self.atributo = valor  # define características do objeto

    def metodo(self):
        # ação que o objeto pode executar
```

### 🔍 Elementos-Chave na classe Bicicleta:
__init__ → construtor, inicializa atributos quando o objeto é criado.

```python
def __init__(self, cor, modelo, ano, valor):
    self.cor = cor
    self.modelo = modelo
    self.ano = ano
    self.valor = valor
```


**self** → é a referência ao próprio objeto. Similiar ao **this** em Java.

Na criação de um método da classe, é obrigatório passar um primeiro argumento para definir a referência ao próprio objeto.

```python
...
  metodo_um(self):
    pass

  metodo_dois(self, numero):
    print(numero)
...
```

Métodos comuns (buzinar, parar, correr)
São funções dentro da classe que manipulam ou usam os atributos.

__str__ → método especial que define como o objeto é representado como texto.
```python
def __str__(self):
    return f"{self.__class__.__name__}: " + ', '.join([f"{chave}={valor}" for chave, valor in self.__dict__.items()])
````

### ▶️ Criando e usando objetos:

```python
b1 = Bicicleta("Vermelha", "Caloi", 2022, 500)
b1.buzinar()
print(b1)  # Usa __str__
```
