Constante de Kaprekar em Python
Descrição

Este programa calcula a constante de Kaprekar (6174) a partir de um número informado pelo usuário.

Regras
O número deve ter até 4 dígitos
Caso o usuário digite menos de 4 dígitos (ex: 234), o número será tratado como 0234
Não pode ter todos os dígitos iguais (ex: 1111)
Funcionamento

O programa:

Separa os dígitos do número
Organiza em ordem crescente e decrescente
Faz a subtração
Repete o processo até chegar em 6174
Conta o número de tentativas
Exemplo

Entrada: 234

Saída:
4320 - 0234 = 4086

8640 - 0468 = 8172

8721 - 1278 = 7443

7443 - 3447 = 3996

9963 - 3699 = 6264

6642 - 2466 = 4176

7641 - 1467 = 6174

6174

tentativas: 7

```python
num = int(input())
aux = num
tentativas = 0

while aux != 6174:
    # SEPARAÇÃO DOS DÍGITOS
    d1 = aux // 1000 % 10
    d2 = aux // 100 % 10
    d3 = aux // 10 % 10
    d4 = aux % 10

    # Teste para dígitos iguais
    if d1 == d2 == d3 == d4:
        aux = int(input("NAO PODE 4 DIGITOS IGUAIS, TENTE NOVAMENTE:"))
    else:
        # ORGANIZAÇÃO POR TROCA (Garante que d1 > d2 > d3 > d4)
        if d1 < d2:
            reserva = d1
            d1 = d2
            d2 = reserva
        if d1 < d3:
            reserva = d1
            d1 = d3
            d3 = reserva
        if d1 < d4:
            reserva = d1
            d1 = d4
            d4 = reserva
        if d2 < d3:
            reserva = d2
            d2 = d3
            d3 = reserva
        if d2 < d4:
            reserva = d2
            d2 = d4
            d4 = reserva
        if d3 < d4:
            reserva = d3
            d3 = d4
            d4 = reserva

        # MONTAGEM DOS NÚMEROS
        n1 = (d1 * 1000) + (d2 * 100) + (d3 * 10) + d4
        n2 = (d4 * 1000) + (d3 * 100) + (d2 * 10) + d1

        aux = n1 - n2
        tentativas = tentativas + 1

        # PROCESSAMENTO
        print(n1, "-", n2, "=", aux)

# SAIDA
print(aux)
print("tentativas:", tentativas)
```
google colab
<img width="677" height="790" alt="Captura de tela 2026-04-22 151241" src="https://github.com/user-attachments/assets/bd608707-c418-4dc9-8b0b-2365c206104f" />
