# GIT Y GITLENS
## 1. Definición rápida de GIT:

+ Git es un sistema control de versiones que nos permite guardar multiples veriones de un archivo sin la necesidad de crear multiples carpetas ni duplicar el archivo, por su parte se conserva el mismo archivo a lo largo del desarrollo y git almacena los cambios que se realizan.

+ Además de almacenar los cambios Git permite trabajar con colaboradores, permitiendo trabajar en equipo de forma cómoda, los cambios son guardados junto con el autor del mismo.

+ Cuando los cambios son guardados es posible comparar el archivo con sus versiones anteriores.

## 2. Comandos básicos de Git

- **git init**  

     Sirve para inicializar un repositorio en la ruta.
    se crea un espacio en memria RAM llamado staged en donde se guardarán los archivos temporalmente

- **git add (nombre del archivo)**  

    Sirve para que el sistema control de versiones sepa que el archivo existe
    envía el archivo a la seccion staged en espera de que sea subido al repositorio.

- **git add .**  

    Sirve para añadir todos los archivos que tuvieron un cambio.

- **git remove (nombre del archivo)**  

    remueve el archivo de la sección staged.

- **git commit -m "(mensaje)"**  

    Commit envía los últimos cambios del archivo a la base de datos del control de versiones.
    -m es para incluir un mesnaje que describa los cambios realizados.
    el comit es envíado al repositorio que por defecto se llama master.

- **git checkout -- (nombre del archivo)**  

    Revierte los cambios realizados que no fueron guardados com commit.

- **git diff (nombre del archivo)**  

    Muestra las diferencias que tiene el archivo sin commit.

- **git branch**  

    Muestra las ramas que disponemos.

- **git branch (nombre de la rama)**  

    Agrega una nueva rama.

- **git checkout (nombre de la rama)**  

    Cambia a la rama seleccionada.

- **git remote (url)**  

    indicamos el repositorio al que se guardará el control de versiones.

- **git push**  

    "empuja" o envía los cambios al repositorio elegido con git remote.

- **git push --all**  

    actualiza todos los cambios de todas las ramas.

- **git push -u origin (rama)**  

    Envia los archivos con su respectivo commit
    requiere login

- **git clone (url)**  

    clona el repositorio en el equipo.

- **git fetch**   

    va a buscar las actualizaciones del repositorio.

- **git pull**  

    "Hala" o trae los archivos nuevos en el repositorio.


