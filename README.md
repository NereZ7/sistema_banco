# sistema_banco
Aprendendo a desenvolver possibilidades.
Uma ajuda fundamental do Tutor Guilherme da DIO!

menu = """

[1] Depositar
[2] Sacar
[3] Extrato
[4] Sair

=> """

saldo = 1000
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "1":
        deposito = float(input("Qual valor deseja despositar? "))

        if deposito > 0:
            saldo += deposito 
            print('Seu saldo atualizado é: R${}'.format(saldo + deposito))
            extrato += f"Deposito: R$ {deposito:.2f}\n"

        else:  
            print("Operação falhou! O valor informado é inválido.")
 
    elif opcao == "2":

        valor = float(input("Qual valor deseja sacar? "))

        excedeu_saldo = valor > saldo 

        excedeu_limite = valor > limite 

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Voce não tem saldo suficiente")

        elif excedeu_limite:
            print("Operacão falhou! O valor de saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1
            print('Voce sacou: R${}'.format(valor))
            print('Seu saldo atual é: R${}'.format(saldo - valor))
        
        else: 
            print("Operação falha! O valor informado é inválido")

    
    elif opcao == "3":
        print("\n=================== EXTRATO ====================")
        print("Não foram realizados movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==================================================")
        


    elif opcao == "4":
        print("Sair")
        break

    else: 
        print("Opção inválida, selecione outra alternativa por favor.")
