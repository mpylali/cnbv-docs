# API expuesta por las ITF

## POST /api/solicitudReportes

**URL** : `/api/solicitudReportes`

**Método** : `POST`

**Autenticación requerida** : Si

**Datos de ejemplo** Todos los campos deben ser enviados.

```json
{
  "id": "5349b4ddd2781d08c09890a1",
  "estadoReporte": {
    "id": "Solicitado",
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

### Respuesta exitosa

**Código** : `201 Created`

**Contenido de ejemplo**

```json
{
    "id": "5349b4ddd2781d08c09890a1",
    "cadenaOriginal": "5349b4ddd2781d08c09890a1|Solicitado|CAT_MINIMO|201808|Prestadero|2018-09-01",
    "fechaAcuse": "2018-09-01",
    "selloDigital": "5349b4ddd2781d08c09890a15349b4ddd2781d08c09890a15349b4ddd2781d08c09890a1",
    "solicitudReporte":{
        "id": "5349b4ddd2781d08c09890a1"
    }
}
```

### Respuesta de error

**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

#### Or

**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

#### Or

**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`

---------
## GET /api/solicitudReportes/{id}/datos

**URL** : `/api/solicitudReportes/{id}/datos?page={page}&size={size}`

**Método** : `GET`

**Autenticación requerida** : Si

**Parámetros URL** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```id ```| ```integer``` |Identificador de la solicitud del reporte|
| ```page```| ```integer``` |Número de página solicitada|
| ```size```| ```integer``` |Número de registros de una página|

### Respuesta exitosa

**Código** : `200 Ok`

**Header de ejemplo**
| Header | Valor |
| :--: |:--:|
| ```link ```| <https://itf.com/api/solicitudReportes/5349b4ddd2781d08c09890a1/datos?page=3&size=5>; rel="prev", <https://itf.com/api/solicitudReportes/5349b4ddd2781d08c09890a1/datos?page=6&size=5>; rel="next", <https://itf.com/api/solicitudReportes/5349b4ddd2781d08c09890a1/datos?page=10&size=5>; rel="last", <https://itf.com/api/solicitudReportes/5349b4ddd2781d08c09890a1/datos?page=1&size=5>; rel="first" |

**Contenido de ejemplo**

```json
{
	"solicitudReporte":{
	  "id": "5349b4ddd2781d08c09890a1"
	}
	"Dato":[
		{
			"Concepto":"100000000000",
			"Monto":"1000000.0",
			"Moneda":"1"
		},
		{
			"Concepto":"110000000000",
			"Monto":"200000.0",
			"Moneda":"1"
		},
		{
			"Concepto":"110100000000",
			"Monto":"50000.0",
			"Moneda":"1"
		}
	]
}
```

### Respuesta de error

**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

#### Or

**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

#### Or

**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`

---------

## PUT /api/solicitudReportes/{id}/estadoReporte
**URL** : `/api/solicitudReportes/{id}/estadoReporte`

**Método** : `PUT`

**Autenticación requerida** : Si

**Datos de ejemplo** Todos los campos deben ser enviados.

```json
{
  "id": "ReporteAceptado",
  "descripcion": "Reporte aceptado",
  "nombre": "Reporte aceptado"
}
```

### Respuesta exitosa

**Código** : `200 Ok`

**Contenido de ejemplo**

```json
{
    "id": "5349b4ddd2781d08c09890a1",
    "cadenaOriginal": "5349b4ddd2781d08c09890a1|ReporteAceptado|CAT_MINIMO|201808|Prestadero|2018-09-01",
    "fechaAcuse": "2018-09-01",
    "selloDigital": "5349b4ddd2781d08c09890a15349b4ddd2781d08c09890a15349b4ddd2781d08c09890a1",
    "solicitudReporte":{
        "id": "5349b4ddd2781d08c09890a1"
    }
}
```

### Respuesta de error



**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

#### Or



**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

#### Or



**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`

---------

## PUT /api/solicitudReportes/{id}/tipoFlujo
**URL** : `/api/solicitudReportes/{id}/estadoReporte`

**Método** : `PUT`

**Autenticación requerida** : Si

**Datos de ejemplo** Todos los campos deben ser enviados.

```json
{
  "id": "ENVIO",
  "descripcion": "Envio del reporte por parte de la ITF",
  "nombre": "Envio Reporte"
}
```

### Respuesta exitosa

**Código** : `200 Ok`

**Contenido de ejemplo**

```json
{
    "id": "5349b4ddd2781d08c09890a1",
    "cadenaOriginal": "5349b4ddd2781d08c09890a1|ReporteAceptado|CAT_MINIMO|201808|Prestadero|2018-09-01|ENVIO",
    "fechaAcuse": "2018-09-01",
    "selloDigital": "5349b4ddd2781d08c09890a15349b4ddd2781d08c09890a15349b4ddd2781d08c09890a1",
    "solicitudReporte":{
        "id": "5349b4ddd2781d08c09890a1"
    }
}
```

### Respuesta de error



**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

#### Or



**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

#### Or



**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`