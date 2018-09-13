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