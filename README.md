<p align="center"><img src="banner picas.png" width="100%"></p>

# Proyecto Final

___

<p align="center"><img src="Picas.png" width="25%"></p>

## 1. Introducción

Para el proyecto final de Introducción a las Ciencias de la Computación y a la Programación, desarrollé en Python un juego llamado **Picas y Fijas**. El objetivo del juego es adivinar un número de cuatro dígitos que no se repiten. El número es generado aleatoriamente por el programa en el modo de un solo jugador, e introducido por el contrincante en el modo de dos jugadores. Las pistas que se le proporcionan al usuario para que adivine correctamente los cuatro dígitos que componen el número y su respectivo orden se llaman *picas* y *fijas*. Las *picas* indican los dígitos que forman parte del número a adivinar, pero no se encuentran en la posición correcta, y las *fijas* son los que cumplen ambas condiciones. Cuando el jugador consigue un total de cuatro fijas, es decir adivina el número, da fin al juego.

## 2. Instrucciones

El jugador cuenta con límite de diez intentos para adivinar el número. En cada intento ingresará un número de cuatro dígitos sin repetir ningún número. Luego, el programa le entregará el número de picas y fijas correspondientes al número ingresado. Al costado derecho de la ventana se irán almacenando los resultados de cada intento para que el jugador los tenga presentes. Cuando el jugador consiga las cuatro fijas se le entragará la puntuación que obtuvo en la partida. Si terminan los diez intentos y no se logró con el objetivo se le revelará cuál era el número correcto.

## 3. Modos de Juego

### 3.1. Un Solo Jugador

En este modo de juego, el jugador tendrá que adivinar un número generado aleatoriamente por la máquina dentro del límite de diez intentos.

### 3.2. Dos Jugadores

Cada jugador ingresará un número para que el otro lo adivine. Ambos tendran los diez intentos y el juego acabará cuando alguno de los dos consiga las cuatro fijas o cuando ambos hayan gastado todos sus intentos. Solo se le entregará puntaje al ganador, y en todos los casos se revelarán ambos números una vez terminado el juego.

## 4. Sistema de Puntuación

<p align="center"><img src="Puntuación.PNG" width="50%"></p>

Al comienzo del juego, el jugador cuenta con doscientos puntos. Por cada intento que utilize se le descuentan veinte. Por cada fija se suman cinco puntos y por cada pica son tres más. Estas sumas y restas dan como resultado el puntaje final obtenido en la partida.

___

## 5. Desarrollo

Como se mencionó anteriormente el programá se desarrolló en python utilizando varias librerías, entre las que destaca [tkinter](https://docs.python.org/2/library/tkinter.html). Tkinter es una librería utilizada para crear [interfaces gráficas de usuario](https://es.wikipedia.org/wiki/Interfaz_gr%C3%A1fica_de_usuario) conocidas también como **GUI** \(del inglés *graphical user interface*).

### 5.1. Librerías

Las librerías utilizadas en el programa fueron: *tkinter* \(GUI), *PIL* \(Insertar imágenes en una ventana de tkinter) y *random* \(para generar el número aleatoriamente).

```python
from tkinter import *
from PIL import ImageTk, Image
from tkinter import messagebox
from random import randint
```

### 5.2. Menú

<p align="center"><img src="Menú.PNG" width="25%"></p>

Lo primero que se hizo fue crear la ventana principal del programa donde quedaría el menú, crear los objetos *(labels y botones)* y asignar los comandos correspondientes.

```python
#Ventana menú
menu = Tk()
menu.tittle('Picas y Fijas')
menu.iconbitmap('picas.ico')
logo = ImageTk.PhotoImage(Image.open('picasblanco.png'))

#Comandos botones
#1. Salir
def salir():
  response = messagebox.askokcancel('Salir del Juego','¿Estás seguro de querer salir?')
  if response == 1:
    menu.quit()
    
#2. Instrucciones
def insbutton():
	messagebox.showinfo('Instrucciones','El juego consiste en adivinar un número de 4 dígitos donde ningún dígito se repite. Las pistas que tenemos para adivinar el número se  llaman picas y fijas. Las picas son aquellos dígitos que si se encuentran en el número original pero no están en la posición correcta. Las fijas son los que se encuentran en la posición que es. Se tiene un número máximo de 10 intentos, en cada intento se le entregan el número de fijas y picas correspondientes. Al lado derecho se almacenan todos los intentos con sus respectivos números de picas(P) y fijas(F). El juego acaba cuando el jugador logre tener en un intento 4 fijas que significa que adivinó el número, o cuando se le acaben los 10 intentos. En el modo de un solo jugador, se tiene que adivinar un número generado aleatoriamente por la máquina; y en el de dos jugadores, cada uno ingresará un número para que el contrario lo adivine, gana el primero que logré las 4 fijas.')
  
#3. Un Jugador
def s_player():

#4. Dos Jugadores
def d_player():

#Objetos
logolabel = Label(menu,bg='blue',image=logo).grid(row=0,column=0)
splayer = Button(menu,text='Un Jugador',bg='blue',fg='white',font='Arial 14 bold',command=s_player).grid(row=1,column=0,sticky=W+E)
dplayer = Button(menu,text='Dos Jugadores',bg='blue',fg='white',font='Arial 14 bold',command=d_player).grid(row=2,column=0,sticky=W+E)
instrucciones = Button(menu,text='Instrucciones',bg='blue',fg='white',font='Arial 14 bold',command=insbutton).grid(row=3,column=0,sticky=W+E)
exit = Button(menu,text='Salir del Juego',bg='blue',fg='white',font='Arial 14 bold',command=salir).grid(row=4,column=0,sticky=W+E)

menu.mainloop()

```

### 5.3. Modo Un Jugador

<p align="center"><img src="Un Jugador.PNG" width="25%"></p>
