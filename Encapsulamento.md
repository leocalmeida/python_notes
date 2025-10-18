# 🐍 Encapsulamento e Polimorfismo em Java
> Aqui está um simples exemplo do uso do Polimorfismo e Encapsulamento em Python, explicado de um jeito fácil, com exemplos para me ajudar a lembrar.
---

### 🧩 Encapsulamento

O encapsulamento é um dos pilares da Programação Orientada a Objetos (POO).
Ele consiste em proteger os dados de uma classe, permitindo o acesso apenas por meio de métodos controlados, conhecidos como getters e setters.

Em outras palavras, o encapsulamento serve para esconder os detalhes internos de uma classe, garantindo maior segurança e controle sobre como os dados são manipulados.

Diferentemente de linguagens como Java ou C++, que possuem palavras-chave como public, private e protected, Python não implementa encapsulamento estrito (em nível de linguagem) de atributos.

Em vez disso, Python utiliza convenções de nomenclatura para indicar a intenção do desenvolvedor sobre a visibilidade dos atributos:

| Convenção             | Nomenclatura    | Significado                                                                                                                                     | Acesso (Técnico)     | Uso Recomendado                                                                 |
| --------------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ------------------------------------------------------------------------------- |
| Público               | nome_atributo   | O atributo pode ser acessado e modificado livremente a partir de qualquer lugar.                                                                | Direto               | Para atributos que não precisam de controle de acesso.                          |
| Protegido (Convenção) | _nome_atributo  | Indica que o atributo deve ser tratado como "protegido". O acesso direto não é impedido, mas é desaconselhado fora da classe e suas subclasses. | Direto (Convenção)   | Para atributos que devem ser usados internamente ou por subclasses.             |
| Privado (Quase)       | __nome_atributo | Atributo "quase" privado. Python realiza uma "name mangling" (mecanismo de renomeação) para dificultar o acesso direto fora da classe.          | Indireto (Renomeado) | Para atributos internos que não devem ser acessados ou modificados diretamente. |

### 🔒 Exemplo de Encapsulamento
```python
# Atributus públicos
class Carro:
    def __init__(self, marca):
        self.marca = marca  # Atributo Público

meu_carro = Carro("Ford")
print(meu_carro.marca)  # Acesso direto
meu_carro.marca = "Fiat" # Modificação direta
```

```python
# Atributos protegidos (Convenção)
class Conta:
    def __init__(self, saldo_inicial):
        self._saldo = saldo_inicial # Convenção de Protegido

    def depositar(self, valor):
        if valor > 0:
            self._saldo += valor

conta = Conta(100)
print(conta._saldo) # Acesso técnico permitido, mas desaconselhado
```

```python
# Atributos com Name Mangling "Quase privados"
class Funcionario:
    def __init__(self, nome, salario):
        self.__salario = salario # Atributo Quase Privado

    def get_salario(self):
        return self.__salario

    def _get_salario_interno(self):
        # Acesso dentro da classe é normal
        return self.__salario

func = Funcionario("João", 5000)

# print(func.__salario) # ERROR: AttributeError (Acesso direto falha)
print(func.get_salario()) # Acesso através de um método público (recomendado)

# Acesso "forçado" através do nome renomeado:
print(func._Funcionario__salario) # Acesso técnico possível (desaconselhado)
```

### 🛠️ Propriedades (Getters e Setters "Pythônicos")

A forma mais comum e recomendada de implementar o controle de acesso e validação de dados em Python, simulando o encapsulamento, é utilizando a built-in **@property**:

O decorador **@property** permite que você defina métodos (getters, setters e deleters) que podem ser acessados como se fossem atributos, oferecendo um controle elegante sobre a leitura e escrita de dados:
Uma breve explicação

Transforma Métodos em Atributos, permitindo que você chame um método como se ele fosse um atributo (sem usar parênteses ()).

Ao invés de usar de _circulo.get_raio()_, você usa _circulo.raio_.

Podemos pode definir lógica de validação, cálculo ou processamento sempre que o atributo for lido (Getter - @property) ou modificado (Setter - @nome_da_property.setter).

Permite que você altere a implementação interna da classe (por exemplo, de um atributo simples para um valor calculado) sem alterar a forma como o código externo interage com ele.

Em essência, a _@property_ age como um intermediário entre o usuário do objeto e os dados internos (que geralmente usam a convenção de protegido, como self._atributo), garantindo que a integridade dos dados seja mantida.


```python
class Circulo:
    def __init__(self, raio):
        self._raio = raio # Atributo interno, usa convenção de protegido

    @property
    def raio(self):
        """O getter para o raio."""
        return self._raio

    @raio.setter
    def raio(self, novo_raio):
        """O setter para o raio, com validação."""
        if novo_raio > 0:
            self._raio = novo_raio
        else:
            raise ValueError("O raio deve ser positivo.")

c = Circulo(5)
print(c.raio)      # Chama o @property getter
c.raio = 10        # Chama o @raio.setter
# c.raio = -2      # Lança um ValueError
```

---
