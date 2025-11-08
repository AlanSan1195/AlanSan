# 🧱 Arkanoid Game

<div align="center">
  <img src="./sprite.png" alt="Arkanoid Game" width="400px"/>
</div>

## 🎮 Descripción

Una recreación del clásico juego arcade **Arkanoid** construida completamente con JavaScript vanilla y HTML5 Canvas. Este juego de rompe-bloques te desafía a destruir todos los bloques mientras mantienes la pelota en juego con tu paleta. ¡Un verdadero homenaje a los juegos arcade de los 80s!

## ✨ Características

- 🎯 **13 bloques desafiantes** - Diferentes tipos de bloques para romper
- 🏓 **Física de pelota realista** - Colisiones precisas y rebotes dinámicos
- 🎮 **Controles suaves** - Control fluido de la paleta con teclado
- 💥 **Sistema de colisiones** - Detección precisa entre pelota, paleta y bloques
- ❤️ **Sistema de vidas** - Gestiona tus 3 vidas cuidadosamente
- 🎨 **Gráficos retro** - Sprites pixel art auténticos al estilo arcade
- 🔊 **Efectos visuales** - Bordes decorativos y background temático

## 🕹️ Cómo Jugar

### Controles

- **←** Flecha Izquierda - Mover paleta a la izquierda
- **→** Flecha Derecha - Mover paleta a la derecha
- **Espacio** - Pausar/Reanudar (si está implementado)

### Objetivo

1. Mueve la paleta para mantener la pelota en juego
2. Rompe todos los bloques rebotando la pelota contra ellos
3. Evita que la pelota caiga por debajo de la paleta
4. ¡Completa el nivel rompiendo los 13 bloques!

### Reglas

- Comienzas con **3 vidas**
- Pierdes una vida cada vez que la pelota cae
- El juego termina cuando pierdes todas tus vidas
- Los bloques se destruyen al ser golpeados por la pelota

## 🛠️ Tecnologías Utilizadas

- **HTML5** - Estructura del juego
- **CSS3** - Estilos y efectos visuales
- **JavaScript (ES6)** - Lógica del juego
- **Canvas API** - Renderizado de gráficos 2D
- **Sprites** - Imágenes para elementos del juego

## 📂 Estructura del Proyecto

```
01-arkanoid-Game/
├── index.html          # Archivo principal del juego
├── sprite.png          # Sprites de paleta y pelota
├── bricks.png          # Sprites de los bloques
├── borde.png           # Imagen del borde decorativo
└── bkg.png             # Fondo del juego
```

## 🚀 Instalación y Ejecución

### Opción 1: Abrir directamente
1. Descarga o clona el repositorio
2. Abre el archivo `index.html` en tu navegador web

### Opción 2: Con servidor local
```bash
# Si tienes Python 3 instalado
python -m http.server 8000

# O con Node.js y npx
npx serve

# Luego abre http://localhost:8000 en tu navegador
```

### Opción 3: Demo en línea
🎮 **[Jugar en línea](https://arkanoidsan.netlify.app/)**

## 💡 Conceptos Aprendidos

Este proyecto me permitió practicar y dominar:

- ✅ **Canvas API** - Dibujo y renderizado 2D
- ✅ **Game Loop** - Ciclo de actualización y renderizado
- ✅ **Detección de colisiones** - Algoritmos de intersección de rectángulos y círculos
- ✅ **Física básica** - Velocidad, dirección y rebotes
- ✅ **Event Listeners** - Captura de entrada del usuario
- ✅ **Sprites y Assets** - Manejo de imágenes en juegos
- ✅ **Coordenadas 2D** - Sistema de posicionamiento en canvas

## 🎯 Desafíos Técnicos

### 1. Detección de Colisiones
Implementar la detección precisa de colisiones entre:
- Pelota circular vs. paleta rectangular
- Pelota vs. bloques rectangulares
- Cálculo de ángulos de rebote

### 2. Física del Juego
- Velocidad constante de la pelota
- Dirección de rebote basada en el punto de impacto
- Movimiento fluido de la paleta

### 3. Renderizado Eficiente
- Limpiar y redibujar el canvas en cada frame
- Optimizar el game loop con `requestAnimationFrame`
- Manejo eficiente de sprites

## 🔮 Mejoras Futuras

- [ ] Sistema de puntuación
- [ ] Múltiples niveles con diferentes diseños
- [ ] Power-ups (pelota más grande, paleta más ancha, etc.)
- [ ] Efectos de sonido y música
- [ ] Tabla de clasificación con LocalStorage
- [ ] Diferentes tipos de bloques con propiedades especiales
- [ ] Modo multijugador

## 👨‍💻 Autor

**Alan Sandoval**

- GitHub: [@AlanSan1195](https://github.com/AlanSan1195)
- Proyecto inspirado en los tutoriales de [Midudev](https://midu.dev)

## 📝 Licencia

Este proyecto es de código abierto y está disponible para fines educativos.

## 🙏 Agradecimientos

- **Midudev** - Por los excelentes tutoriales de JavaScript
- **Taito Corporation** - Creadores del Arkanoid original (1986)
- La comunidad de desarrolladores JavaScript

---

<div align="center">
  <p>⭐ Si te gustó este proyecto, ¡dale una estrella en GitHub! ⭐</p>
  <p>🎮 <a href="https://arkanoidsan.netlify.app/">Jugar Ahora</a> | 📂 <a href="../">Ver Más Proyectos</a></p>
</div>
