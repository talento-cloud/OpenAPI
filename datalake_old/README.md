# API publica de talento cloud para entregar datos a proveedores como datalake 

En este proyecto se documenta API REST para entregar info a datalake el cual usa como método de autenticación Oauth 2.0 

## Atenticación 

Ejemplo para obtener token:

```bash
curl -X POST https://clientex.talento.cloud/oauth2/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=client_credentials" \
  -d "client_id=webhook-servicio" \
  -d "client_secret=mi-secreto" \
  -d "scope=talento.read"
```

Ejemplo de respuesta json:
```json
{
  "access_token": "eyJhbGci...",
  "token_type":   "Bearer",
  "expires_in":   3600,
  "scope":        "talento.read"
}
```

## Endpoints para consultar datos

### Selección - Reporte de selección detallado

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/seleccion/reporteDetallado/{banderaIncluirInactivos} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
      {
        "nro_solicitud": 12345,
        "cargo": "Auxiliar",
        "empresa" : "x",
        "ciudad" : "x",
        "solicitante": "x",
        "personaCancela" : "x",
        "personaCierra" : "x",
        "fechaSolicitud" : "2023-01-01",
        "fechaRadicacion" : "2023-01-02",
        "fechaAsignacionResponsable" : "2023-01-03",
        "fechaCancelacion" : "2023-01-04",
        "fechaCierre" : "2023-01-05",
        "tipoConvocatoria" : "x",
        "motivo": "x",
        "personasAReemplezar": "",
        "tipoSolicitud" : "x",
        "responsables": "",
        "porcentajeAvance": 50,
        "estadoProceso": "x",
        "fechaUltimaEtapa": "2023-01-06",
        "cantidadVacantesSolicitadas": 10,
        "cantidadVacantesPendientes": 5,
        "cantidadCandidatosConsiderados": 50,
        "cantidadCandidatosContratados": 1, 
        "vicepresidencia" : "x",
        "regional" : "x",
        "sede": "x",
        "lider": "",
        "justificacion": "x",
        "observaciones": "",
        "observacionesCancelacion": "",
        "cliente": "x",
        "ans": 30,
        "diasTranscurridos": 10,
        "cumplimiento": "No cumple",
        "diasTotales": 400,
        "fechaContratacion": "2023-01-07",
        "candidatoElegido": "x",
        "candidatoElegidoCedula": "x",
        "cubrimiento": "Externo",
        "criticidad": "",
        "centroCosto": ""
      }
    ]
  }
}
```

### Selección - Seguimiento por etapas

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/seleccion/seguimientoPorEtapa/{estado} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
            "proceso": "SEL-6",
            "cargo": "Analista contable",
            "empresa": "Talento cloud",
            "fechaSolicitud": "2023-01-01",
            "fechaAsignacionResponsables": "2023-01-02",
            "fechaCancelacion": "2023-01-03",
            "fechaCierre": "2023-01-04",
            "tipoConvocatoria": "MIXTA",
            "responsablesProceso": "x,y,z",
            "porcentajeAvance": 90,
            "estadoRequisicion": "Publicada",
            "fechaAprobacionFinal": "2023-01-05",
            "preseleccionFechaPrimerCandidato": "2023-01-06",
            "preseleccionFechaUltimoCandidato": "2023-01-07",
            "filtroTelefonicoFechaPrimerCandidato": "2023-01-06",
            "filtroTelefonicoFechaUltimoCandidato": "2023-01-07",
            "entrevistaGrupalFechaPrimerCandidato": "2023-01-06",
            "entrevistaGrupalFechaUltimoCandidato": "2023-01-07",
            "pruebaPsicotecnicaFechaPrimerCandidato": "2023-01-06",
            "pruebaPsicotecnicaFechaUltimoCandidato": "2023-01-07",
            "xxxFechaPrimerCandidato": "2023-01-06",
            "xxxFechaUltimoCandidato": "2023-01-07"
        }
    ]
  }
}
```    

### Formación - Avance por tema

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/formacion/avancePorTema/{incluirUsuarioInactivos}/{codTema}/{codAnio}/{fechaInicial}/{fechaFinal} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```        

### Bienestar - reporte detallado beneficios/reconocimientos

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/bienestar/reporteDetallado \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```      

### Bienestar - reporte transacciones puntos beneficios/reconocimientos

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/bienestar/transaccionesPuntos/{anio} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```

### HojaVida - Reporte datos básicos usuario interno

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/hojavida/datosBasicos \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```

### HojaVida - Información de nómina

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/hojavida/infoNomina \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```


### Objetivos Smart - Resultados consolidados de gestión (Todo el grupo)

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/objetivossmart/resultadosConsolidadosGestion/{anio} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```

### Objetivos Smart - Modelo mapa de desempeño

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/objetivossmart/modeloMapaDesempeno/{modeloMapaTalento}/{temporadaMT} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```

### Competencias - Detalle valoración de competencias (de todo el grupo)

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/competencias/detalleValoracion/{codProceso} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```

### Operativos (Dec) - Reporte operativos

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/operativosdec/reporte/{codMapaTalento}/{codTemporadaMT} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```

### Transversal - Reporte de todos los usuarios del sistema

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/transversar/todosUsuarios/{tipo} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```

### Transversal - Reporte de los usuarios activos

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/transversar/usuariosActivos \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```

### Transversal - Novedades

Solicitud:
```bash
curl -X GET https://clientex.talento.cloud/api/v1/transversar/novedades/{tipo} \
  -H "Authorization: Bearer eyJhbGci..."
```

Ejemplo respuesta:
```json
{
  "codigo": 200,
  "mensaje": "OK",
  "data": {
    "reporte": [
        {
        }
    ]
  }
}
```


## Documentación de la API de talento cloud generado con redoc
Para generar documento html
```bash
npx @redocly/cli build-docs openapi.yaml -t custom-template.hbs -o index.html
```

Para validar un archivo openai
```bash
redocly lint --extends=minimal .\openapi.yaml
```