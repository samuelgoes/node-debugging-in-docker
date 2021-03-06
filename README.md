# Node debugging in docker
#### Ejercicio para aprender a hacer debugging de aplicaciones node-js dentro de contenedores docker
#### Created by: Danielo Rodríguez Rivero
#### Keywords: rest,microservice, tutorial


Hello fellow reader. This repository is a tutorial about how to debug node-js applications inside docker containers.
The readme and instructions are on Spanish, however all the code, comments and basic operating may be on english.
I made this an spanish manual because there are very few tutorials on my native language about this topic.
In any case, if you really want an english version, don't hesitate to open an issue. If it gets enough interest I may consider creating an international english version.

## Get things running

First a small set of instructions in English for any international reader that may want to take a look.

* Start the server `npm start`
* Start the server on dev mode `npm run start-dev` 
* Run tests `npm test`
* With the server running, open `http://localhost:3000/version` to see the version of your package
* With the server running, open `http://localhost:3000/documentation` to see the documentation of your API

## Required tools

* **VSCode** our editor of choice. We even include the special `.vscode` folder so you can follow the tutorial completely, including the debugging configurations.
* **Docker** should be installed an accesible on the user path.
* **git**: git should be installed. We also assume that you have some familiarity with such tool.

## Uso de este tutorial

Este tutorial/manual es interactivo y está pensado para ser completado de la mano de un tutor, que en muchos de los casos será el autor del mismo. 
No obstante, hay un pequeño conjunto de reglas y directrices que pueden ayudar a utilizarlo:

* Cada rama representa un estadio diferente del tutorial, con distintas aprochimaciones a la solución en cada una de ellas.
Todas cuentan con parte de la solución pero tienen algún defecto o problema que se debe solucionar.
  * **master**: Contiene el código básico y las instrucciones. No tiene la posibilidad de debugging dentro del contenedor. Se puede hacer debugging en local y generar una imagen de docker
  * **01-basic-way**: La primera aproximación (ñapa) a la solución. Se trata de la forma más básica y menos aconsejable
  * **02-bug-on-startup**: En esta rama se introduce un problema que nos dificulta la tarea: El contenedor arrancará pero debido a un bug parará antes de que podamos acceder a la interfaz de debugging
  * **03-configurable-debugging**: En esta rama se introduce el uso de una pequeña ayuda para habilitar de forma dinámica el debugging dentro del contenedor, sin tener que reconstruir la imagen.
  * **04-already-running-container**: Pequeño truco que nos permite activar el protocolo de debug en cualquier contenedor que esté corriendo sin tener que reconstruir la imagen

### Lecciones

En cada rama el enunciado del ejercicio, así como cualquier ayuda para completarlo, estará en el README en una sección titulada **Lección-xx** donde `xx` debe coincidir con el prefijo de la rama.
Puede que los cambios significativos se detallen en la sección de la lección, pero puede que existan diferencias no detalladas. 
En caso de que quieras ver de forma detallada que ha cambiado con respecto a la lección anterior , **git** es tu amigo y el uso de `git diff` está recomendado. Esto es un tutorial para gente espabilada oiga.

### Cómo completar las lecciones

Este manual o conjunto de ejercicios pretende ser completado en el ordenador del participante.
Por lo tanto, para un correcto seguimiento del mismo se debe clonar el repositorio en su máquina, instalar las dependencias requeridas y cambiar de una rama a otra para navegar por las distintas lecciones.
Para facilitar esta tarea hay a continuación un listado de comandos a ejecutar de forma secuencial y una pequeña referencia de algunos comandos útiles.

Los primeros pasos para poder empezar deberían ser:

1. `git clone git@github.com:danielo515/node-debugging-in-docker.git` 
1. `npm install` o si prefieres simplemente ejecuta `yarn` en caso de que lo tengas instalado
1. `npm start` para comprobar que todo funciona correctamente

Algunos comandos de referencia:

* `npm run build` en cualquiera de las ramas construye la imagen de docker
* `npm run docker-start` ejecuta el contenedor en modo interactivo (para poder ver los logs). Asegúrate de **construir la imagen primero!**
* `git checkout master` para volver a las instrucciones básicas 
* `git checkout 01-basic-way` para ir a la primera lección
* `git checkout 02-bug-on-startup` para ir a la segunda lección

The example microservice that is used for exploring the different scenarios was generated by the [Hapi Swagger ES6 Generator](https://github.com/danielo515/generator-hapi-swagger-es6)
