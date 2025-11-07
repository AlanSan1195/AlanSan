# Estructura de Datos de Proyectos

Este directorio contiene la información de todos los proyectos en formato JSON para facilitar la reutilización y mantenimiento.

## 📁 Archivos

- `projects.json` - Contiene todos los datos de los proyectos

## 🔧 Estructura de Datos

Cada proyecto debe seguir esta estructura:

```json
{
  "nombre-proyecto": {
    "id": "nombre-proyecto",
    "title": "Título del Proyecto",
    "subTitle": "Descripción breve del proyecto",
    "image": {
      "src": "/imagenes/proyecto.webp",
      "alt": "Texto alternativo de la imagen"
    },
    "links": {
      "website": "https://proyecto.com",
      "github": "https://github.com/usuario/repo"
    },
    "review": [
      "Párrafo 1 de la descripción general",
      "Párrafo 2 de la descripción general"
    ],
    "technologies": [
      "Tecnología 1",
      "Tecnología 2",
      "Tecnología 3"
    ],
    "technologiesDetails": [
      {
        "name": "Nombre de la tecnología",
        "description": "Descripción detallada de cómo se usó"
      }
    ],
    "implementations": [
      "Implementación 1",
      "Implementación 2",
      "Implementación 3"
    ]
  }
}
```

## 📝 Campos

### Campos Obligatorios
- **id**: Identificador único del proyecto
- **title**: Título completo del proyecto
- **subTitle**: Descripción breve del proyecto
- **image.src**: Ruta a la imagen del proyecto
- **image.alt**: Texto alternativo de la imagen

### Campos Opcionales
- **links.website**: URL del sitio web del proyecto
- **links.github**: URL del repositorio en GitHub
- **review**: Array de párrafos con la descripción general (puede estar vacío)
- **technologies**: Array de tecnologías usadas (badges)
- **technologiesDetails**: Array de objetos con detalles de cada tecnología
- **implementations**: Array de puntos de implementación técnica

## 🚀 Uso

### 1. Agregar un Nuevo Proyecto

1. Abre `projects.json`
2. Agrega un nuevo objeto siguiendo la estructura
3. Crea una página en `src/pages/nombre-proyecto.astro`

### 2. Crear la Página del Proyecto

```astro
---
import ProjectDetail from "../components/ProjectDetail.astro";
import projectsData from "../data/projects.json";

const project = projectsData["nombre-proyecto"];
---

<ProjectDetail project={project} />
```

### 3. Agregar HTML en el Contenido

Puedes usar HTML en los strings de `review` e `implementations`:

```json
{
  "review": [
    "<strong class='text-white'>Texto destacado</strong> con contenido normal"
  ]
}
```

## ✨ Beneficios

- ✅ **Centralización**: Todos los datos en un solo lugar
- ✅ **Reutilización**: El componente `ProjectDetail` es reutilizable
- ✅ **Mantenimiento**: Fácil actualizar información
- ✅ **Escalabilidad**: Agregar nuevos proyectos es simple
- ✅ **Consistencia**: Todas las páginas siguen el mismo formato

## 📋 Ejemplo Completo

Ver `suitch` en `projects.json` para un ejemplo completo de uso.
