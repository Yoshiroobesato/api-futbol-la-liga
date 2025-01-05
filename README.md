# 🏆 UltraTV LaLiga API

API RESTful que proporciona información actualizada sobre la Liga Española de Fútbol, incluyendo tabla de posiciones, calendario de partidos y plantillas de equipos.

[![API Status](https://img.shields.io/badge/status-active-success.svg)](https://ultratv.neocities.org)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Documentation](https://img.shields.io/badge/docs-OpenAPI-green.svg)](https://ultratv.neocities.org/docs)

## 📋 Tabla de Contenidos

- [Características](#-características)
- [Requisitos](#-requisitos)
- [Instalación](#-instalación)
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

## 🛠 Requisitos

- Node.js 14.x o superior
- npm o yarn
- Acceso a internet para las consultas web

## 💻 Instalación

```bash
# Clonar el repositorio
git clone https://github.com/yourusername/ultratv-laliga-api.git

# Instalar dependencias
cd ultratv-laliga-api
npm install

# Configurar variables de entorno
cp .env.example .env
# Editar .env con tus configuraciones

# Iniciar el servidor
npm start
```

## 📚 Uso

La API está disponible en `https://api.ultratv.neocities.org`. Todas las respuestas son en formato JSON y deben incluir la cabecera:

```http
Accept: application/json
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
curl -X GET "https://api.ultratv.neocities.org/api/liga/espana/tabla" \
  -H "Accept: application/json"
```

### Consultar Plantel con JavaScript

```javascript
const getTeamSquad = async (teamId) => {
  try {
    const response = await fetch(
      `https://api.ultratv.neocities.org/api/liga/espana/${teamId}/plantel`
    );
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
};
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

- Máximo 100 solicitudes por minuto por IP
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
