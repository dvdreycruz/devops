# Bootcamp Devops Continuo
## Módulo 1 Linux:  Ejercicios CLI

### **Ejercicio 1: Crea mediante comandos de bash la siguiente jerarquía de ficheros y directorios**

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

#### **Solución**
~~~
mkdir -p foo/dummy
mkdir -p foo/empty
echo "Me encanta la bash" > foo/dummy/file1.txt
touch foo/dummy/file2.txt
~~~

---
---
---
### **Ejercicio 2: Mediante comandos de bash, vuelca el contenido de file1.txt a file2.text y mueve file2.txt a la carpeta empty.**
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
#### **Solución**

~~~
cat foo/dummy/file1.txt > foo/dummy/file2.txt
mv foo/dummy/file2.txt foo/empty/file2.txt
~~~
---
---
---

### **Ejercicio 3: Crear un script de bash que agrupe los pasos de los ejercicios anteriores y además permita establecer el texto de file1.txt alimentándose como parámetro al invocarlo.**
Si se le pasa un texto vacío al invocar el script, el texto de los ficheros, el texto por defecto será:
~~~
Que me gusta la bash!!
~~~
---
#### **Solución**
Lo primer es crear el fichero que contendrá el script y otorgarle permisos de escritura
~~~
touch script.sh
chmod +x script.sh
~~~
Una vez creado el fichero _script.sh_ definimos su contenido
~~~
#!/bin/bash
create_initial_structure(){
  local content=$1
  mkdir -p foo/dummy
  mkdir -p foo/empty
  echo $1 > foo/dummy/file1.txt
  touch foo/dummy/file2.txt
  cat foo/dummy/file1.txt > foo/dummy/file2.txt
  mv foo/dummy/file2.txt foo/empty/file2.txt
}

TEXT='Que me gusta la bash!!'
if [[ $# > 0 ]]; then
  TEXT=$1
fi

$(create_initial_structure "${TEXT}")
~~~

Una vez creado lo podemos invocar de la siguiente manera
~~~
. script.sh
~~~
---
---
---
### **Ejercicio 4 Opcional: Crea un script de bash que descargue el contenido de una página web a un fichero**
Una vez descargado el fichero, que busque en el mismo una palabra dada (esta se pasará como parámetro) y muestre por pantalla el número de línea donde aparece
#### **Solución**
##Captura de parametros
~~~
#!/bin/bash

#Captura de parametros
URL="https://www.google.es"
WORD="script"
LINES="";

if [[ $#<1 ]]; then
  echo "Error: Nº de parámetros insuficientes";
  exit 2;
fi

#Almaceno la palabra a buscar
if [[ $#>1 ]]; then
  WORD=$1
fi

#Almaceno la URL
if [[ $#>2 ]]; then
  URL=$2
fi

if [[ $#>2 ]]; then
  echo "Error: Nº de parámetros erróneo";
  exit 2;
fi

#Web a fichero
curl -s $URL > web.html

#Bucle buscando la palabra y mostrando solamente el número de la linea
cat web.html | grep -na $WORD | while read line ; do
   echo  $(echo $line| cut -d: -f1)
done
~~~
