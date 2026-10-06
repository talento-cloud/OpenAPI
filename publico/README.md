# API de talento cloud para Datalake

En este proyecto se documenta API REST para módulo de Datalake

## Documentación de la API de talento cloud generado con redoc

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\openapi.yaml
```

Para generar documento html
```bash
npx @redocly/cli build-docs openapi.yaml -t ../custom-template.hbs -o index.html
```

