# Notificar estado

Recibe la notificación del estado del reporte en el servidor de la ITF

**URL** : `/api/solicitudReportes/{id}/estadoReporte`

**Método** : `PUT`

**Autenticación requerida** : Si

**Datos de ejemplo** Todos los campos deben ser enviados.

```json
{
  "id": "9874b4ddd2781d08c12889a1",
  "descripcion": "Reporte recibido",
  "nombre": "Reporte recibido"
}
```

## Respuesta exitosa

**Condición** : Si todo está bien y se actualizó la solicitud en el servidor de la ITF.

**Código** : `200 Ok`

**Contenido de ejemplo**

```json
{
    "id": "5349b4ddd2781d08c12889a1",
	"cadenaOriginal": "string",
	"fechaAcuse": "2018-09-13T13:00:00",
	"selloDigital": "9gekFpfoFhB9DhYhozT6HQbW4cOZFGVSI8XkTcxzXUqSGawHFOGgIpiUAdXSNhdgAIuKEJM7BUaB8mkMv/pvt2IUZ+==",
	"solicitudReporte":{
	  "id": "5349b4ddd2781d08c09890a1",
	  "estadoReporte": {
		"id": "5349b4ddd2781d08c09890b2",
		"descripcion": "Reporte solicitado",
		"nombre": "Reporte solicitado"
	  },
	  "fechaRecepcion": "2018-09-12",
	  "numeroEnvios": 1,
	  "reporte": {
		"id": "5349b4ddd2781d08c09890c3",
		"fechaLimiteRecepcion": "2018-09-28",
		"fechaSolicitud": "2018-09-12",
		"periodo": {
		  "id": "string",
		  "fechaFin": "2018-09-01T00:00:00",
		  "fechaInicio": "2018-09-01T23:59:59"
		},
		"tipoFlujo": {
		  "id": "5349b4ddd2781d08c09890d4",
		  "descripcion": "Reporte que tendrá disponible la ITF para su consulta",
		  "nombre": "CONSULTA_REPORTE"
		},
		"tipoReporte": {
		  "id": "5349b4ddd2781d08c09890e5",
		  "descripcion": "Reporte que cumple con el labor de supervisión en el seguimiento de temas financieros",
		  "nombre": "REGULATORIO"
		},
		"templateReporteCatalogoConceptos": {
		  "id": "5349b4ddd2781d08c09890f9",
		  "periodicidad": "Mensual",
		  "vigenciaInicio": "2018-01-01",
		  "vigenciaFin": "2018-12-31",
		  "TemplateReporte": {
			"id": "5349b4ddd2781d08c0989a21",
			"version": 1,
			"descripcion": "Catálogo mínimo",
			"descripcionCorta": "A-0111",
			"elementosPorPagina": 1000,
			"maxErrores": 1,
			"columnas": [
			  {
				"id": "5349b4ddd2781d08c0989b32",
				"nombre": "Concepto",
				"min": "",
				"max": "",
				"requerida": true,
				"formato": "string",
				"catalogoRelacionado": "Concepto"
			  },
			  {
				"id": "5349b4ddd2781d08c0989c45",
				"nombre": "Monto",
				"min": "0",
				"max": "",
				"requerida": true,
				"formato": "decimal",
				"catalogoRelacionado": ""
			  },
			  {
				"id": "5349b4ddd2781d08c0989d56",
				"nombre": "Moneda",
				"min": "",
				"max": "",
				"requerida": true,
				"formato": "int",
				"catalogoRelacionado": "Moneda"
			  }
			]
		  },
		  "catalogoConceptos": {
			"id": "5349b4ddd2781d08c0989e89",
			"version": 1,
			"conceptos": [
			  {
				"id": "5349b4ddd2781d08c09890f3",
				"concepto": "ACTIVO",
				"ordenPresentacion": 1,
				"conceptoPadreId": ""
			  },
			  {
				"id": "5349b4ddd2781d08c09890f4",
				"concepto": "DISPONIBILIDADES",
				"ordenPresentacion": 2,
				"conceptoPadreId": "5349b4ddd2781d08c09890f3"
			  },
			  {
				"id": "5349b4ddd2781d08c09890f5",
				"concepto": "CAJA",
				"ordenPresentacion": 3,
				"conceptoPadreId": "5349b4ddd2781d08c09890f4"
			  }
			]
		  }
		}
	  },
	  "tipoFlujo": {
		"id": "5349b4ddd2781d08c09890d4",
		"descripcion": "Reporte que tendrá disponible la ITF para su consulta",
		"nombre": "CONSULTA_REPORTE"
	  }
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