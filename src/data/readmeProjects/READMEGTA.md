# GTA VI Landing Page — Efecto Scroll al estilo Rockstar Games 🎮

Este proyecto es una landing page inspirada en el sitio oficial de **GTA VI** de Rockstar Games, replicando el icónico efecto de scroll animado que caracteriza a la web original. Utilizamos [GSAP (GreenSock Animation Platform)](https://gsap.com/) y su plugin **ScrollTrigger** para crear animaciones fluidas y profesionales sincronizadas con el scroll del usuario.

## 🚀 Tecnologías utilizadas

- **[Astro 5.9.2](https://astro.build/)** — Framework moderno para construir sitios web rápidos.
- **[TailwindCSS 4.1.10](https://tailwindcss.com/)** — Framework de CSS utility-first para estilos personalizados.
- **[GSAP 3.13.0](https://gsap.com/)** — Biblioteca de animación JavaScript de nivel profesional.

## 🎬 Efectos implementados

### 1. **Efecto de máscara con logo (Mask Effect)**
Utilizamos CSS `mask-image` combinado con animaciones GSAP para crear el efecto distintivo donde el logo de GTA VI actúa como una ventana que revela el contenido:

```css
#logo-stack {
  background-color: white;
  mask-image: url("/logo-stack.svg");
  mask-position: center 20%;
  mask-repeat: no-repeat;
  mask-size: clamp(5200vh, 3500%, 0vh);
}
```

### 2. **Animaciones secuenciales al hacer scroll**
El scroll controla una secuencia fluida de animaciones que incluyen:
- Zoom del hero key
- Desvanecimiento del logo y botón de play
- Transición del tamaño de la máscara
- Aparición del footer con efecto clip-path
- Animación de escala y opacidad coordinada

## 📚 Lo que aprendimos de GSAP

### 1. **Importación y registro de plugins**

Para usar funcionalidades avanzadas como las animaciones controladas por scroll, es necesario importar y registrar los plugins:

```js
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);
```

El método `registerPlugin()` activa el plugin ScrollTrigger, permitiéndonos vincular animaciones al scroll de la página.

**📖 Referencia:** [gsap.registerPlugin()](https://gsap.com/docs/v3/GSAP/gsap.registerPlugin/)

---

### 2. **Timeline: Secuenciación de animaciones**

Creamos una línea de tiempo (`timeline`) para encadenar múltiples animaciones y controlarlas de forma cohesiva:

```js
const tl = gsap.timeline({
  ease: "power2.out",
  scrollTrigger: {
    scrub: 1,
  },
});
```

**Propiedades clave:**
- **`ease`**: Define la curva de aceleración de las animaciones (en este caso `power2.out`).
- **`scrollTrigger.scrub`**: Sincroniza las animaciones con el scroll. Un valor de `1` añade suavizado.

**📖 Referencias:**
- [Timeline](https://gsap.com/docs/v3/GSAP/Timeline/)
- [Easing en GSAP](https://gsap.com/docs/v3/Eases)
- [ScrollTrigger scrub](https://gsap.com/docs/v3/Plugins/ScrollTrigger/)

---

### 3. **gsap.set(): Estado inicial**

Antes de animar, establecemos el estado inicial de elementos con `gsap.set()`:

```js
gsap.set("#footer", {
  opacity: 0,
  clipPath: "ellipse(60% 0% at 50% 190%)",
});
```

Esto configura el footer invisible y con una forma elíptica colapsada, listo para animarse.

**📖 Referencia:** [gsap.set()](https://gsap.com/docs/v3/GSAP/gsap.set())

---

### 4. **Posicionamiento relativo en Timeline: `"<"` y `">"`**

GSAP permite controlar cuándo inicia cada animación dentro de la timeline usando parámetros de posición:

#### **`"<"` — Inicio simultáneo**
Inicia la animación al mismo tiempo que la anterior:

```js
tl.to("#hero-key", { duration: 1, scale: 1 })
  .to("#hero-key-logo", { opacity: 0 }, "<")
  .to("#hero-play-button", { opacity: 0 }, "<")
  .to("#hero-footer", { opacity: 0 }, "<")
```

Aquí, todas las animaciones de opacidad comienzan al mismo tiempo que la animación de escala del hero key.

#### **`">"` — Después de la anterior**
Inicia la animación después de que termine la anterior:

```js
.to("#footer", {
  clipPath: "ellipse(60% 100% at 50% 50%)",
  opacity: 1,
  duration: 1.5,
}, ">0.2")
```

El `">0.2"` significa que esta animación inicia 0.2 segundos después de que termine la animación anterior.

#### **Otros parámetros útiles:**
- **`"-=1"`**: Inicia 1 segundo antes de que termine la anterior (solapamiento).
- **`"+=0.5"`**: Inicia 0.5 segundos después de que termine la anterior (gap).

**📖 Referencia:** [Position Parameter en Timeline](https://gsap.com/docs/v3/GSAP/Timeline/#position-parameter)

---

### 5. **Propiedades animables**

En este proyecto animamos varias propiedades CSS:

```js
tl.to("#logo-stack", { 
  maskSize: "clamp(20vh, 29%, 30vh)", 
  duration: 1 
}, "<")
```

**Propiedades utilizadas:**
- **`scale`**: Escala de transformación del elemento.
- **`opacity`**: Transparencia del elemento (0 a 1).
- **`maskSize`**: Tamaño de la máscara CSS.
- **`clipPath`**: Define la forma visible del elemento.
- **`duration`**: Duración de la animación en segundos.

**📖 Referencias:**
- [Propiedades animables en GSAP](https://gsap.com/docs/v3/GSAP/CorePlugins/)
- [CSS Properties en GSAP](https://gsap.com/docs/v3/GSAP/CorePlugins/CSSPlugin/)

---

### 6. **ScrollTrigger con scrub**

El `scrub` es la característica más importante para crear animaciones vinculadas al scroll:

```js
scrollTrigger: {
  scrub: 1,
}
```

**¿Qué hace `scrub`?**
- Con `scrub: true`: Las animaciones se vinculan directamente al scroll (sin suavizado).
- Con `scrub: 1`: Añade 1 segundo de suavizado para transiciones más fluidas.

Esto crea el efecto característico de Rockstar Games donde el usuario controla la animación con el scroll.

**📖 Referencia:** [ScrollTrigger scrub](https://gsap.com/docs/v3/Plugins/ScrollTrigger/#scrub)

---

### 7. **Easing functions**

Utilizamos diferentes funciones de easing para controlar la aceleración de las animaciones:

```js
.to("#footer", {
  ease: "power4.out",
  scale: 0.8,
  duration: 1.5,
})
```

**Easing utilizados en el proyecto:**
- **`power2.out`**: Desaceleración suave al final.
- **`power4.out`**: Desaceleración más pronunciada.
- **`power2.inOut`**: Aceleración al inicio y desaceleración al final.

**📖 Referencia:** [GSAP Ease Visualizer](https://gsap.com/docs/v3/Eases)

---

### 8. **clipPath para efectos de revelado**

Usamos `clipPath` para crear efectos de revelado tipo cortina elíptica:

```js
.to("#footer", {
  clipPath: "ellipse(60% 100% at 50% 50%)",
  opacity: 1,
}, ">0.2")
.to("#footer", {
  clipPath: "ellipse(60% 100% at 50% -100%)",
}, ">")
```

Esto crea una transición donde el footer aparece con forma elíptica desde abajo y luego se desvanece hacia arriba.

**📖 Referencia:** [clipPath en MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/clip-path)

---

## 🎨 Características adicionales

### Fuentes personalizadas
Implementamos las fuentes oficiales de GTA:
- **GTA Regular** (normal)
- **GTA Semibold** (600)
- **GTA Bold** (negrita)
- **GTA Narrow** (condensada)

### Gradiente de texto personalizado
Creamos un gradiente radial para el texto del footer:

```css
.text-gradient {
  background-image: radial-gradient(
    circle at 50% 40vh, 
    #ffd27b 0, 
    #df3a93 60vh, 
    #5c1663 100vh
  );
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
```

### Animación personalizada con Tailwind
Implementamos una animación de bounce personalizada para el indicador de scroll:

```css
@keyframes bounce-pulse {
  0% { transform: translateY(0); scale: 0.8; opacity: 0.8; }
  50% { transform: translateY(-5px); scale: 1; }
  100% { transform: translateY(0); scale: 0.8; opacity: 0.8; }
}
```

---

## 📦 Instalación y uso

```bash
# Instalar dependencias
pnpm install

# Iniciar servidor de desarrollo
pnpm dev

# Construir para producción
pnpm build

# Vista previa de la build
pnpm preview
```

---

## 🔗 Recursos útiles de GSAP

- [Documentación oficial de GSAP](https://gsap.com/docs/)
- [ScrollTrigger Demos](https://gsap.com/docs/v3/Plugins/ScrollTrigger/demos)
- [GSAP Cheat Sheet](https://gsap.com/resources/get-started/)
- [Forum de GSAP](https://gsap.com/community/)
- [CodePen Collection de ScrollTrigger](https://codepen.io/collection/nVYWZR)

---

## 👨‍💻 Autor

Desarrollado con 💚 por [Alan San](https://alansan.pro) - 2025

[![GitHub](https://img.shields.io/badge/GitHub-AlanSan1195-181717?logo=github)](https://github.com/AlanSan1195)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-devsan11-0A66C2?logo=linkedin)](https://www.linkedin.com/in/devsan11/)

---

**Nota:** Este proyecto es solo con fines educativos y de aprendizaje. No tiene relación oficial con Rockstar Games ni Take-Two Interactive.
