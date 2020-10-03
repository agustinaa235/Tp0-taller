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
 ```
 typedef struct Persona_t{
    int edad;
    char nombre;
    char apellido;
 }Persona_t;
 ```
 por separado la suma del size of de cada elemento que constituye la estructura es es 4 de la edad, 1 del nombre, y 1 del apellido sumando 6 bytes pero cuando se hace sizeof(Persona_t) = 12 bytes
 
 
 
 2.**Paso 1**
 
   2. **Sercom Errores de generacion y normas de programacion**
   
   Al subir el zip del paso 1 al sercom, cuando compila informa lo siguiente:
   
  ![Errores paso 1](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso1.png)


  El primer error que aparece es que no encuentra el tipo de dato wordscounter_t ya que nunca incluyo el archivo paso1_wordscounter.h donde ahi 
  estaria definido la estructura wordscounter_t y la firma de las distintas funciones.
  Los siguientes errores que aparecen, sucede lo mismo que con el primero, al no encontar el include del paso1_wordscounter.h no encuenta donde estan declaradas     esas funciones. En todos los casos se trata de un error de compilacion.

 ![Errores normas de programacion](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso1parte2.png)
 
 * El error de la linea 27 se refiere a que hay que dejar un espacio luego de usar un while ej: while (state != STATE_FINISHED)
 * El error de la linea 41 se refiere a que no hay qe dejar un doble espcail luego de usar el if ej: if (c== EOF)
 * El error de la linea 47 se refiere a a que no si se viene usando un c}ierto criterio con el tema de las llaves seguirlo y no camiarlo. eje:
   ```
   if (a>b) {
        return 0;
    }else if (a<b) {
        return 3;
    }else {
        return 2;
    }
    ```
 * El error de la linea 48 es igual al error de la linea 41
 * El error de la linea 53 se refiere a que una vez que termina una palabra en la terminacion de una linea de codigo al lado de la palbra va el; ej: return 0;
 * El error de la linea se refiere a que no se llega a ver el comentario entero, es mejor que el largo sea menor o igual a 80 caracteres 
 
