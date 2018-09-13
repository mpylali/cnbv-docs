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