# Project: Talento Publico API Documentation

## Directory Overview

This directory contains the API documentation for the "Talento Publico" API. It provides the necessary files to understand, test, and generate documentation for the API.

## Key Files

*   **`TalentoPublicoOpenApi3Json.json`**: This is the core of the project. It is the OpenAPI 3 specification that defines the "Talento Publico" API, including its endpoints, parameters, and responses.
*   **`Talento Publico.postman_collection.json`**: This is a Postman collection that can be imported into the Postman application. It provides a convenient way to test the API endpoints defined in the OpenAPI specification.
*   **`redoc-static.html`**: This is a static HTML file containing the human-readable API documentation. It is generated from the `TalentoPublicoOpenApi3Json.json` file using [ReDoc](https://github.com/Redocly/redoc).
*   **`README.md`**: This file provides basic instructions on how to generate the `redoc-static.html` documentation file.

## Usage

*   **Viewing the Documentation**: Open the `redoc-static.html` file in a web browser to view the API documentation.
*   **Testing the API**: Import the `Talento Publico.postman_collection.json` file into Postman to make requests to the API endpoints.
*   **Generating the Documentation**: To regenerate the `redoc-static.html` file, you need to have Node.js and npm installed. Then, run the following command in your terminal:
    ```bash
    npx @redocly/cli build-docs TalentoPublicoOpenApi3Json.json  -o index.html
    ```

## Otros comandos utiles:
Generación con plantilla personalizada:

```bash
npx @redocly/cli build-docs TalentoPublicoOpenApi3Json.json -t custom-template.hbs -o index.html
```


Tambien se puede instalar con npm usando:

```bash
npm install -g @redocly/cli
```

Para dividir archivo openapi:
```bash
redocly split .\TalentoPublicoOpenApi3Json.json --outDir=openapi
```

Para volver a unir divididos:
```bash
redocly bundle openapi/openapi.json --output dist/openapi.json
```