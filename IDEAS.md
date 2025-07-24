# 💡 Ideas y Roadmap del Portfolio

> Archivo para documentar ideas futuras, mejoras planificadas y mantener el contexto del proyecto.

## 🚀 Ideas Próximas a Implementar

### 📝 **Sistema de Posts Dinámico**

#### **Problema Actual:**
- El post en la sección `id="Post"` es estático
- No hay historial de posts anteriores
- Contenido hardcodeado en el componente

#### **Solución Propuesta:**
```astro
<!-- Estructura objetivo -->
<section id="Post" aria-label="Últimos posts">
  {posts.map(post => (
    <article>
      <header>
        <time datetime={post.date}>{post.formattedDate}</time>
      </header>
      <h3>{post.title}</h3>
      <p>{post.description}</p>
      <a href={`/posts/${post.slug}`}>Leer más</a>
    </article>
  ))}
</section>
```

#### **Implementación Sugerida:**
1. **Crear estructura de datos para posts:**
   ```typescript
   interface Post {
     id: string;
     title: string;
     description: string;
     date: Date;
     slug: string;
     category: string;
     tags: string[];
   }
   ```

2. **Opciones de almacenamiento:**
   - **Archivos Markdown** en `/src/content/posts/`
   - **JSON local** en `/src/data/posts.json`
   - **CMS headless** (Strapi, Contentful)
   - **Base de datos** (Supabase, PlanetScale)

3. **Páginas a crear:**
   - `/posts` - Lista de todos los posts
   - `/posts/[slug]` - Post individual
   - Componente `PostCard.astro`
   - Componente `PostList.astro`

### 🔧 **Componentización Avanzada**

#### **Componentes a Extraer:**
```
src/components/
├── blog/
│   ├── PostCard.astro
│   ├── PostList.astro
│   ├── PostMeta.astro
│   └── CategoryTag.astro
├── ui/
│   ├── Button.astro
│   ├── Card.astro
│   └── Badge.astro
└── layout/
    ├── GridContainer.astro
    └── Section.astro
```

#### **Props Interface:**
```typescript
// PostCard.astro
interface Props {
  title: string;
  description: string;
  date: Date;
  category: string;
  slug: string;
  featured?: boolean;
}
```

### 🗄️ **Sistema de Contenido**

#### **Opción 1: Astro Content Collections**
```typescript
// astro.config.mjs
import { defineConfig } from 'astro/config';

export default defineConfig({
  experimental: {
    contentCollections: true
  }
});

// src/content/config.ts
import { defineCollection, z } from 'astro:content';

const posts = defineCollection({
  schema: z.object({
    title: z.string(),
    description: z.string(),
    date: z.date(),
    category: z.string(),
    tags: z.array(z.string()),
    featured: z.boolean().default(false)
  })
});

export const collections = { posts };
```

#### **Opción 2: Base de Datos Simple**
```typescript
// src/lib/posts.ts
import type { Post } from '../types/post';

const posts: Post[] = [
  {
    id: '1',
    title: 'Aprendiendo Grid y Tailwind',
    description: 'Explorando CSS Grid y TailwindCSS...',
    date: new Date('2024-12-20'),
    slug: 'aprendiendo-grid-tailwind',
    category: 'Frontend',
    tags: ['CSS', 'TailwindCSS', 'Grid']
  }
];

export const getAllPosts = () => posts;
export const getLatestPost = () => posts[0];
export const getPostBySlug = (slug: string) => 
  posts.find(post => post.slug === slug);
```

## 🎯 **Roadmap de Desarrollo**

### **Fase 1: Fundación (Próxima)**
- [ ] Crear tipos TypeScript para posts
- [ ] Implementar sistema de datos local
- [ ] Componentizar PostCard
- [ ] Crear página `/posts`

### **Fase 2: Contenido Dinámico**
- [ ] Implementar Astro Content Collections
- [ ] Crear posts en Markdown
- [ ] Sistema de categorías y tags
- [ ] Paginación de posts

### **Fase 3: Funcionalidades Avanzadas**
- [ ] Búsqueda de posts
- [ ] Filtros por categoría
- [ ] RSS feed
- [ ] Comentarios (opcional)

### **Fase 4: Optimización**
- [ ] Lazy loading de imágenes
- [ ] Optimización de rendimiento
- [ ] PWA features
- [ ] Analytics

## 🛠️ **Mejoras Técnicas Pendientes**

### **SEO y Performance**
- [ ] Implementar sitemap dinámico
- [ ] Optimizar Core Web Vitals
- [ ] Añadir meta tags dinámicos por post
- [ ] Implementar JSON-LD para posts

### **Accesibilidad**
- [ ] Navegación por teclado mejorada
- [ ] Skip links
- [ ] Modo alto contraste
- [ ] Reducción de movimiento

### **UX/UI**
- [ ] Modo oscuro/claro toggle
- [ ] Animaciones de transición entre páginas
- [ ] Loading states
- [ ] Error boundaries

## 💭 **Ideas Creativas**

### **Funcionalidades Únicas**
- [ ] Timeline interactivo de aprendizaje
- [ ] Mapa de tecnologías dominadas
- [ ] Calculadora de experiencia
- [ ] Generador de CV dinámico

### **Integraciones**
- [ ] GitHub API para mostrar repos activos
- [ ] Dev.to API para posts externos
- [ ] LinkedIn API para experiencia
- [ ] Spotify API para música mientras codifico

## 📋 **Notas de Implementación**

### **Estructura de Archivos Sugerida:**
```
src/
├── content/
│   └── posts/
│       ├── 2024-12-20-grid-tailwind.md
│       └── 2024-12-21-semantic-html.md
├── components/
│   ├── blog/
│   ├── ui/
│   └── layout/
├── pages/
│   ├── posts/
│   │   ├── index.astro
│   │   └── [slug].astro
│   └── index.astro
├── types/
│   └── post.ts
└── utils/
    ├── posts.ts
    └── date.ts
```

### **Comandos Útiles:**
```bash
# Crear nuevo post
npm run new-post "Título del Post"

# Generar sitemap
npm run build:sitemap

# Optimizar imágenes
npm run optimize:images
```

---

**📝 Nota:** Este archivo debe actualizarse regularmente con nuevas ideas y el progreso de implementación.

**🎯 Próximo paso:** Comenzar con la Fase 1 - Crear tipos TypeScript y componentizar PostCard.