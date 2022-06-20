# Scripting
Los scripts en linux no necesitan formato. 
Simplemente hay que lanzar el script con el comando bash

## bash <nombre_fichero>
Para lanzar el script sin necesidad de utilizar el comando bash tenemos las siguientes alternativas
1. Con el comando source
~~~
source <nombre_fichero>
~~~
2. Sin comando
~~~
. <nombre_fichero>
~~~

## Permisos
Para asignarles permisos de escritura y convertilo en un script ejecutable hay que utilizar el comando chmod

~~~
chmod +<permisos> nombre_fichero
~~~

Al convertirlo en ejecutable en el script deberiamos indicar que tipo de interprete se utilizará al lanzarlo. En la primera línea hay que poner el siguiente formato:
~~~
#!<path_to_interprete>
#!/bin/bash
#!/usr/bin/python3
~~~

## Variables
### env 
Muestra las variables definidos actualmente en el entorno

### printenv <nombre_variable>
Muestra el contenido de una variable

## Entrada/Salidas
Los script tiene una única entrada de parámetros y varios tipos de salidas:
1. Salida estándar
2. Salida de errores 

En los script se pueden definir entradas o salidas.
### Operador '>' y '>>' y '&>'
*'\>'* Redirige la salida estandar a otro destino ***sobreescribiendo*** el contenido del archivo destino
~~~ 
<namescript> > <name_destination_file>  
~~~
  
*'\>>'* Redirige la salida estandar a otro destino ***añadiendo*** el contenido del archivo destino
~~~ 
<namescript> >> <name_destination_file>  
~~~
Se puede elegir el tipo de salida que se desea redirigir indicando el número delante de >
~~~
<namescript> #> <name_file
~~~
*'&>'* Redirige todas las salidas a otro destino ***añadiendo*** el contenido del archivo destino
~~~ 
<namescript> &> <name_destination_file>  
~~~

#### **Descartar la salida**
Si deseamos descargar la salida de un comando podemos redigir la salida a una especie de papelera
~~~
<name_fichero> > /dev/null
~~~

### Operador '<' 
Acepta tanto desde consola como de ficheros