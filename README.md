# Banco_python2
saldo = 0
deposito = 0
saldo_atual = []
clientes = []

def depositar():
    global saldo, deposito
    deposito = float(input('Digite a quantia de dinheiro que deseja depositar: R$'))
    if deposito < 0:
        print('Não é possível depositar um valor negativo!')
    else:
        saldo += deposito
        print(f'Depósito de R${deposito:.2f} realizado com sucesso.')

def sacar():
    global saldo
    for c in range(3):
        saque = float(input('Digite a quantia que deseja sacar: R$'))
        if saque > 500:
            print('Você não pode sacar mais de R$500,00 por vez!')
        elif saque > saldo:
            print('Você não pode sacar por falta de saldo!')
            break
        else:
            saldo -= saque
            saldo_atual.append(saque)
            print(f'Saque de R${saque:.2f} realizado com sucesso.')

def extrato():
    print(f'Saldo atual: R${saldo:.2f}')
    print(f'Depósitos totais: R${deposito:.2f}')
    if not saldo_atual:
        print('Nenhum saque realizado.')
    else:
        for s in saldo_atual:
            print(f'Saque: R${s:.2f}')

def cliente():
    nome = input('Digite o nome do cliente: ')
    clientes.append(nome)
    nascimento = input('Digite sua data de nascimento: ')
    clientes.append(nascimento)
    cpf = input('Digite seu CPF (somente números): ')
    clientes.append(cpf)
    end = input('Digite seu endereço: ')
    clientes.append(end)

    print(f'Cliente {nome} cadastrado com sucesso.\n')



def criar_conta():
    cpf=str(input('Digite seu cpf:'))
    for cliente in clientes:
        if cliente['cpf'] == cpf:
            print('CPF já cadastrado! Não é possível criar outra conta com o mesmo CPF.')
        else:
            print('Conta criada com sucesso!')

while True:
    print('MENU:')
    print('1 - Depositar')
    print('2 - Sacar')
    print('3 - Extrato')
    print('4 - Adicionar cliente')
    print('5 - Listar clientes')
    print('6 - Sair')
    op=int(input('Digite uma opção:'))
    
    if op == 1:
        depositar()
    elif op == 2:
        sacar()
    elif op == 3:
        extrato()
    elif op == 4:
        cliente()
    elif op == 5:
        criar_conta()
    elif op == 6:
        break
    else:
        print('Opção inválida! Tente novamente.\n')
