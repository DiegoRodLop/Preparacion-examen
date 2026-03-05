**Examen DWEC Segunda Evaluación (Simulacro)**

Contexto del examen

Vas a desarrollar una aplicación en VueJS que gestione una lista de "Favoritos" de usuarios de GitHub. La aplicación debe permitir buscar un usuario, mostrar sus datos y guardarlo en una lista local.

**Preparación (Git**)

*Clona el repositorio proporcionado (o crea uno nuevo).

*Crea una rama llamada desarrollo-examen.

Al finalizar, deberás hacer un merge a la rama main y subir los cambios.

**Tareas a realizar**
**1. Lógica de Datos: js/githubService.js (Módulos ES6)**

Crea un archivo de lógica pura que será importado por Vue. Debe contener:

Función formatearFecha(timestamp): Recibe un timestamp y devuelve la fecha en formato localizado dd/mm/aaaa.

Función asíncrona obtenerDatosGithub(username):

Debe usar fetch para llamar a https://api.github.com/users/{username}.

Si la respuesta es ok, devuelve el JSON.

Si no (error 404), debe lanzar un error o devolver null.

**2. Componente de Visualización: components/UserCard.vue**

Este componente servirá para mostrar cada usuario en la lista de favoritos.

Props: Recibe un objeto usuario.

Template: Debe mostrar:

La imagen del avatar (avatar_url).

El nombre de usuario (login).

Un enlace a su perfil (html_url) que se abra en pestaña nueva.

La fecha en la que se añadió a favoritos (formateada usando la función del punto 1).

Evento: Un botón "Eliminar" que envíe un emit al padre con el id del usuario.

**3. Aplicación Principal: App.vue**

Es el núcleo de la aplicación. Debe implementar:

Estado (Reactividad):

busqueda: String vinculado al input.

favoritos: Array que almacena los usuarios guardados.

error: Mensaje para mostrar si el usuario no existe.

cargando: Booleano para mostrar un mensaje de "Buscando..." mientras el fetch está en curso.

Método buscarYAñadir:

Se activa al pulsar ENTER en el input o click en "Añadir".

Llama a la lógica de githubService.js.

Añade al usuario al array favoritos incluyendo un campo fechaAñadido con el timestamp actual (Date.now()).

Importante: No se pueden añadir usuarios duplicados (comprobar por id).

Template:

Un formulario con @submit.prevent.

Un v-for que recorra favoritos y renderice el componente UserCard.

Uso de v-if / v-else para gestionar el estado de carga y los errores.

**💡 Claves para aprobar (basado en tu examen anterior)**
Async/Await: Asegúrate de usar try...catch en la función que hace el fetch. El profesor valorará que controles qué pasa si falla el internet o si el usuario no existe.

No manipules el DOM: A diferencia del primer examen donde usabas document.getElementById, aquí todo debe hacerse mediante reactividad (ref o reactive) y directivas (v-model, v-bind).

Git: No olvides hacer commits frecuentes con mensajes claros (ej: feat: add fetch logic, fix: component styling). Es probable que miren el historial de commits.

Uso de Props y Emits: Es fundamental para demostrar que entiendes cómo se comunican los componentes en Vue.
