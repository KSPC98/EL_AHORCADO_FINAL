# Juego del Ahorcado en Python

Este es un juego simple del ahorcado desarrollado en Python. El jugador selecciona un nivel de dificultad y trata de adivinar una palabra oculta letra por letra antes de quedarse sin vidas.

## Funcionalidades Principales

- **Selección de Nivel de Dificultad:** El jugador puede elegir entre tres niveles: fácil, medio y difícil, que determinan la dificultad de la palabra a adivinar.
  
- **Interfaz Gráfica Simple:** Utiliza la consola para mostrar la palabra oculta, las letras usadas, las vidas restantes y el dibujo del ahorcado según las vidas.
  
- **Finalización del Juego:** El juego termina cuando el jugador adivina la palabra completa o pierde todas sus vidas.

## Cómo Usar

1. Ejecutar el script `ahorcado.py`.
2. Seleccionar un nivel de dificultad.
3. Introducir letras para adivinar la palabra oculta.
4. Seguir las instrucciones en pantalla.

## Requisitos

- Python instalado.
- Biblioteca estándar de Python (os, random).

## Autor

Desarrollado por Kevin Perez

## Fecha

Última fecha de actualización: 26/06/2024

## Explicación del código

import os  
import random  

    os: Módulo para interactuar con el sistema operativo y realizar operaciones como limpiar la pantalla.
    random: Módulo para generar números aleatorios, utilizado aquí para seleccionar palabras aleatorias.

def clear_screen():  
    os.system('cls' if os.name == 'nt' else 'clear')  

    Función que limpia la pantalla. Usa os.name para determinar el sistema operativo y ejecuta cls en Windows o clear en sistemas Unix.

adivinar=['PHYTON', 'PROGRAMACION','ORDENADOR', 'AHORCADO', 'JUEGO', 'AUTONOMO', 'PRACTICA', 'DICCIONARIO', 'PROBLEMAS']  

    Lista de palabras que pueden ser seleccionadas para que el jugador las adivine.

def elegir_palabra(nivel):  
    if nivel == 'facil':  
        return random.choice(['PHYTON', 'JUEGO', 'ORDENADOR'])  
    elif nivel == 'medio':  
        return random.choice(['AHORCADO', 'AUTONOMO', 'PRACTICA'])  
    elif nivel == 'dificil':  
        return random.choice(['PROGRAMACION', 'DICCIONARIO', 'PROBLEMAS'])  
    else:  
        return random.choice(adivinar)  

    Retorna una palabra aleatoria dependiendo del nivel seleccionado ('facil', 'medio', 'dificil') o elige una palabra aleatoria de adivinar si el nivel no es válido.

def seleccionar_nivel():  
    while True:  
        clear_screen()  
        print("SELECCIONE UN NIVEL DE DIFICULTAD: ")  
        print("1. FACIL")  
        print("2. MEDIO")  
        print("3. DIFICIL")  
        opcion= input("INGRESE EL NUMERO CORRESPONDIENTE AL NIVEL (1/2/3): ")  
        if opcion == '1':  
            return 'facil'  
        elif opcion == '2':  
            return 'medio'  
        elif opcion == '3':  
            return 'dificil'  
        else:  
            print("OPCION NO VALIDA. INGRESE 1, 2 O 3.")  
            input("PRESIONE ENTER PARA CONTINUAR...")  
            clear_screen()  

    Muestra al usuario las opciones de nivel y espera a que el usuario ingrese una opción válida ('1', '2', '3'). Llama a clear_screen() para limpiar la pantalla antes de imprimir las opciones.

