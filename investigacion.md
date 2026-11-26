
# UT2.A4 - Git y GitHub: Recuperación de una configuración dañada

**Nombre y apellidos:** [TU NOMBRE Y APELLIDOS]

## 1. Problema detectado

El servidor web tenía un problema de seguridad porque el cortafuegos estaba desactivado.

La configuración contenía firewall=no, cuando debería estar configurada como firewall=si.

## 2. Investigación del historial

Para consultar el historial utilicé:

git log --oneline

El commit que introdujo el error fue:

Actualizacion de seguridad

Para comprobar los cambios realizados utilicé:

git show [ID DEL COMMIT INCORRECTO]

El resultado mostró que se había cambiado firewall=si por firewall=no.

También utilicé:

git diff [ID DEL COMMIT]^ [ID DEL COMMIT] -- servidor.conf

Con este comando pude comprobar las diferencias entre las dos versiones.

## 3. Identificación del error

El primer commit que introdujo el error fue Actualizacion de seguridad.

Su identificador fue: [ID DEL COMMIT INCORRECTO]

## 4. Recuperación de una versión anterior

Utilicé el comando:

git checkout [ID DEL COMMIT ANTERIOR] -- servidor.conf

Recuperé la versión correspondiente al commit Cambio de puerto.

Esta versión tenía el puerto 8080 y el cortafuegos activado.

Las modificaciones posteriores no desaparecieron del historial, pero no estaban presentes temporalmente en el archivo recuperado.

## 5. Cambios que debían conservarse

La empresa necesitaba mantener los siguientes cambios:

- Puerto 8080.
- Página principal inicio.html.
- Límite de 100 conexiones.
- Cortafuegos activado.

## 6. Solución definitiva

Primero recuperé la última versión del archivo mediante:

git restore --source=HEAD --staged --worktree servidor.conf

Después modifiqué únicamente la línea del cortafuegos:

firewall=si

Finalmente registré la solución:

git add servidor.conf

git commit -m "Correccion de configuracion de seguridad"

## 7. Utilidad de Git

Git es una herramienta que permite controlar las versiones de los archivos.

Gracias a Git podemos consultar los cambios realizados, identificar errores, recuperar versiones anteriores y solucionar problemas sin perder el historial de modificaciones.

Es especialmente útil para administrar servidores y archivos de configuración porque permite mantener un registro de los cambios realizados por diferentes técnicos.
