# tp0

1.**Paso 0**

  1.ItemA
  Compilacion del programa Hola Mundo con y sin valgrind
    ![Compilacion del programa Hola mundo con y sin Valgrind](https://github.com/agustinaa235/tp0/blob/master/HolaMundoConYSinValgrind.png)
    
  
    
 1.ItemB
 que es Valgrind?
 
 Valgrind es una herramienta para los porgramadores en la cual nos ayuda a detectar perdidas de memoria en nuestro codigo.
 A su vez nso ayuda detectar fallas en el codigo. Por ejemplo cuando estamos accediendo a memoria que no pedimos o estamos
 pisando otras variables.
 
 La funcion sizeof() nos devuelve la cantidad de bytes que ocupa el tipo de dato que le estemos pasando.
 El tamanio depende de la arquitectura y del compilador.
 En el caso de ser in int, sizeof(int) devuelve 4 bytes mientras que en el caso de pasarle el tipo de dato char 
 nos devuelve 1 byte.
 
 
 2.**Paso 1**
 
   2. **Sercom Errores de generacion y normas de programacion
   
   Al subir el zip del paso 1 al sercom, cuando compila informa lo siguiente:
   
  ![Errores paso 1](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso1.png)


El primer error que aparece es que no encuentra el tipo de dato wordscounter_t ya que nunca incluyo el archivo paso1_wordscounter.h donde ahi 
estaria definido la estructura wordscounter_t y la firma de las distintas funciones.
Los siguientes errores que aparecen, sucede lo mismo que con el primero, al no encontar el include del paso1_wordscounter.h no encuenta donde estan declaradas esas funciones.

 
 
 
