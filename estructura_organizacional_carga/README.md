# API de Carga Masiva de Estructura Organizacional

Este documento describe la API del microservicio que carga la estructura organizacional (las posiciones y
quién ocupa cada una) de forma masiva, a partir de un archivo `.xlsx`, con validación fila a fila y una vista
previa de los cambios antes de aplicar nada.

## Descripción General

Es una **carga total**: la plantilla se descarga con todos los colaboradores activos y el archivo representa la
estructura completa. La API permite a los clientes:

*   Descargar la plantilla oficial `.xlsx` (versión 3): hoja **Instrucciones** y hoja **Usuarios**, prellenada
    con todos los colaboradores activos, con su código de cargo externo e interno y el código del cargo padre.
*   Crear una carga y subir el archivo (directo a S3 con una URL prefirmada).
*   Validar el archivo de forma asíncrona y hacer *polling* del progreso.
*   Revisar el resultado fila a fila (aceptadas/rechazadas, motivos por regla) y la **vista previa de cambios**
    (qué se crea, actualiza, elimina o desocupa) antes de aplicar.
*   Confirmar la carga: crea, actualiza, elimina (de forma lógica) o desocupa posiciones. Quien no viene en el
    archivo sale de la estructura. Nunca modifica los usuarios.
*   Consultar el historial de cargas del tenant, la auditoría de cada carga y descargar el log de resultados.

Solo pueden usar esta API personas marcadas como administradoras del sistema, y solo puede existir una carga
activa por tenant a la vez.

## Documentación Técnica

La especificación completa de los endpoints, incluyendo parámetros, cuerpos de solicitud y esquemas de
respuesta, se encuentra en el archivo [openapi.yaml](openapi.yaml).

Este archivo sigue el estándar OpenAPI 3.0.3 y puede ser utilizado con herramientas como Swagger UI o Postman
para interactuar con la API.

## Documentación de la API de talento cloud generado con redoc
Para generar documento html
```bash
npx @redocly/cli build-docs openapi.yaml -t ../custom-template.hbs -o index.html
```

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\openapi.yaml
```

Para encriptar html previamente generado reemplazando el anterior
```bash
npx staticrypt index.html -p "TalentoCloud." --short -t ../login-template.html --template-title "Talento Cloud - Acceso a Documentación" --template-instructions "Ingresa la contraseña para ver la documentación de la API" --template-placeholder "Contraseña de acceso" --template-button "Desbloquear" --template-remember "Recordar contraseña" --remember 30 -d .
```
