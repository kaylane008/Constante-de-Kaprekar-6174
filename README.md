def validar_entrada(num_str):
    # Validação de tipo (inteiro positivo)
    if not num_str.isdigit():
        print("Erro: o valor informado não é um número inteiro positivo.")
        return False

    num = int(num_str)

    # Validação de faixa (0 a 9999)
    if num < 0 or num > 9999:
        print("Erro: o número deve estar entre 0000 e 9999.")
        return False

    # Completar com zeros à esquerda para garantir 4 dígitos
    num_str = num_str.zfill(4)

    # Validação de repetição de dígitos
    contagem = {}
    for d in num_str:
        contagem[d] = contagem.get(d, 0) + 1

    if max(contagem.values()) >= 3:
        print("Erro: o número possui muitos dígitos repetidos.")
        return False

    return True


def kaprekar(num_str):
    print(f"Número informado: {num_str}\n")

    iteracao = 1

    while True:
        # Ordenar dígitos
        asc = ''.join(sorted(num_str))          # crescente
        desc = ''.join(sorted(num_str, reverse=True))  # decrescente

        ndc = int(asc)
        ndd = int(desc)

        resultado = ndd - ndc

        print(f"Iteração {iteracao}: {desc} - {asc} = {str(resultado).zfill(4)}")

        if resultado == 6174:
            break

        # Preparar próxima iteração
        num_str = str(resultado).zfill(4)
        iteracao += 1


# Programa principal
entrada = input("Digite um número de até 4 dígitos: ")

if validar_entrada(entrada):
    entrada = entrada.zfill(4)
    kaprekar(entrada)# Constante-de-Kaprekar-6174
