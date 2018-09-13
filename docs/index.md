# API CNBV 


## Flujo de una solicitud

### Flujo 1 "Consulta":  La CNBV consulta los datos del reporte expuestos en el servidor de la ITF

* **Flujo Ideal**

    * **1.-** La CNBV crea una "SolicituReporte" en el servidor de la ITF (POST /api/solicitudReportes)
    * **2.-** La ITF actualiza el "EstadoReporte" a "ListoParaConsultarReporte" en el servidor de la CNBV (PUT /api/solicitudReportes/{id}/estadoReporte)
    * **3.-** La CNBV consulta un arreglo de "Dato" de la "SolicitudReporte" en el servidor de la ITF (GET /api/solicitudReportes/{id}/datos)
    * **4.-** La CNBV actualiza el "EstadoReporte" a "ReporteConsultado" en el servidor de la ITF (PUT /api/solicitudReportes/{id}/estadoReporte)
    * **5a.-** Si el reporte tiene errores: La CNBV actualiza el "EstadoReporte" a "ValidadoConErrores" en el servidor de la ITF (PUT /api/solicitudReportes/{id}/estadoReporte). La ITF después de corregir el reporte volverá a ejecutar el punto 2 del proceso 
    * **5b.-** Si el reporte es aceptado: La CNBV actualiza el "EstadoReporte" a "ReporteAceptado" en el servidor de la ITF (PUT /api/solicitudReportes/{id}/estadoReporte)


* **Flujo Alterno**

    En caso de que la ITF no ejecute el paso 2 del **Flujo Ideal** en el tiempo que la CNBV determine se seguirá con este flujo alterno

    * **2.-** La CNBV actualiza el "TipoFlujo" a "ENVIO" en el servidor de la ITF (PUT /api/solicitudReportes/{id}/tipoFlujo)

    Una vez actualizado el "TipoFlujo" se deberá continuar con el **Flujo 2 "Envio"**


### Flujo 2 "Envio":  La ITF envía los datos del reporte al servidor de la CNBV

* **1.-** La CNBV crea una "SolicituReporte" en el servidor de la ITF (POST /api/solicitudReportes)
* **2.-** La ITF envía un arreglo de "Dato" de la "SolicitudReporte" al servidor de la ITF (PUT /api/solicitudReportes/{id}/datos)
* **3a.-** Si el reporte tiene errores: La CNBV actualiza el "EstadoReporte" a "ValidadoConErrores" en el servidor de la ITF (PUT /api/solicitudReportes/{id}/estadoReporte). La ITF después de corregir el reporte volverá a ejecutar el punto 2 del proceso 
* **3b.-** Si el reporte es aceptado: La CNBV actualiza el "EstadoReporte" a "ReporteAceptado" en el servidor de la ITF (PUT /api/solicitudReportes/{id}/estadoReporte)


## Ejemplos de las llamadas a las APIs

### **API expuesta por las ITF**
#### **POST /api/solicitudReportes**

**URL** : `/api/solicitudReportes`

**Método** : `POST`

**Autenticación requerida** : Si

**Datos de ejemplo** Todos los campos deben ser enviados.

```json
{
  "id": "5349b4ddd2781d08c09890a1",
  "estadoReporte": {
    "id": "5349b4ddd2781d08c09890b2",
    "descripcion": "Reporte solicitado",
    "nombre": "Reporte solicitado"
  },
  "reporte": {
    "id": "5349b4ddd2781d08c09890c3",
    "fechaLimiteRecepcion": "2018-09-28",
    "fechaSolicitud": "2018-09-12",
    "periodo": {
      "id": "201808",
      "fechaFin": "2018-09-01T00:00:00",
      "fechaInicio": "2018-09-30T23:59:59"
    },
    "tipoFlujo": {
      "id": "CONSULTA",
      "descripcion": "La CNBV consulta los datos del reporte expuestos en el servidor de la entidad supervisada",
      "nombre": "Consulta"
    },
    "tipoReporte": {
      "id": "REGULATORIO",
      "descripcion": "Reporte que cumple con la labor de supervisión en el seguimiento de temas financieros",
      "nombre": "Regulatorio"
    },
    "templateReporteCatalogoConceptos": {
      "id": "5349b4ddd2781d08c09890f9",
      "periodicidad": "Mensual",
      "vigenciaInicio": "2018-01-01",
      "vigenciaFin": "2018-12-31",
      "TemplateReporte": {
        "id": "CAT_MINIMO",
        "version": 1,
        "descripcion": "Catálogo mínimo",
        "descripcionCorta": "A-0111",
        "elementosPorPagina": 1000,
        "maxErrores": 1000,
        "columnas": [
          {
            "id": "5349b4ddd2781d08c0989b32",
            "nombre": "Concepto",
            "min": "12",
            "max": "12",
            "requerida": true,
            "tipoDato": "string",
            "formato": "############",
            "catalogoRelacionado": "Concepto"
          },
          {
            "id": "5349b4ddd2781d08c0989c45",
            "nombre": "Monto",
            "requerida": true,
            "tipoDato": "decimal"
          },
          {
            "id": "5349b4ddd2781d08c0989d56",
            "nombre": "Moneda",
            "requerida": true,
            "tipoDato": "int",
            "catalogoRelacionado": "Moneda"
          }
        ]
      },
      "catalogoConceptos": {
        "id": "IFC_CAT_MINIMO",
        "version": 1
      }
    }
  },
  "tipoFlujo": {
      "id": "CONSULTA",
      "descripcion": "La CNBV consulta los datos del reporte expuestos en el servidor de la entidad supervisada",
      "nombre": "Consulta"
    }
}
```

## Respuesta exitosa

**Condición** : Si todo está bien y se registró la solicitud en el servidor de la ITF.

**Código** : `201 Created`

**Contenido de ejemplo**

```json
{
    "id": "5349b4ddd2781d08c09890a1",
    "cadenaOriginal": "CAT_MINIMO|201808|Prestadero|2018-09-01",
    "fechaAcuse": "2018-09-01",
    "selloDigital": "5349b4ddd2781d08c09890a15349b4ddd2781d08c09890a15349b4ddd2781d08c09890a1",
    "solicitudReporte":{
        "id": "5349b4ddd2781d08c09890a1"
    }
}
```

## Respuesta de error

**Condición** : Si

**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

### Or

**Condición** : Si

**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

### Or

**Condición** : Si

**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`


* **GET /api/solicitudReportes/{id}/datos**
* **PUT /api/solicitudReportes/{id}/estadoReporte**
* **PUT /api/solicitudReportes/{id}/tipoFlujo**

### **API expuesta por La CNBV**
* **GET /api/solicitudReportes/{id}/estadoReporte**
* **PUT /api/solicitudReportes/{id}/estadoReporte**
* **GET /api/solicitudReportes/{id}/datos**
* **PUT /api/solicitudReportes/{id}/datos**

 





