2024-06-23 17:57

Status:

Tags: [[programming]] [[android]] [[facultad]]
# Apuntes Android Teoria

- Toda aplicación debe tener el archivo AndroidManifest.xml. 
Proporciona al S.O. información esencial de la aplicación, para que esta pueda ser ejecutada.

- xml es un lenguaje de marcas con el que se pueden describir estructuras de datos

-  `android:gravity` define la gravedad de los contenidos de la view sobre la que se usa.
- `android:layout_gravity` define la gravedad de la view relativo a su padre.


Para recibir un resultado desde la activity que se va a iniciar se debe lanzar dicha activity utilizando un objeto de la clase “ActivityResultLauncher”.

Este objeto permite lanzar la actividad y definir o registrar un escuchador de evento, que será llamado, por el sistema operativo, cuando la actividad lanzada finalice. Este objeto puede definirse como un atributo de la clase.

Intent implícitos que NO especifican el componente que se desea iniciar sino que sólo describen una acción a realizar y opcionalmente los datos sobre los que trabajar

Ejemplos, action view, action dial, action send
type: text/plain

# ==Ciclo de vida de una activity==

-Una aplicación generalmente consiste en múltiples activities vinculadas entre sí, corriendo en un único proceso del S.O.
Normalmente, hay una activity principal que se presenta al usuario cuando éste inicia la aplicación por primera vez
Cada vez que se inicia una activity nueva, se detiene la anterior, se la incluye en la pila de activities y obtiene el foco.
Cuando el usuario presiona el botón atrás, se quita de la pila, se destruye, y se reanuda la activity anterior

-Una activity puede pasar por distintos estados: ==created, paused, stopped, resumed o destroyed.==
Por cada transición de estado se ejecutarán una serie de métodos callbacks

onSaveInstanceState () se invoca cuando una activity que pierde el foco y espera ser reanudada (el usuario no la cerró explícitamente) está en riesgo de ser destruida.
onRestoreInstanceState() se utiliza para recuperar los datos almacenados en onSaveInstanceState(). Muchas veces no se usa porque la recuperación también se puede hacer en el onCreate().
# ==Layouts==

- El Layout de una activity representa el diseño de la interfaz de usuario determinando la disposición de distintos componentes visuales (views) en la misma
- Los layouts también son vistas pero pertenecen a una categoría específica de vistas (ViewGroup)
- Los elementos visuales simples, como los editText, TextView, Button, son clases particulares de vistas que deben ser dispuestos dentro de un contenedor
- El contenedor es un ViewGroup


# ==Recursos==


# Reference

