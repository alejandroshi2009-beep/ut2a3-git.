
# UT2.A4 - Git y GitHub: Recuperación de una configuración dañada

**Nombre y apellidos:** Alejandro de Leon Comes

## 1. Problema detectado

El problema detectado en el servidor web fue que el cortafuegos estaba desactivado.

La configuración contenía firewall=no, cuando debería estar configurada como firewall=si.

Esto suponía un problema de seguridad para el servidor.

## 2. Investigación del historial

Para investigar el problema utilicé los siguientes comandos:

**Consultar el historial de commits:**

git log --oneline

Este comando permite consultar todos los cambios registrados en el repositorio.

**Comprobar los cambios de un commit:**

git show [ID DEL COMMIT INCORRECTO]

Con este comando comprobé que se había cambiado firewall=si por firewall=no.

**Comparar dos versiones:**

git diff [ID DEL COMMIT ANTERIOR] [ID DEL COMMIT INCORRECTO] -- servidor.conf

Este comando permitió identificar exactamente qué línea se había modificado.

## 3. Identificación del error

El primer commit que introdujo el error fue:

Actualizacion de seguridad

**Identificador del commit:** [ESCRIBE AQUÍ EL IDENTIFICADOR REAL]

El error consistió en desactivar el cortafuegos mediante el cambio de firewall=si a firewall=no.

## 4. Recuperación de una versión anterior

Para recuperar la versión anterior al error utilicé:

git checkout [ID DEL COMMIT ANTERIOR] -- servidor.conf

Recuperé la versión correspondiente al commit Cambio de puerto.

Esta versión mantenía el puerto 8080 y tenía el cortafuegos activado.

Las modificaciones posteriores no desaparecieron del historial, pero temporalmente no aparecían en el archivo recuperado.

**Respuestas:**

- ¿Qué versión del archivo has recuperado?

La versión del commit Cambio de puerto.

- ¿Se han perdido temporalmente las modificaciones posteriores?

Sí, las modificaciones posteriores no aparecían temporalmente en el archivo recuperado.

- ¿Han desaparecido los commits posteriores del historial?

No, todos los commits siguen guardados en el historial de Git.

- ¿Por qué no conviene utilizar directamente esta versión antigua como solución definitiva?

Porque perderíamos los cambios válidos realizados posteriormente, como la página principal inicio.html y el límite de 100 conexiones.

## 5. Cambios que debían conservarse

La empresa necesitaba mantener las siguientes modificaciones:

- Puerto del servidor: 8080.
- Página principal: inicio.html.
- Límite de conexiones: 100.
- Cortafuegos: activado (firewall=si).

## 6. Solución definitiva

Para solucionar el problema sin perder los cambios válidos, primero recuperé la versión más reciente mediante:

git restore --source=HEAD --staged --worktree servidor.conf

Después modifiqué únicamente la configuración del cortafuegos:

firewall=si

Finalmente guardé la corrección utilizando los siguientes comandos:

git add servidor.conf

git commit -m "Correccion de configuracion de seguridad"

De esta manera se solucionó el problema sin perder las modificaciones anteriores.

## 7. Utilidad de Git

Git es una herramienta que permite controlar las versiones de los archivos y registrar todos los cambios realizados.

Gracias a Git podemos consultar el historial, comparar versiones, recuperar archivos anteriores y solucionar errores sin perder los cambios correctos.

Es una herramienta muy útil para los técnicos informáticos porque permite administrar archivos de configuración de servidores de forma segura y organizada.

## 8. Conclusión

He conseguido identificar el cambio que desactivó el cortafuegos, recuperar una versión anterior del archivo y solucionar el problema conservando las modificaciones válidas.

Finalmente, he registrado la investigación y la configuración corregida en el repositorio Git.
