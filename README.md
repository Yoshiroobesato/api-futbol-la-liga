# 🏆 UltraTV LaLiga API

API RESTful que proporciona información actualizada sobre la Liga Española de Fútbol, incluyendo tabla de posiciones, calendario de partidos y plantillas de equipos.

[![API Status](https://img.shields.io/badge/status-active-success.svg)](https://rapidapi.com/obesatoy/api/api-futbol-espana)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Documentation](https://img.shields.io/badge/docs-OpenAPI-green.svg)](https://ultratv.neocities.org/docs)

## 📋 Tabla de Contenidos

- [Características](#-características)
- [Requisitos](#-requisitos)
- [Uso](#-uso)
- [Endpoints](#-endpoints)
- [Ejemplos](#-ejemplos)
- [Respuestas de Error](#-respuestas-de-error)
- [Limitaciones de Uso](#-limitaciones-de-uso)
- [Contribuir](#-contribuir)
- [Licencia](#-licencia)

## ✨ Características

- Tabla de posiciones actualizada de LaLiga
- Calendario y resultados de partidos por jornada
- Información detallada de equipos y plantillas
- Respuestas JSON bien estructuradas
- Manejo de errores estandarizado
- Documentación completa con OpenAPI



## 📚 Uso

La API está disponible en `api-futbol-espana.p.rapidapi.com`. Todas las respuestas son en formato JSON y deben incluir la cabecera:

```http
Accept: application/json
```
```API https://rapidapi.com/obesatoy/api/api-futbol-espana
```

## 🔌 Endpoints

### Tabla de Posiciones

```http
GET /api/liga/espana/tabla
```

Retorna la tabla de posiciones actualizada de LaLiga.

#### Respuesta

```json
{
  "data": [
    {
      "pos": "1",
      "img": "url_escudo",
      "equipo": "Real Madrid",
      "puntos": "70",
      "pj": "30",
      "pg": "22",
      "pe": "4",
      "pp": "4",
      "gf": "60",
      "gc": "20"
    }
  ],
  "attribution": "Powered by UltraTV"
}
```

### Agenda de Jornada

```http
GET /api/liga/espana/{jornada}/agenda
```

Retorna los partidos de una jornada específica.

#### Parámetros

| Nombre   | Tipo    | Descripción           |
|----------|---------|----------------------|
| jornada  | integer | Número de la jornada (1-38) |

#### Respuesta

```json
{
  "data": [
    {
      "local": "Barcelona",
      "visitante": "Real Madrid",
      "resultado": "2-1"
    }
  ],
  "attribution": "Powered by UltraTV"
}
```

### Lista de Equipos

```http
GET /api/liga/espana/equipos
```

Retorna la lista completa de equipos con sus IDs.

### Plantel de Equipo

```http
GET /api/liga/espana/{id}/plantel
```

Retorna la plantilla completa de un equipo específico.

## 🎯 Ejemplos

### Consultar Tabla con curl

```bash
GET /api/liga/espana/:id/plantel HTTP/1.1
X-Rapidapi-Key: TU API KEY
X-Rapidapi-Host: api-futbol-espana.p.rapidapi.com
Host: api-futbol-espana.p.rapidapi.com

```

### Consultar Plantel con JavaScript

```javascript
const data = null;

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener('readystatechange', function () {
	if (this.readyState === this.DONE) {
		console.log(this.responseText);
	}
});

xhr.open('GET', 'https://api-futbol-espana.p.rapidapi.com/api/liga/espana/:id/plantel');
xhr.setRequestHeader('x-rapidapi-key', 'TU API KEY');
xhr.setRequestHeader('x-rapidapi-host', 'api-futbol-espana.p.rapidapi.com');

xhr.send(data);
```

## ❌ Respuestas de Error

La API utiliza códigos de estado HTTP estándar. Los errores son retornados en el siguiente formato:

```json
{
  "error": {
    "status": 404,
    "message": "Equipo no encontrado",
    "attribution": "Powered by UltraTV - https://ultratv.neocities.org/"
  }
}
```

### Códigos de Estado

- `200`: Éxito
- `400`: Error en la solicitud
- `404`: Recurso no encontrado
- `429`: Demasiadas solicitudes
- `500`: Error interno del servidor

## ⚠️ Limitaciones de Uso

- Máximo 500 solicitudes
- Datos actualizados cada 5 minutos
- Uso comercial requiere autorización previa

## 🤝 Contribuir

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia Apache 2.0 - ver el archivo [LICENSE](LICENSE) para más detalles.

---

Desarrollado con ❤️ por [UltraTV](https://ultratv.neocities.org)
