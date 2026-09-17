# API de Estructura Organizacional

Este documento describe la API para la gestión de la Estructura Organizacional de Talento Cloud.

## Descripción General

La API de Estructura Organizacional permite a los clientes construir y gestionar un organigrama jerárquico. Proporciona endpoints para:

*   Visualizar la estructura completa.
*   Crear y eliminar posiciones.
*   Asignar y desvincular ocupantes de las posiciones.
*   Consultar catálogos de datos como cargos y niveles organizacionales.
*   Obtener información sobre los usuarios dentro de la estructura.

## Documentación Técnica

La especificación completa de los endpoints, incluyendo parámetros, cuerpos de solicitud y esquemas de respuesta, se encuentra en el archivo [openapi.yaml](openapi.yaml).

Este archivo sigue el estándar OpenAPI 3.0.3 y puede ser utilizado con herramientas como Swagger UI o Postman para interactuar con la API.

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
