En el archivo openapi.yaml quiero modificar el endoint /slc/magneto/webhook/{tenant} para cambiarlo por otro que defino a continuación:
De titulo "WebHook para Secofa"

El siguiente es el curl del endpoint
```bash
curl --location 'https://somostalentoalianza.talento-dev.cloud/api/slc/secofa/webhook/{tenant}' \ 
 --header 'Authorization: Bearer <TU_TOKEN_JWT>' 
 --data '{
    "id_estudio_generado": "15092026_9966310000",
    "archivo_base64": "JVBERi0xLjQKJcOkw7zDtsOfCjIgMCBvYmoKPDwvTGVuZ3RoIDMgMCBSL0ZpbHRlci9GbGF0ZURlY29kZT4+CnN0cmVhbQp4nJ1YyY7jNhC9..."
}'   
```

Un ejemplo de la respuesta es el siguiente json:

{
    "message": "Datos del candidato de Secofa recibidos",
    "success": true,
    "idEstudioGenerado": "15092026_9966330000"
}
