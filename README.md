# GIT
## 1. Definición rápida de GIT:

+ Git es un sistema control de versiones que nos permite guardar multiples veriones de un archivo sin la necesidad de crear multiples carpetas ni duplicar el archivo, por su parte se conserva el mismo archivo a lo largo del desarrollo y git almacena los cambios que se realizan.

+ Además de almacenar los cambios Git permite trabajar con colaboradores, permitiendo trabajar en equipo de forma cómoda, los cambios son guardados junto con el autor del mismo.

+ Cuando los cambios son guardados es posible comparar el archivo con sus versiones anteriores.

## 2. Comandos básicos de Git:

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

# GITFLOW

## 1. ¿Qué es GitFlow?

- Es un workflow para git en donde se establecen normas y formas en las que se debe utilizar git.
- Consiste en un modelo de ramificación y generación de versiones.
- Es descentralizado, ya que su primisa consiste en trabajar en ramas independientes que convergen a una rama de desarrollo la cual lanza versiones finales a la rama master cuando la versión es verificada.

## 2. Tipos de ramas:

1. Principales:  
    - Son ramas que no se instancian, es decir que sólo puede existir una para la producción y otra para el desarrollo.
     
    - No pueden recibir código por medio de commits.

    - Su nombre se relaciona directamente con el tipo, suelen ser master y develop.

    - El código es incorporado a través de otra rama.

2. Auxiliares:

    - Se pueden instanciar todas las veces que se requiera.

    - Las instancias tienen el objetivo de realizar  trabajos independientes para una vez terminados sean incorporadoal desarrolo.

    - su nombre está compuesto por el tipo y por su objetivo, funcionalidad, versión, etc.

        - Feature son aquellas en las que se trabajará directamente.

        - Realse se usa para lanzar una versión compacta a master.

        - Hotfix se usa para resolver un error puntual en producción
    - Estas ramas tienen un principio y un fin, en cuanto se hace merge con la rama principal desaparecen.

    ```mermaid
    gitGraph:
    options
    {
        "nodeSpacing": 150,
        "nodeRadius": 10
    }
    end
    commit
    checkout master
    branch develop
    checkout develop
    commit
    branch feature
    checkout feature
    commit
    commit
    checkout master
    commit
    checkout develop
    commit
    merge feature
    branch realse
    checkout realse
    commit
    commit
    checkout master
    merge realse
    commit
    checkout develop
    commit
    merge realse
    
    ```
        
## 3. Primeros pasos con GitFlow:  

GitFlow contiene un conjunto de herramientas que nos permiten realizar nuestros propósitos con las ramas, basta con tener instalado Git en nuestro sistemas operativo para iniciar.  

1. Usar GitFlow en un proyecto:  
    - para iniciar un proyecto utilizando GitFlow es necesario sustituir el comando `git init` por el comando `git flow init`, de esta forma dispondremos de las herramientas de GitFlow.
2. Creando las principales ramas:
    - Cuando usamos GitFlow en nuestro proyecto nos crea aútmoaticamente las ramas master y develop, también, nos pregunta cómo queremos que se nombren por defecto las ramas secundarias.
3. Creando las ramas auxiliares:  
    
    1. Ramas de funciones (feature):  

        - Para crear una rama feature desde la terminal nos situamos en la rama develop ya que utilizan la rama develop como la principal.

        - Una vez estemos en la rama develop ejecutamos el siguiente comando `git flow feature start (nombre de la rama feature)`.

        - De esta forma ya se ha creado la rama feature, ahora se puede realizar la funcionalidad por la que fue creada y utilizar git para hacerle commits o publicarla al repositorio central para que un compañero pueda realizar cambios sobre la misma.

        Grafica de las ramas cuando se crea una rama feature y se trabaja sobre ella:  

        ```mermaid
        gitGraph:
        options
        {
            "nodeSpacing": 150,
            "nodeRadius": 10
        }
        end
        commit
        branch develop
        checkout develop
        commit
        branch feature
        checkout feature
        commit
        commit
        ```

        - Cuando se termina la funcionalidad se procede a fusionar los cambios con la rama develop, para ello en lugar de utilizar el comando `merge` utilizamos `git flow feature finish (nombre de la rama feature)` en el fondo lo que hace este comando es posicionarnos en develop, hacer merge de la rama feature y posteriormente elimina la rama feature ya que cumplió su ciclo de vida.

        Grafica de las ramas cuando se fusiona una rama feature con la rama develop:  

        ```mermaid
        gitGraph:
        options
        {
            "nodeSpacing": 150,
            "nodeRadius": 10
        }
        end
        commit
        branch develop
        checkout develop
        commit
        branch feature
        checkout feature
        commit
        commit
        checkout develop
        commit
        merge feature
        ```





    2. Ramas de lanzamiento (realse):  

        - Para crear una rama realse desde la terminal nos situamos en la rama develop ya que utilizan la rama develop como la principal.

        - Una vez estemos en la rama develop ejecutamos el siguiente comando `git flow realse start (versión que se espera lanzar)`.

        - De esta forma ya se ha creado la rama realse, ahora se procede a revisar, pulir y probar las funcionalidades de la verisón, se pueden realizar commits y comunmente se añade la documentación pertinente.

        - De igual forma que con las ramas feature, las ramas realse se crean a partir de la develop por lo que la gráfica sería la misma mientras se trabaja con la rama realse que con las feature.

        - Llegado el momento o la fecha de lanzar la verisón a producción se fusiona la rama realse con master y con develop, de esta forma master dispondrá de la versión y develop también, develop requiere tener dicha versión para poder continuar el desarrollo pero de la siguiente versión.

        - Para realizar la fusión de realse con master y develop ejecutamos `git flow release finish (número de la versión)` y posteriormente agregamos un comentario que describa a la versión.

        Grafica de las ramas cuando se lanza una nueva versión:

        ```mermaid
        gitGraph:
        options
        {
            "nodeSpacing": 150,
            "nodeRadius": 10
        }
        end
        commit
        branch develop
        checkout develop
        commit
        branch realse
        checkout realse
        commit
        commit
        checkout develop
        commit
        merge realse
        checkout master
        commit
        checkout master
        merge develop

        
        ```
