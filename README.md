### Documentación de la API de talento cloud generado con redoc


Ejemplo de generación:

```bash
npx @redocly/cli build-docs TalentoPublicoOpenApi3Json.json -o index.html
```

O con plantilla:

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

#### Bibliografía
- https://redocly.com/docs/cli/commands/build-docs#use-a-custom-template
- https://github.com/Redocly/redoc