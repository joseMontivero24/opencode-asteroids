# Guía del repositorio

## Ejecución y verificación
- Abre `index.html` directamente en el navegador; no requiere instalación ni compilación.
- No hay `package.json`, dependencias, tests automatizados ni configuración de lint o typecheck. No supongas que existen comandos `npm run`.
- Si Node.js está disponible, `node --check game.js` comprueba la sintaxis, no el funcionamiento del juego.
- Verifica los cambios de jugabilidad en el navegador: flechas para rotar/propulsar, Espacio para disparar; comprueba fragmentación y puntuación, cambio de nivel, pérdida de vidas, reaparición y reinicio con Espacio tras «GAME OVER».

## Acoplamientos importantes
- `index.html` carga `game.js` como script clásico después de crear `#canvas`. El script accede al DOM y arranca inmediatamente con `initGame()` y `requestAnimationFrame(loop)`; no es un módulo importable en Node.js.
- El tamaño del canvas en `index.html` y las constantes `W`/`H` de `game.js` están duplicados (800 × 600). Si cambias las dimensiones, actualiza ambos.
- `loop()` entrega `dt` en segundos, limitado a 0.05; las actualizaciones y los temporizadores usan esa unidad.
- `keys` representa teclas mantenidas; `pressed(code)` consume `justPressed`. El disparo y el reinicio usan este último mecanismo, no lectura continua de `keys`.
- Los estados son `playing`, `dead` y `gameover`: `initGame()` reinicia toda la partida; `Ship.reset()` reinicia la nave y concede invencibilidad; `nextLevel()` conserva puntuación, vidas, power-ups sin recoger y el tiempo de Velocidad mediante `preserveSpeedBoost`.
- Los tamaños de asteroide son 1 = pequeño, 2 = mediano, 3 = grande; `RADII`, `SPEEDS` y `POINTS` usan esos índices.
- Velocidad multiplica el desplazamiento, no `vx`/`vy`: evita acumular velocidad permanente. Una nueva recolección reinicia el temporizador a 5 segundos; morir lo cancela. Sus constantes y `SpeedPowerUp` están antes de `Ship`.
