# 🍖 La Matera - Restaurante Argentino

[![Astro](https://img.shields.io/badge/Astro-5.7.11-FF5D01?logo=astro&logoColor=white)](https://astro.build/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.3.2-38B2AC?logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Three.js](https://img.shields.io/badge/Three.js-0.162.0-000000?logo=three.js&logoColor=white)](https://threejs.org/)

![Vista previa del sitio](public/imagenes/preview.webp)

## 📋 Descripción del Proyecto

Este fue mi primer proyecto freelance real: un rediseño completo del sitio web para **La Matera**, un restaurante argentino en Guadalajara con gran tradición en la ciudad. El objetivo principal era crear una experiencia web más atractiva y moderna que mejorara la comunicación de los platillos hacia los clientes, alejándose del diseño anterior y generando mayor engagement.

### 🎯 Objetivos del Proyecto
- Rediseñar completamente la presencia web del restaurante
- Crear una experiencia visual atractiva que comunique la calidad de los platillos
- Mejorar la accesibilidad para reservaciones
- Mostrar el menú de forma interactiva y visualmente agradable
- Implementar efectos visuales que transmitan la atmósfera del restaurante

## 🚀 Tecnologías Utilizadas

- **Astro 5.7.11** - Framework principal (SSR mode)
- **Tailwind CSS 3.3.2** - Estilos y diseño responsivo
- **Three.js 0.162.0** - Efectos visuales 3D (partículas de humo)
- **Clerk** - Sistema de autenticación (implementado pero no utilizado en producción)
- **Node.js Adapter** - Para renderizado del lado del servidor

## ✨ Características Principales

### 🎨 Efectos Visuales
- **Efecto de humo con Three.js**: Animación de partículas 3D en el fondo que da profundidad y atmósfera
- **Video hero en la portada**: Presentación impactante del restaurante
- **Efectos de luces de fondo**: Ambiente visual mejorado
- **Máscaras degradadas**: Transiciones suaves entre secciones

### 📱 Secciones del Sitio
1. **Home/Reserva**: Landing page con video y CTA para reservar vía WhatsApp
2. **Carta Digital**: Menú completo organizado por categorías:
   - Empanadas
   - Pizzas
   - Entradas
   - Ensaladas
   - Cocina (pastas)
   - Campo (carnes)
   - Mar (mariscos)
   - Granja (pollo)
   - Postres
3. **Eventos**: Carrusel informativo sobre servicios de eventos
4. **Nosotros**: Historia y valores del restaurante

### 📐 Diseño Responsivo
- Mobile-first approach
- Navegación adaptable (menú hamburguesa en móvil)
- Carruseles horizontales optimizados para touch
- Imágenes optimizadas en formato WebP

## 🎓 Lo Que Aprendí (Reflexión Honesta)

### ✅ Logros
- **Primera experiencia real con un cliente**: Aprendí a comunicarme, recibir feedback y ajustar según las necesidades reales
- **Implementación de efectos avanzados**: Logré integrar Three.js para crear una experiencia visual única
- **Optimización de imágenes**: Todo el sitio usa WebP para mejor rendimiento
- **SEO básico**: Implementé meta tags, Open Graph y Twitter Cards
- **Responsive design**: El sitio funciona bien en diferentes dispositivos

### 🔧 Áreas de Mejora (Lo Que Haría Diferente Hoy)

#### Organización del Código
- **Datos hardcodeados**: El menú está directamente en el componente en lugar de estar en archivos JSON o una base de datos
- **Componentes grandes**: Algunos componentes como `pruebaCartaContenedor.astro` tienen demasiada responsabilidad
- **Nombres inconsistentes**: Mezcla de español e inglés en nombres de archivos y variables (ej: `Caurosel` en lugar de `Carousel`)
- **Componentes sin usar**: Varios archivos como `AsadosDeTira.astro`, `Filetes.astro` parecen no estar en uso

#### Arquitectura
- **Clerk sin uso**: Se instaló un sistema de autenticación completo que no se utiliza en producción
- **Falta de separación de concerns**: Lógica, datos y presentación mezclados en los mismos archivos
- **No hay gestión de estado**: Para una aplicación más compleja se necesitaría algo como Nanostores

#### Accesibilidad
- **Faltan algunos alt texts**: No todas las imágenes tienen descripciones significativas
- **Navegación por teclado**: Podría mejorarse la navegación sin mouse
- **Contraste de colores**: Algunas áreas con `text-white/65` podrían tener problemas de contraste

#### Performance
- **Video sin optimización**: El video de hero es grande y no tiene fallback
- **Lazy loading limitado**: No se implementó carga diferida en todas las imágenes
- **JavaScript no optimizado**: El efecto de humo se ejecuta constantemente

## 📦 Instalación y Uso

```bash
# Clonar el repositorio
git clone https://github.com/AlanSan1195/matera-landing.git

# Instalar dependencias
pnpm install

# Ejecutar en desarrollo
pnpm dev

# Construir para producción
pnpm build

# Vista previa de la build
pnpm preview
```

## 🌐 Despliegue

El sitio está configurado para SSR (Server-Side Rendering) con el adaptador de Node.js en modo standalone.

```bash
# Después de hacer build
node dist/server/entry.mjs
```

## 📁 Estructura del Proyecto

```
├── public/              # Archivos estáticos
│   ├── imagenes/       # Imágenes del sitio
│   ├── fuentes/        # Tipografías personalizadas
│   └── video.mp4       # Video hero
├── src/
│   ├── components/     # Componentes Astro reutilizables
│   ├── layouts/        # Layout principal
│   ├── pages/          # Rutas del sitio
│   └── middleware.ts   # Middleware de Clerk
├── astro.config.mjs    # Configuración de Astro
└── tailwind.config.cjs # Configuración de Tailwind
```

## 🎨 Personalización

### Fuentes
- **Lora Variable**: Fuente principal del sitio
- **Boldes (Magical Night)**: Fuente personalizada para títulos
- **Permanent Marker**: Fuente decorativa

### Colores (Tailwind)
```javascript
{
  primary: "#0C1018",   // Negro principal
  secundary: "#efefef", // Blanco/Gris claro
  tercero: "#ff3b3f",   // Rojo acento
}
```

## 📸 Screenshots

![Home con video hero](https://github.com/AlanSan1195/matera-prototipe/assets/130740412/5415a0f9-748a-412b-80d5-1da5aefb1e02)

![Menú digital](https://github.com/AlanSan1195/matera-prototipe/assets/130740412/86f27b04-05a3-4096-81ce-66290102f784)

<img width="501" alt="Vista de sección eventos" src="https://github.com/AlanSan1195/matera-prototipe/assets/130740412/df80b8a1-ce14-454e-8cc7-8095f99ed6da">

## 🔮 Posibles Mejoras Futuras

### Corto Plazo
- [ ] Migrar datos del menú a archivos JSON
- [ ] Implementar un CMS headless (Strapi, Contentful)
- [ ] Mejorar accesibilidad (ARIA labels, navegación por teclado)
- [ ] Optimizar el video hero
- [ ] Implementar lazy loading en todas las imágenes

### Mediano Plazo
- [ ] Sistema de reservas integrado (no solo WhatsApp)
- [ ] Página de administración para actualizar menú
- [ ] Integración con sistema de pedidos en línea
- [ ] Blog de recetas o noticias del restaurante
- [ ] Galería de fotos de clientes

### Largo Plazo
- [ ] Progressive Web App (PWA)
- [ ] Sistema de fidelización de clientes
- [ ] Integración con redes sociales
- [ ] Analytics avanzados

## 🤝 Contribuciones

Este proyecto fue desarrollado como freelance para un cliente real. Si encuentras bugs o tienes sugerencias, siéntete libre de abrir un issue.

## 📝 Licencia

Proyecto privado desarrollado para La Matera Restaurante.

## 🙏 Agradecimientos

- **La Matera**: Por confiar en mí para su primer proyecto web profesional
- **Comunidad de Midudev**: Por el tutorial del efecto de humo con Three.js
- **Fernando Herrera**: Por el slider adaptado en el carrusel

---

### 💭 Nota Personal

Este fue mi primer proyecto real como desarrollador freelance. Mirando atrás, veo muchas cosas que haría diferente hoy, pero también estoy orgulloso de lo que logré con los conocimientos que tenía en ese momento. Cada línea de código, cada error y cada solución fueron parte de mi aprendizaje. Este README refleja no solo el proyecto, sino también mi crecimiento como desarrollador.

**Lo más importante que aprendí**: Un código que funciona y resuelve el problema del cliente tiene valor, incluso si no es perfecto. La perfección viene con la práctica y la experiencia.

---

**Desarrollado con ❤️ por [Alan Sandoval](https://github.com/AlanSan1195)**

🌐 [lamatera.online](https://lamatera.online)
