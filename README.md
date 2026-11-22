# 🚀 Esquiva Asteroides

> **Juego arcade de HTML5 + Canvas.** Hecho por **Aether** (asistente técnico del Creador) con la orientación de su Creador, **Thomi**.

## 🎮 ¿Qué es?

Un juego de disparos y esquivado de asteroides en un solo archivo HTML. Sin dependencias externas, sin build, sin servidor. Abrís el archivo en un navegador y jugás.

## 🕹️ Cómo jugar

| Tecla | Acción |
|-------|--------|
| Flechas ⬆️⬇️⬅️➡️ | Mover la nave (con inercia y rotación) |
| Espacio | Disparar (cooldown 150 ms) |

## ⚙️ Cómo funciona

### Arquitectura

- **Un solo archivo** (`asteroids_game.html`) con HTML, CSS y JavaScript embebidos.
- **Canvas 800×600** con un loop de `requestAnimationFrame` (60 FPS).
- **Objetos**: nave, balas, asteroides (con polígono irregular generado a la vuelo), partículas de explosión.
- **Colisiones**: círculo-vs-círculo (balas vs asteroides) y distancia Euclidiana (asteroides vs nave).
- **Audio**: 3 archivos locales (`laser-shot-fx_150bpm.wav`, `lumora_studios-pixel-explosion-319166.mp3`, `freesound_community-pixel-sound-effect-4-82881.mp3`).
- **UI**: overlays absolutos para menú inicial y game over, HUD de puntuación y nivel.

### Dificultad progresiva

| Parámetro | Fórmula |
|-----------|---------|
| Nivel | `floor(elapsed / 12) + 1` (cambia cada 12 s) |
| Velocidad base | `2 + (level-1) × 0.4` px/s |
| Intervalo de spawn | `max(500, 1500 - (level-1) × 150)` ms |
| Asteroides por fila | `min(3 + floor((level-1)/2), 6)` |
| Ángulo de caída | `[-0.3, 0.3]` rad (no solo vertical) |

### Estado de la partida

```
menu → playing → gameover → (restart) → playing
```

## 📁 Estructura del repo

```
asteroids-game/
├── README.md
├── .gitignore
├── asteroids_game.html
├── laser-shot-fx_150bpm.wav
├── lumora_studios-pixel-explosion-319166.mp3
└── freesound_community-pixel-sound-effect-4-82881.mp3
```

## 🛠️ Cómo abrirlo

```bash
# Opción 1: abrir directamente
xdg-open asteroids_game.html

# Opción 2: servidor local
python3 -m http.server 8080
# → http://localhost:8080
```

## 📝 Log

- **v1.0** — Base: nave, asteroides, balas, partículas, audio, dificultad creciente, game over con reinicio.
- **v1.1** — Bucle de render corregido (un solo `gameLoop` persistente, sin doble dibujo).
- **v1.2** — Repositorio GitHub.

## 🤝 Agradecimientos

- **Aether** — código, arquitectura y documentación.
- **Thomi** — orientación, dirección creativa y la idea de que exista este repo.
- **FreeSound** — assets de audio.

## 📄 Licencia

MIT
