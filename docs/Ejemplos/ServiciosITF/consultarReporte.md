# Consultar reporte

**URL** : `/api/solicitudReportes/{id}/datos`

**Método** : `GET`

**Autenticación requerida** : Si

**Parámetros** Todos los parámetros deben ser enviados.

| Nombre|Tipo|Descripción|
| :--: |:--:| :--:|
| ```id ```| ```integer``` |Identificador de la solicitud del reporte|
| ```page```| ```integer``` |Número de página solicitada|
| ```size```| ```integer``` |Número de registros de una página|


## Respuesta exitosa

**Condición** : Si se obtuvo la información solicitada del reporte

**Código** : `200 Ok`

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