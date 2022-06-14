# Bootcamp Devops Continuo
## Módulo 1 Linux
### Ejercicios CLI

#### **Ejercicio 1: Crea mediante comandos de bash la siguiente jerarquía de ficheros y directorios**

~~~
foo/
├─ dummy/
|  ├─ file1.txt
|  ├─ file2.txt
├─ empty/
~~~

Donde _file1.txt_ debe contener el siguiente texto.
~~~
Me encanta la bash!!
~~~
Y _file2.txt_ debe permancer vacío

---


#### Solución
Aquí vendra la solución al problema


---
---
#### **Ejercicio 2: Mediante comandos de bash, vuelca el contenido de file1.txt a file2.text y mueve file2.txt a la carpeta empty.**
~~~
foo/
├─ dummy/
|  ├─ file1.txt
├─ empty/
|  ├─ file2.txt
~~~
Donde *file1.txt* y *file2.txt* deben contener el siguiente texto
~~~
Me encanta la bash!!
~~~
---
#### Solución
Aquí vendrá la solución del ejercicio2


---
---

#### **Ejercicio 3: Crear un script de bash que agrupe los pasos de los ejercicios anteriores y además permita establecer el texto de file1.txt alimentándose como parámetro al invocarlo.**
Si se le pasa un texto vacío al invocar el script, el texto de los ficheros, el texto por defecto será:
~~~
Que me gusta la bash!!
~~~
---
#### Solución
---
---
#### **Ejercicio 4 Opcional: Crea un script de bash que descargue el contenido de una página web a un fichero**
Una vez descargado el fichero, que busque en el mismo una palabra dada (esta se pasará como parámetro) y muestre por pantalla el número de línea donde aparece