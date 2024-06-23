El código implementa el juego del ahorcado utilizando Python. Comienza limpiando la pantalla y solicitando al usuario que ingrese una palabra. Luego, utiliza un ciclo while para permitir que el usuario adivine letras hasta que adivine la palabra completa o cometa suficientes errores para perder el juego. El progreso del juego se muestra en la pantalla y se limpia después de cada interacción para mantener la interfaz limpia y clara para el jugador. Acontinuación se explica cada linea codigo y cual es el proposito:

import os   
-Propósito: Se importa la biblioteca os, que permite interactuar con el sistema operativo. En este caso, se utilizará para limpiar la pantalla de la consola.

def clear_screen():
    os.system('cls' if os.name == 'nt' else 'clear')   
-Propósito: Define una función llamada clear_screen() que utiliza os.system() para ejecutar el comando de limpieza de pantalla específico del sistema operativo (cls en Windows y clear en sistemas Unix/Linux).

clear_screen()   
-Propósito: Limpia la pantalla de la consola al inicio del programa, proporcionando una interfaz limpia para que el usuario pueda interactuar.

palabra = input("INGRESE PALABRA A SER ADIVINADA: ")   
-Propósito: Solicita al usuario que ingrese una palabra que desea que otro jugador adivine. La palabra ingresada se guarda en la variable palabra.

oculta = ['_'] * len(palabra)   
-Propósito: Crea una lista llamada oculta que contiene guiones bajos (_) con la misma longitud que la palabra ingresada por el usuario. Esta lista representará la palabra a adivinar, con las letras adivinadas reveladas y las letras no adivinadas ocultas por guiones bajos.

while True:   
-Propósito: Inicia un ciclo infinito que representa el juego principal del ahorcado. Este ciclo continuará ejecutándose hasta que el jugador gane o pierda el juego.

print("LA PALABRA A ADIVINAR ES: ", " ".join(oculta))   
print()   
letra = input("INTRODUZCA UNA LETRA: ")   
clear_screen()   
-Propósito: Imprime en la pantalla la palabra a adivinar, representada por guiones bajos y letras adivinadas hasta el momento. Luego, solicita al usuario que ingrese una letra para intentar adivinar la palabra oculta. Después de que el usuario ingresa la letra, se limpia la pantalla con clear_screen() para proporcionar una interfaz limpia para la próxima interacción.

if not letra.isalpha() or len(letra) != 1:   
    print("POR FAVOR, INGRESE SOLO UNA LETRA.")   
    continue   
-Propósito: Verifica si la entrada del usuario (letra) es una letra (no un número u otro carácter) y si es solo una letra. Si la entrada no cumple con estos criterios, imprime un mensaje de error y continua con la próxima iteración del ciclo while para que el usuario vuelva a ingresar una letra válida.

if letra in palabra:   
    # Contenido si la letra está en la palabra   
else:   
    # Contenido si la letra no está en la palabra   
-Propósito: Comprueba si la letra ingresada por el usuario está presente en la palabra a adivinar (palabra). Dependiendo de si la letra está en la palabra o no, se actualiza la lista oculta para revelar la letra adivinada o se procede a mostrar un mensaje indicando que la letra no está en la palabra.

if '_' not in oculta:   
    # Contenido si se adivinó completamente la palabra   
else:   
    # Contenido si no se adivinó completamente la palabra   
-Propósito: Verifica si ya se han adivinado todas las letras de la palabra (_ no está presente en oculta). Si todas las letras han sido adivinadas, muestra un mensaje de victoria y termina el juego. Si todavía quedan guiones bajos en oculta, verifica si el jugador ha perdido (muestra la palabra completa).

print("GRACIAS POR JUGAR EL AHORCADO")   
-Propósito: Imprime un mensaje de agradecimiento al jugador por participar en el juego del ahorcado después de que se haya determinado si ganó o perdió el juego.