def dibujar_ahorcado(vidas):  
    if vidas == 5:  
        print("  ____ ")  
        print(" |    |")  
        print(" |")  
        print(" |")  
        print(" |")  
        print(" |")  
        print("_|___")  
    elif vidas == 4:  
        print("  ____ ")  
        print(" |    |")  
        print(" |    O")  
        print(" |")  
        print(" |")  
        print(" |")  
        print("_|___")  
    elif vidas == 3:  
        print("  ____ ")  
        print(" |    |")  
        print(" |    O")  
        print(" |    |")  
        print(" |")  
        print(" |")  
        print("_|___")  
    elif vidas == 2:  
        print("  ____ ")  
        print(" |    |")  
        print(" |    O")  
        print(" |   /|")  
        print(" |")  
        print(" |")  
        print("_|___")  
    elif vidas == 1:  
        print("  ____ ")  
        print(" |    |")  
        print(" |    O")  
        print(" |   /|\\")  
        print(" |")  
        print(" |")  
        print("_|___")  
    else:  
        print("  ____ ")  
        print(" |    |")  
        print(" |    O")  
        print(" |   /|\\")  
        print(" |   / \\")  
        print(" |")  
        print("_|___")  

    Imprime el dibujo del ahorcado según el número de vidas restantes (vidas). Cada caso representa un estado diferente del dibujo del ahorcado.

oculta = ['_'] * len(palabra)  
vidas = 5  
usadas = []  

    oculta: Lista que contiene las letras adivinadas y guiones bajos (_) para las letras no adivinadas.
    vidas: Número de vidas restantes del jugador.
    usadas: Lista de letras que el jugador ya ha intentado adivinar.

 while True:  
        clear_screen()  
        dibujar_ahorcado(vidas)  
        print("LA PALABRA A ADIVINAR ES: ", " ".join(oculta))  
        print(f"VIDAS RESTANTES: {vidas}")  
        print(f"LETRAS UTILIZADAS: {' '.join(usadas)}")  
        print()  

        Limpia la pantalla, dibuja el ahorcado, imprime la palabra oculta con guiones y letras adivinadas (oculta), muestra las vidas restantes y las letras usadas.

    Entrada de letra (letra = input("INTRODUZCA UNA LETRA: ").strip().upper()):
        Solicita al jugador ingresar una letra y la convierte a mayúsculas para asegurar la consistencia.

if letra in usadas:  
    print("¡YA HAS INTENTADO CON ESA LETRA!.")  
    input("PRESIONA ENTER PARA CONTINUAR...")  
    continue  

    Verifica si la letra ya ha sido ingresada anteriormente. Si es así, muestra un mensaje y espera a que el jugador presione Enter antes de continuar con el bucle.

if not letra.isalpha() or len(letra) != 1:  
    print("POR FAVOR, INGRESE SOLO UNA LETRA.")  
    input("PRESIONA ENTER PARA CONTINUAR...")  
    continue  

    Verifica si la entrada del jugador no es una letra o si son más de una letra. Muestra un mensaje de error y espera a que el jugador presione Enter antes de continuar con el bucle.

usadas.append(letra)  

    Agrega la letra ingresada a la lista usadas.

if letra in palabra:  
    print(f"LA LETRA '{letra}' ESTÁ EN LA PALABRA SECRETA")  
    for i in range(len(palabra)):  
        if palabra[i] == letra:  
            oculta[i] = letra  

    Verifica si la letra ingresada está en la palabra a adivinar (palabra). Si es así, muestra un mensaje y reemplaza los guiones bajos correspondientes en oculta con la letra correcta.

if '_' not in oculta:  
    clear_screen()  
    print("¡FELICIDADES!¡HAS ADIVINADO LA PALABRA SECRETA!")  
    print(f"¡LA PALABRA ERA '{palabra}'!")  
    break  

    Verifica si ya no hay guiones bajos (_) en oculta, lo que significa que el jugador ha adivinado todas las letras de la palabra. Muestra un mensaje de victoria y termina el juego.

else:  
    print(f"LA LETRA '{letra}' NO ESTÁ EN LA PALABRA SECRETA.")   
    vidas -= 1   
    if vidas == 0:  
        clear_screen()  
        dibujar_ahorcado(vidas)  
        print(f"¡HAZ PERDIDO! ¡LA PALABRA ERA '{palabra}'!")  
        break  

    Si la letra no está en la palabra, muestra un mensaje y disminuye el número de vidas (vidas). Si vidas llega a 0, muestra un mensaje de derrota, dibuja el ahorcado completo y termina el juego.

print ("GRACIAS POR JUGAR EL AHORCADO")  

    Imprime un mensaje de agradecimiento después de que el juego termina, ya sea por victoria o derrota.
