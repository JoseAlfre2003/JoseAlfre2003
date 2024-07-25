import random

def choose_word():
    palabras = ['gato', 'perro', 'elefante', 'tigre', 'leon']
    return random.choice(palabras)

def jugar_ahorcado():
    palabra = choose_word()
    palabra_adivinada = ['_'] * len(palabra)
    intentos = 6
    letras_usadas = []

    print("¡Bienvenido al juego del ahorcado!")
    
    while intentos > 0 and '_' in palabra_adivinada:
        print(f"Palabra: {' '.join(palabra_adivinada)}")
        print(f"Intentos restantes: {intentos}")
        print(f"Letras usadas: {', '.join(letras_usadas)}")

        letra = input("Ingresa una letra: ").lower()

        if letra in letras_usadas:
            print("Ya has usado esa letra. ¡Intenta con otra!")
            continue
        else:
            letras_usadas.append(letra)

        if letra in palabra:
            print("¡Bien hecho! Has adivinado una letra.")
            for i in range(len(palabra)):
                if palabra[i] == letra:
                    palabra_adivinada[i] = letra
        else:
            print("Letra incorrecta. ¡Perdiste un intento!")
            intentos -= 1
    
    if '_' not in palabra_adivinada:
        print(f"¡Felicidades! Has adivinado la palabra '{palabra}'.")
    else:
        print(f"¡Oh no! Te has quedado sin intentos. La palabra era '{palabra}'.")

if __name__ == "__main__":
    jugar_ahorcado()

