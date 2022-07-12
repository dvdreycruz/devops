# Bootcamp Devops Continuo
## Módulo 1 CI/CD

## Ejercicios Jenkins ##

### **1. CI/CD de una Java + Gradle**

En el directorio raíz de este código fuente, crea un Jenkinsfile que contenga un pipeline declarativa con los siguientes stages:

- **Checkout** descarga de código desde un repositorio remoto, preferentemente utiliza GitHub.
- **Compile** compilar el código fuente, para ello utilizar gradlew compileJava
- **Unit Tests** ejecutar los test unitarios, para ello utilizar gradlew test

Para ejecutar Jenkins en local y tener las dependencias necesarias disponibles podemos contruir una imagen a partir de [este Dockerfile](https://campus.lemoncode.net/jenkins-resources/gradle.Dockerfile)

### **2. Modificar la pipeline para que utilice la imagen Docker de Gradle como build runners**

## Ejercicios GitLab ##
### **1. CI/CD de una aplicación spring**
- Crea un nuevo proyecto en GitLab y un repositorio en el mismo, para la aplicación springapp. El código fuente de la misma lo puedes encontrar en este [enlace](https://campus.lemoncode.net/02-gitlab/springapp).

- Sube el código al repositorio recientemente creado en GitLab.

- Crea una pipeline con los siguientes stages:

- maven:build - En este stage el código de la aplicación se compila con [maven](https://maven.apache.org/).

- maven:test - En este stage ejecutamos los tests utilizando [maven](https://maven.apache.org/).

- docker:build - En este stage generamos una nueva imagen de Docker a partir del Dockerfile suministrado en el raíz del proyecto.

- deploy - En este stage utilizamos la imagen anteriormente creada, y la hacemos correr en nuestro local

Pistas:

- Utiliza la versión de maven 3.6.3
- El comando para realizar una build con maven: *mvn clean package*
- El comando para realizar los tests con maven: *mvn verify*
- Cuando despleguemos la aplicación en local, podemos comprobar su ejecución en: http://localhost:8080

### **2. Crear un usuario nuevo y probar que no puede acceder al proyecto anteriormente creado**
- Añadirlo con el role *guest*, comprobar que acciones puede hacer.

- Cambiar a role *reporter*, comprobar que acciones puede hacer.

- Cambiar a role *developer*, comprobar que acciones puede hacer.

- Cambiar a role *maintainer*, comprobar que acciones puede hacer.

Nota (acciones a probar):

- Commit
- Ejecutar pipeline manualmente
- Push and pull del repo
- Merge request
- Acceder a la administración del repo

### **3. Crear un nuevo repositorio, que contenga una pipeline, que clone otro proyecto, springapp anteriormente creado. Realizarlo de las siguientes maneras:**
- Con el método de CI job permissions model
    - ¿Qué ocurre si el repo que estoy clonando no estoy cómo miembro?

Pista: https://docs.gitlab.com/ee/user/project/new_ci_build_permissions_model.html (Dependent Repositories)

- Con el método deploy keys
    - Crear deploy key en el repo springapp y poner solo lectura
    - Crear pipeline que usando la deploy key

Pista: https://docs.gitlab.com/ee/ci/ssh_keys/
