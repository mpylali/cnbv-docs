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