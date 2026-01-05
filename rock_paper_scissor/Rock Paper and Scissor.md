# Rock Paper and Scissor 🪨 🧾 ✂️
O famigerado Pedra, papel e tesoura

Um jogo simples, de conhecimento de quase todas as pessoas e ótimo para treinar conceitos simples de programação.

Conceitos utilizados:
* Laço de repetição
* Condições
* Tratamento de dados de entrada

``` python
import random
def rock_paper_scissor():
    jogada = input("Escolha sua jogada: Pedra, Papel ou Tesoura")
    jogada = jogada.lower().strip()
    while(jogada not in ("pedra","papel","tesoura")):
        print("Opção inválida!!\nEscolha uma opção válida.")
        jogada = input("Escolha sua jogada: Pedra, Papel ou Tesoura")
        jogada = jogada.lower().strip()
        
    cpu = ["pedra","papel","tesoura"]
    random.shuffle(cpu)
    jogada_cpu = cpu[0]
    if jogada == jogada_cpu:
        return f"Você: {jogada} x CPU: {jogada_cpu} - Empate"
    elif (jogada == "tesoura" and jogada_cpu == "papel") or (jogada == "papel" and jogada_cpu == "pedra") or (jogada == "pedra" and jogada_cpu == "tesoura"):
        return f"Você: {jogada} x CPU: {jogada_cpu} - Você venceu!"
    else:
        return f"Você: {jogada} x CPU: {jogada_cpu} - Computador venceu!"
    
```
Como chamar:
```python
rock_paper_scissor()
```
