
[main.py](https://github.com/user-attachments/files/25934132/main.py)
import random

def escolher_palavra():
    palavras = ["python", "desenvolvimento", "algoritmo", "computador", "jogo", "programacao"]
    return random.choice(palavras)  

def jogar_forca():
    palavra = escolher_palavra()
    letras_corretas = ["_"] * len(palavra)
    letras_erradas = []
    tentativas = 0
    max_tentativas = 6

    print("Bem-vindo ao Jogo da Forca!")
    
    while tentativas < max_tentativas:
        print("\nPalavra: " + " ".join(letras_corretas))
        print("Letras erradas: " + ", ".join(letras_erradas))
        exibir_forca(tentativas)
        
        # Solicitar palpite
        palpite = input("\nDigite uma letra: ").lower()

        if palpite.isalpha() and len(palpite) == 1:
            if palpite in letras_corretas or palpite in letras_erradas:
                print("Você já tentou essa letra.")
                continue
            if palpite in palavra:
                for i in range(len(palavra)):
                    if palavra[i] == palpite:
                        letras_corretas[i] = palpite
                print(f"Boa! A letra {palpite} está na palavra.")
            else:
                letras_erradas.append(palpite)
                tentativas += 1
                print(f"A letra {palpite} não está na palavra.")
        else:
            print("Por favor, insira apenas uma letra válida.")
        
        if "_" not in letras_corretas:
            print(f"\nParabéns! Você acertou a palavra: {palavra}")
            break
    else:
        print(f"\nVocê perdeu! A palavra era: {palavra}")
        exibir_forca(tentativas)

# Iniciar o jogo
jogar_forca()
