# API de talento cloud para Analíticas - Selección

En este proyecto se documenta la API REST usada por PowerBI para consumir datos analíticos del módulo de Selección (procesos de requisición, candidatos, etapas, encuestas de satisfacción y maestros) de talento cloud

## Documentación de la API de talento cloud generado con redoc
Para generar documento html
```bash
npx @redocly/cli build-docs openapi.yaml -t ../../custom-template.hbs -o index.html
```

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\openapi.yaml
```
