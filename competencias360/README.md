# API de talento cloud para módulo de valoración de competencias 360 

En este proyecto se documenta API REST para entregar info

## Documentación de la API de talento cloud generado con redoc
Para generar documento html
```bash
npx @redocly/cli build-docs openapi.yaml -t ../custom-template.hbs -o index.html
```

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\openapi.yaml
```