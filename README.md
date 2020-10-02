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
   
   Descomprimiendo el codigo 'source_unsafe.zip'...
Archive:  source_unsafe.zip
  inflating: source_unsafe/paso1_main.c
  inflating: source_unsafe/paso1_wordscounter.c
  inflating: source_unsafe/paso1_wordscounter.h
Compilando el codigo...
  CC  paso1_main.o
paso1_main.c: In function ‘main’:
paso1_main.c:22:9: error: unknown type name ‘wordscounter_t’
   22 |         wordscounter_t counter;
      |         ^~~~~~~~~~~~~~
paso1_main.c:23:9: error: implicit declaration of function ‘wordscounter_create’ [-Wimplicit-function-declaration]
   23 |         wordscounter_create(&counter);
      |         ^~~~~~~~~~~~~~~~~~~
paso1_main.c:24:9: error: implicit declaration of function ‘wordscounter_process’ [-Wimplicit-function-declaration]
   24 |         wordscounter_process(&counter, input);
      |         ^~~~~~~~~~~~~~~~~~~~
paso1_main.c:25:24: error: implicit declaration of function ‘wordscounter_get_words’ [-Wimplicit-function-declaration]
   25 |         size_t words = wordscounter_get_words(&counter);
      |                        ^~~~~~~~~~~~~~~~~~~~~~
paso1_main.c:27:9: error: implicit declaration of function ‘wordscounter_destroy’ [-Wimplicit-function-declaration]
   27 |         wordscounter_destroy(&counter);
      |         ^~~~~~~~~~~~~~~~~~~~
make: *** [<builtin>: paso1_main.o] Error 1

real    0m0.200s
user    0m0.023s
sys     0m0.025s
[Error] Fallo la compilacion del codigo en 'source_unsafe.zip'. Codigo de error 2

El primer error que aparece es que no encuentra el tipo de dato wordscounter_t ya que nunca incluyo el archivo paso1_wordscounter.h donde ahi 
estaria definido la estructura wordscounter_t y la firma de las distintas funciones.
Los siguientes errores que aparecen, sucede lo mismo que con el primero, al no encontar el include del paso1_wordscounter.h no encuenta donde estan declaradas esas funciones.

 
 
 
