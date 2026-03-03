### Documentación de la API de talento cloud generado con redoc


Ejemplo de generación:

```bash
npx @redocly/cli build-docs TalentoPublicoOpenApi3Json.json -o index.html
```

O con plantilla:

```bash
npx @redocly/cli build-docs TalentoPublicoOpenApi3Json.json -t custom-template.hbs -o index.html
npx @redocly/cli build-docs dist/openapi.json -t custom-template.hbs -o index.html
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

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\TalentoPublicoOpenApi3Json.json
redocly lint --extends=minimal .\dist\openapi.json
```

#### Extras
Para migrar de postman a redoc primero hay que exportar el archivo de postman en formato json y luego convertirlo a formato openapi lo cual se puede lograr con https://www.apimatic.io/transformer 

#### Bibliografía
- https://redocly.com/docs/cli/commands/build-docs#use-a-custom-template
- https://github.com/Redocly/redoc