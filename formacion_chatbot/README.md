# API de talento cloud para Formación

En este proyecto se documenta API REST para el módulo de Formación pensado para ser consultado por chatbot ClaudIA

## Documentación de la API de talento cloud generado con redoc
Para generar documento html
```bash
npx @redocly/cli build-docs openapi.yaml -t ../custom-template.hbs -o index.html
```

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\openapi.yaml
```
