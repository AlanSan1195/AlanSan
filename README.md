# Portfolio Alan San

> Portfolio personal con Astro, TailwindCSS y efectos visuales inspirados en auroras boreales.

![Astro](https://img.shields.io/badge/Astro-5.11.0-orange) ![TailwindCSS](https://img.shields.io/badge/TailwindCSS-4.1.11-blue) ![TypeScript](https://img.shields.io/badge/TypeScript-strict-blue)

## Tecnologias

- **Astro 5.11** - Framework para sitios web estaticos
- **TailwindCSS 4.1** - Estilos utilitarios
- **TypeScript** - Tipado estricto

## Ultimo cambio: Rutas dinamicas para proyectos

Se implemento una ruta dinamica `[id].astro` que genera automaticamente todas las paginas de proyectos desde `projects.json`.

### Antes (8 archivos duplicados)

```
src/pages/
├── rocketchat.astro   # 9 lineas identicas
├── simpsons.astro     # 9 lineas identicas
├── gta.astro          # 9 lineas identicas
├── arkanoid.astro     # 9 lineas identicas
├── airpods.astro      # 9 lineas identicas
├── matera.astro       # 9 lineas identicas
├── valmari.astro      # 9 lineas identicas
└── suitch.astro       # 9 lineas identicas
```

Cada archivo tenia el mismo patron:

```astro
---
import ProjectDetail from "../components/ProjectDetail.astro";
import projectsData from "../data/projects.json";

const project = projectsData.rocketchat;
---

<ProjectDetail project={project} />
```

### Ahora (1 archivo dinamico)

```
src/pages/
└── [id].astro   # Genera todas las rutas
```

```astro
---
import ProjectDetail from "../components/ProjectDetail.astro";
import projectsData from "../data/projects.json";

export function getStaticPaths() {
  return Object.values(projectsData).map((project) => ({
    params: { id: project.id },
    props: { project },
  }));
}

const { project } = Astro.props;
---

<ProjectDetail project={project} />
```

### Beneficios

| Aspecto | Antes | Ahora |
|---------|-------|-------|
| Archivos de pagina | 8 | 1 |
| Lineas de codigo | ~72 | ~15 |
| Agregar proyecto | Crear archivo .astro | Solo editar JSON |
| Mantenimiento | Cambiar 8 archivos | Cambiar 1 archivo |

### Como agregar un nuevo proyecto

Solo agrega el objeto a `src/data/projects.json`:

```json
{
  "nuevo-proyecto": {
    "id": "nuevo-proyecto",
    "order": 9,
    "title": "Mi Nuevo Proyecto",
    ...
  }
}
```

La ruta `/nuevo-proyecto` se genera automaticamente en el build.

## Estructura actual

```
src/
├── components/
│   ├── Grid.astro           # Grid principal del home
│   ├── ProjectDetail.astro  # Detalle de proyecto (reutilizable)
│   ├── Hero.astro
│   ├── Header.astro
│   ├── Footer.astro
│   └── Social.astro
├── data/
│   ├── projects.json        # Fuente unica de datos
│   └── project-template.json
├── layouts/
│   └── Layout.astro
├── pages/
│   ├── index.astro          # Home
│   ├── proyectos.astro      # Listado de proyectos
│   └── [id].astro           # Rutas dinamicas de proyectos
└── styles/
    └── global.css
```

## Flujo de datos

```
projects.json
    │
    ├──> Grid.astro (extrae latestProject, beforeLastProject)
    │
    ├──> proyectos.astro (lista todos excepto suitch)
    │
    └──> [id].astro ──> ProjectDetail.astro (detalle individual)
```

## Comandos

```bash
pnpm install   # Instalar dependencias
pnpm dev       # Servidor de desarrollo
pnpm build     # Build para produccion
pnpm preview   # Preview del build
```

---

**Desarrollado por Alan San**
