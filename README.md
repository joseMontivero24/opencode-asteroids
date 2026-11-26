# Asteroids

Clon del clásico arcade **Asteroids** implementado en canvas HTML5 puro, sin dependencias ni bundler.

## Descripción

Nave espacial en un campo de asteroides con envolvimiento de bordes (el espacio es toroidal). Destruye asteroides para sumar puntos: los grandes se parten en medianos, los medianos en pequeños. Incluye el power-up **Velocidad**.

## Tecnologías

- **HTML5 Canvas** — renderizado 2D
- **JavaScript (ES6+)** — lógica del juego en un solo archivo `game.js`
- Sin frameworks, sin bundler, sin dependencias

## Cómo correr

Abre `index.html` directamente en el navegador (doble clic), o usa un servidor local:

```bash
npx serve .
```

Luego visita `http://localhost:3000`.

## Controles

| Tecla     | Acción     |
| --------- | ---------- |
| `←` `→`   | Rotar nave |
| `↑`       | Propulsar  |
| `Espacio` | Disparar   |

## Power-up: Velocidad

- Cada asteroide destruido tiene un **20 % de probabilidad** de dejar un círculo celeste con una **V**.
- Recógelo con la nave antes de que desaparezca a los **10 segundos**.
- Duplica la velocidad de desplazamiento durante **5 segundos de juego**, sin modificar la rotación ni los disparos.
- El indicador `VELOCIDAD ×2` muestra el tiempo restante. Recoger otro reinicia la duración a 5 segundos, sin acumular multiplicadores.
- Cambiar de nivel conserva el tiempo restante y los objetos sin recoger; perder una vida o reiniciar la partida cancela el efecto.

## Puntuación

| Asteroide | Puntos |
| --------- | ------ |
| Grande    | 20     |
| Mediano   | 50     |
| Pequeño   | 100    |

## Características

- 3 vidas con invencibilidad temporal al reaparecer (parpadeo)
- Asteroides se parten en fragmentos más pequeños al ser destruidos
- Partículas de explosión al destruir asteroides
