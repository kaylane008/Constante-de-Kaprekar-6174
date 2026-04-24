# Entrada
n = int(input("Digite 4 números distintos: "))

# 1. Validação: positivo
if n <= 0:
    print("Erro: o número deve ser positivo.")

# 2. Validação de faixa
elif n > 9999:
    print("Número inválido: deve ter até 4 dígitos.")

else:
    # Extrair dígitos
    d1 = n // 1000
    d2 = (n % 1000) // 100
    d3 = (n % 100) // 10
    d4 = n % 10

    # 3. Validação de repetição
    if (d1 == d2 == d3) or (d1 == d2 == d4) or (d1 == d3 == d4) or (d2 == d3 == d4):
        print("Número possui muitos dígitos repetidos.")

    else:
        print("\nNúmero informado:", n)
        iteracao = 0

        while n != 6174:

            d1 = n // 1000
            d2 = (n % 1000) // 100
            d3 = (n % 100) // 10
            d4 = n % 10

            # Ordenação
            if d1 > d2:
                d1, d2 = d2, d1
            if d1 > d3:
                d1, d3 = d3, d1
            if d1 > d4:
                d1, d4 = d4, d1
            if d2 > d3:
                d2, d3 = d3, d2
            if d2 > d4:
                d2, d4 = d4, d2
            if d3 > d4:
                d3, d4 = d4, d3

            ndc = d1*1000 + d2*100 + d3*10 + d4
            ndd = d4*1000 + d3*100 + d2*10 + d1

            resultado = ndd - ndc

            iteracao += 1

            print(f"Iteração {iteracao}: {ndd:04d} - {ndc:04d} = {resultado:04d}")

            n = resultado

        print(f"\nConstante de Kaprekar (6174) atingida em {iteracao} iterações.")
