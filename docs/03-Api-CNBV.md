# API expuesta por las CNBV
## GET /api/solicitudReportes/{id}/estadoReporte
# Consultar estado

**URL** : `/api/solicitudReportes/{id}/estadoReporte`

**Método** : `GET`

**Autenticación requerida** : Si

**Parámetros de URL** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```id ```| ```integer``` |Identificador de la solicitud del reporte|

## Respuesta exitosa

**Condición** : Si se obtuvo el estado del reporte

**Código** : `200 Ok`

**Contenido de ejemplo**

```json
{
	"id": "ReporteSolicitado", 
	"descripcion": "Reporte solicitado",
	"nombre": "Reporte solicitado"
}
```

## Respuesta de error

**Condición** : Si

**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`
----------
## PUT /api/solicitudReportes/{id}/estadoReporte
# Notificar estado

Recibe la notificación del estado del reporte en el servidor de la ITF

**URL** : `/api/solicitudReportes/{id}/estadoReporte`

**Método** : `PUT`

**Autenticación requerida** : Si

**Parámetros de URL** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```id ```| ```integer``` |Identificador de la solicitud del reporte|

**Datos de ejemplo** Todos los campos deben ser enviados.

```json
{
  "id": "ReporteRecibido",
  "descripcion": "Reporte recibido",
  "nombre": "Reporte recibido"
}
```

## Respuesta exitosa

**Condición** : Si todo está bien y se actualizó la solicitud en el servidor de la CNBV.

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

## Respuesta de error

**Condición** : Si

**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`
----------
## GET /api/solicitudReportes/{id}/datos
# Consultar reporte

**URL** : `/api/solicitudReportes/{id}/datos`

**Método** : `GET`

**Autenticación requerida** : Si

**Parámetros de URL** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```id ```| ```integer``` |Identificador de la solicitud del reporte|
| ```page```| ```integer``` |Número de página solicitada|
| ```size```| ```integer``` |Número de registros de una página|

## Respuesta exitosa

**Condición** : Si se obtuvo la información solicitada del reporte

**Código** : `200 Ok`

**Parámetros Header** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```links```| ```string``` |Links de navegación|

**Contenido de ejemplo**

```json
{
	"solicitudReporte":{
	  "id": "5349b4ddd2781d08c09890a1"
	}
	"Dato":[
		{
			"Concepto":"100000000000",
			"Monto":1000000.0,
			"Moneda":1
		},
		{
			"Concepto":"110000000000",
			"Monto":200000.0,
			"Moneda":1
		},
		{
			"Concepto":"110100000000",
			"Monto":50000.0,
			"Moneda":1
		}
	]
}
```

## Respuesta de error

**Condición** : Si

**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`
-----------
## PUT /api/solicitudReportes/{id}/datos
# Recibir reporte

**URL** : `/api/solicitudReportes/{id}/datos`

**Método** : `PUT`

**Autenticación requerida** : Si

**Parámetros de URL** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```id ```| ```integer``` |Identificador de la solicitud del reporte|

**Parámetros Header** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```reporteCompletado```| ```boolean``` |Especifica si el paquete de datos es el ultimo y por tanto la transferencia del reporte se ha completado|

**Datos de ejemplo** Todos los campos deben ser enviados.

```json
{
	"solicitudReporte":{
	  "id": "5349b4ddd2781d08c09890a1"
	}
	"Dato":[
		{
			"Concepto":"100000000000",
			"Monto":1000000.0,
			"Moneda":1
		},
		{
			"Concepto":"110000000000",
			"Monto":200000.0,
			"Moneda":1
		},
		{
			"Concepto":"110100000000",
			"Monto":50000.0,
			"Moneda":1
		}
	]
}
```
## Respuesta exitosa

**Condición** : Si se registró la información recibida del reporte

**Código** : `200 Ok`

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

## Respuesta de error

**Condición** : Si

**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`
----------
## GET /api/reportes/{id}
# Consultar información del reporte

**URL** : `/api/reportes/{id}`

**Método** : `GET`

**Autenticación requerida** : Si

**Parámetros** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```id ```| ```integer``` |Identificador de la solicitud del reporte|



## Respuesta exitosa

**Condición** : Si se obtuvo la información del reporte

**Código** : `200 Ok`

**Contenido de ejemplo**

```json
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
}
```

## Respuesta de error

**Condición** : Si

**Código** : `401 Unauthorized`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `403 Forbidden`

**Headers** : `{}`

**Content** : `{}`

### O

**Condición** : Si

**Código** : `404 Not Found`

**Headers** : `{}`

**Content** : `{}`
