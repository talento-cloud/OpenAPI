# API publica de talento cloud para entregar datos a proveedores como datalake 

En este proyecto se documenta API REST para entregar info

## Documentación de la API de talento cloud generado con redoc
Para generar documento html
```bash
npx @redocly/cli build-docs openapi.yaml -t custom-template.hbs -o index.html
```

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\openapi.yaml
```

Para encriptar html previamente generado reemplazando el anterior (dentro de cada subcarpeta)
```bash
npx staticrypt index.html -p "TalentoCloud." --short -t ../login-template.html --template-title "Talento Cloud - Acceso a Documentación" --template-instructions "Ingresa la contraseña para ver la documentación de la API" --template-placeholder "Contraseña de acceso" --template-button "Desbloquear" --template-remember "Recordar contraseña" --remember 30 -d .
```