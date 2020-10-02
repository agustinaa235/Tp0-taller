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
 
 Opciones mas comunes:
 
   * valgrind --track-origins=yes ( detecta cuando encuentra variables sin inicializar)
   * valgrind --leak-check=yes ( activa un detector para en detalle de perdida de memoria)
 
 La funcion sizeof() nos devuelve la cantidad de bytes que ocupa el tipo de dato que le estemos pasando.
 El tamanio depende de la arquitectura y del compilador.
 En el caso de ser in int, sizeof(int) devuelve 4 bytes mientras que en el caso de pasarle el tipo de dato char 
 nos devuelve 1 byte.
 ¿El sizeof() de una struct de C es igual a la suma del sizeof() de cada uno sus elementos?
 Esto no es correcto
 Ejemplo:
 
 typedef struct Persona_t{
    int edad;
    char nombre;
    char apellido;
 }Persona_t;
 
 por separado la suma del size of de cada elemento que constituye la estructura es es 4 de la edad, 1 del nombre, y 1 del apellido sumando 6 bytes pero cuando se hace sizeof(Persona_t) = 12 bytes
 
 
 
 2.**Paso 1**
 
   2. **Sercom Errores de generacion y normas de programacion**
   
   Al subir el zip del paso 1 al sercom, cuando compila informa lo siguiente:
   
  ![Errores paso 1](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso1.png)


El primer error que aparece es que no encuentra el tipo de dato wordscounter_t ya que nunca incluyo el archivo paso1_wordscounter.h donde ahi 
estaria definido la estructura wordscounter_t y la firma de las distintas funciones.
Los siguientes errores que aparecen, sucede lo mismo que con el primero, al no encontar el include del paso1_wordscounter.h no encuenta donde estan declaradas esas funciones. En todos los casos se trata de un error de compilacion.

 ![Errores normas de programacion](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso1parte2.png)
 
 * El error de la linea 27 se refiere a que hay que dejar un espacio luego de usar un while ej: while (state != STATE_FINISHED)
 * El error de la linea 41 se refiere a que no hay qe dejar un doble espcail luego de usar el if ej: if( c== EOF)
 * El error de la linea 47 se refiere a a que no si se viene usando un sierto criterio con el tema de las llaves seguirlo y no camiarlo. eje:
   ``` if ( a>b){
        return 0;
    }else if ( a<b){
        return 3;
    }else {
        return 2;
    }´´´
 * El error de la linea 48 es igual al error de la linea 41
 * El error de la linea 53 se refiere a que una vez que termina una palabra en la terminacion de una linea de codigo al lado de la palbra va el; ej: return 0;
 * El error de la linea se refiere a que no se llega a ver el comentario entero, es mejor que el largo sea menor o igual a 80 caracteres 
 
3.**Paso2 **

  3.**Errores de generacion 2**
    ![Errores de compilacion del zip 2](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso2Parte1.png)
    ![Errores de compilacion del zip 2](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso2Parte2.png)

    
    


 
   
 
   
 
 
