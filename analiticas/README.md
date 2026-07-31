# API de talento cloud para Analíticas (PowerBI)

En este proyecto se documenta la API REST usada por PowerBI para consumir datos analíticos de talento cloud. Cada módulo de negocio se agrupa como un tag dentro de la misma especificación (ej. `HojaDeVida`, `Seleccion`); los nuevos módulos de analíticas que se documenten se agregan como tags adicionales en este mismo `openapi.yaml`, sin crear directorios nuevos.

## Documentación de la API de talento cloud generado con redoc
Para generar documento html
```bash
npx @redocly/cli build-docs openapi.yaml -t ../custom-template.hbs -o index.html
```

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\openapi.yaml
```
