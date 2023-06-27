# Uso de gdb para depurar un programa con listas enlazadas #

Este repositorio contiene un programa que lee datos de temperatura de un archivo tabulado. El programa almacena los datos leídos en una lista enlazada. Al ejecutar, el programa produce una falla de segmentación. Utilice *GDB* para depurar y corregir los errores.

## Uso
El programa tiene el siguiente uso:

```
$ ./lector -h
Lee un archivo tabulado con datos de temperatura.
Uso:
./lector [-c] archivo
./lector -h
Opciones:
 -h	Ayuda, muestra este mensaje
 -c	Archivo contiene línea cabecera
```

El programa usa argumentos para determinar el nombre del archivo a leer. Para leer un archivo tabulado con nombre *datos.txt*:

```
./lector datos.txt
```

Si la primera línea del archivo de datos contiene una cabecera, le podemos pedir al programa que la ignore usando la opción -c:

```
./lector -c datos.txt
```

## Corrección
Utilice *GDB* para encontrar y reparar los siguientes errores:
1. Falla de segmentación al leer un archivo válido.
2. Falla de segementación al leer un archivo inválido (por ejemplo, leer un archivo con cabecera sin usar -c)

La salida esperada usando el archivo de prueba *datos_con_cabecera.txt* :

```
$ ./lector -c datos_con_cabecera.txt 
Abriendo el archivo datos_con_cabecera.txt y asumiendo que tiene cabecera.
12	25	20	24.11
12	25	19	25.34
12	25	18	26.50
12	25	17	27.00
12	25	16	27.10
12	25	15	26.99
12	25	14	24.68
12	25	13	24.57
```
La salida esperada al leer un archivo con datos inválidos (ejemplo al leer *datos_con_cabecera.txt* sin usar -c, la primera línea es inválida):

```
$ ./lector datos_con_cabecera.txt 
Abriendo el archivo datos_con_cabecera.txt.
Error al leer datos_con_cabecera.txt
```
**IMPORTANTE:** El mensaje *Error al leer datos_con_cabecera.txt* debe estar en *STDERR*.

### Uso de GDB
En la imagen de abajo se muestra una captura de pantalla en donde se usa el comando *print* en la consola de *GDB* para mostrar el contenido de un nodo de la lista enlazada. Es necesario demostrar el uso de GDB para explorar el funcionamiento del programa y detectar los posibles bugs, para esto se debe adjuntar en la tabla de abajo una imagen en donde se aprecia el contenido de un **nodo cabecera** usando *print* dentro de *GDB*.

Ejemplo uso de GDB | Demostrar uso de GDB
--- | ---
![Usar print para ver el contenido de una estructura](/imagenes/pantalla_gdb1.png) | Insertar aquí imagen demostrando uso de GDB.

## Entregable
Completar está practica reparando los errores y modificando el README.md con mínimo un commit.