3.**Paso2**

  3.**Errores de generacion 2**
   
   ![Mejora de normas de programacion](https://github.com/agustinaa235/tp0/blob/master/mejorasDeVerificacionDeNormasPaso2.png)

   podemos Observar que se realizaron los cambios mensionados en el paso 1 con respecto a los errores de normas de porgramacion 
   se cambio:
   * while(state != STATE_FINISHED) por while (state != STATE_FINISHED)
   * if (  c == EOF) por if (c == EOF)
   * return next_state ; por un return next_state; 
   * if(strchr(delim_words, c) != NULL) por if (strchr(delim_words, c) != NULL)
   * reduco la cantidad de palabras delcomentarios de la linea 5 en el paso2_wordscounter.h
      

 ![Errores de compilacion del zip 2](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso2Parte1.png)
 ![Errores de compilacion del zip 2](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso2Parte2.png)
 
  * los primeros errores que aparecen es sobre size_t ya que no lo reconoce, esto sucede por que no importo la bibliotecastdef.h con  #include <stddef.h> en el       paso2_wordscounter.h
  * El eror de la linea 25 cuando no reconce FILE es porque no incluyo la biblioteca de stdio.h con  #include <stdio.h>
  * El error de la linea 30 significa que no incluyo la libreria de stdlib.h con #include<stdlib.h> cuando invoca la funcion malloc
  * El error en la linea 20 del .h y en la 17.c significa que se esta definiendo a una misma funcion con diferentes firmas 
  
 4.**Errores de generacion 3**
  ![Errores de compilacion del zip 2](https://github.com/agustinaa235/tp0/blob/master/ErroresPaso3.png)
  
  Se incluyencion las corresponientes librerias mensionadas en el inciso anterior y se arreglo el error de la linea 20 del .h y 17 del .c
  
  * El error en la linea 27 de main.c lo tira porque esa funcion la encuntra en el .h pero no se encuentra implemnetada en el .c
  
 5.**Memory Leaks y Buffer Overflows** 
  
  Se arreglo el error de la linea 27 del main.c implementando la funcion void wordscounter_destroy(wordscounter_t *self) en el archivo paso4_wordscounter.c
  Se volvio a correr el serum con esta nueva modoficacion y se logro una compilacion exitosa y se corrieron las pruebas. Podemos observar que las prubeas de TDA     de longname por ejemplo fallaron con valgrind
  ![Errores de la prueba TDA](https://github.com/agustinaa235/tp0/blob/master/TdaErrorParte1Paso4.png)
  ![Errores de la prueba TDA](https://github.com/agustinaa235/tp0/blob/master/TdaErrorParte2Paso4.png)
  
  *una de las perdida de memoria es cuando se invoca a la funcion "static char wordscounter_next_state(wordscounter_t *self, char state, char c)"
  donde se hace un malloc donde se reserva un espacio de 7 punteros a char y esa memoria no es liberada.
  * Hay otro error relacionado con el archivo, en donde se hace un fopen pero nunca un fclose.
  
  
  ![Errores de la prueba long-name](https://github.com/agustinaa235/tp0/blob/master/LongFileNameErrorPaso4.png)
  ![Errores de la prueba long-name](https://github.com/agustinaa235/tp0/blob/master/LongFileNameErrorParte2Paso4.png.png)
  
  En esta prueba valgrind tira errores de:
  
  * Hay un archivo abierto y este nunca se cerro
  * Otro error que tira es en el llamado de la funcion memcpy donde se genera un buffer overfloat, que significa que se escirbio informacion en un espacio de         memoria en la cual el programador no tenia acceso. Esto se genero debido a que no hubo un chequeo sobre que tan largo es lo que uno va a copiar en que vas         con respecto al especio de memoria que tiene disponible para realizar la copia. 
    utilizando la funcion  strncpy se solucionaria este problema ya que estas funciones si permiten definir un limite nada mas que es responsabilidad del             programador utiliazar valores coherentes para la definicion de ese limite. Si se hubiera utilizado esta funcion con un limite acorde, no se produciria el         error de buffer overfloat.
    
  Que es Segmentation fault? 
  
  Es cuando cuando en un programa se quiere acceder a memoria en la cual el programador no tiene acceso
  
  Que es Buffer overfloat?
  
  Es cuando se quiere escribir informacion en un buffer/array y se termina escribiendo en lugares de memorias que se encuentran sub siguiente a donde se encuentra   el buffer ya que la informacion que se ingreso no fue  controlada en relacion con el tamanio del buffer por lo que se termina escribiendo en lugares que no       corresponden al buffer. 
  
6.**Codigo de retorno y salida estandar**
    6. Mejoras:
      *se cerro el archivo que se abrio ( se invoco a la funcion fclose() antes de finalizar con el programa
      * Ya no se hace uso de la funcion memcpy en donde esta no verificaba el tamanio del buffer en relacion a la informacion que le llegaba
      *Unya no estamas y se lo reemplazo por cambio que se hizo fue que la memoria que se pedia en la variable delim_words char* const char* delim_words = "              ,.;:\n";
    6. Comando Hxdump 
   ![Ejecucion del comando hxdump](https://github.com/agustinaa235/tp0/blob/master/capturaArchivo.png)
    El ultimo caracter es la d.
    
   6. uso de gdb y makefile
   
   ![compilacion con gdb](https://github.com/agustinaa235/tp0/blob/master/gdb.png)
   ![comando info funciones](https://github.com/agustinaa235/tp0/blob/master/infoFunctions.png)
   ![ambos comando de list](https://github.com/agustinaa235/tp0/blob/master/list.png)
   ![comando de break run y quit](https://github.com/agustinaa235/tp0/blob/master/break-run-quit.png)


   
   Comandos gbd:
    * info funcions imprime por pantalla el nombre de las funciones con su tipo de dato
    *list wordscounter_next_state imprime las lineas centradas al rededor de la funcion wordscounter_next_state
    *list imprime mas lineas
    * break 45 va a colocar un breakPoint en la linea correspondiente. En este cas en la 45
    *run  input_single_word.txt va a correr con lo que se le paso como argumento, en ese caso el txt
    *quit se utiliza este comando para salir de gdb.
    
   6. break 45
    no frena en la linea 45 ya que en la funcion wordscounter_next_state antes si uno hace el seguimiento del codigo nunca entra al if (strchr(delim_words, c) !=     NULL) por lo que nunca entra a la linea 45. Es por este motio que falla la prueba ya que nunca llega a contabilizar la palabra
    
7.**Entrega exitosa **

   7. Mejoras
    * Se mejoro la logica de la funcion wordscounter_next_state generando que se pueda contabilizar la palabra
    * se definieron los limitadores como contantes 
    * cambio el valor del error
    
   7. Prueba con distintos archivos
   
   ![Ejecucion del comando hxdump](https://github.com/agustinaa235/tp0/blob/master/paso6primerArchivo.png)
   ![Ejecucion del comando hxdump](https://github.com/agustinaa235/tp0/blob/master/paso6SegundoArchivo.png)
   ![Ejecucion del comando hxdump](https://github.com/agustinaa235/tp0/blob/master/paso6TercerArchivo.png)

  
   
   



   
   

  
  
  
    
  

  
  
  
 
   
 
 
