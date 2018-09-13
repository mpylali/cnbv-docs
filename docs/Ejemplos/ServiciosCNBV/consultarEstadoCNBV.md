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