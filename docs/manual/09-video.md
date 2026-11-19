# 09. Vídeo

Qué sale por el HDMI, qué opciones tiene y qué VDP lleva.

## 1. La salida

Una sola señal: **HDMI 1280×720 a 60 Hz**, con el audio embebido. Cualquier televisor o monitor con HDMI la acepta; los capturadores también.

La imagen del MSX ocupa la pantalla entera. Cada punto del MSX son 4 píxeles de ancho y cada línea 3 de alto, sin fracciones, así que los píxeles salen todos iguales y sin escalones. Se ve el **borde** a los cuatro lados, como en un monitor de tubo: 32 puntos a cada lado del área de 256, que es donde los juegos con scroll esconden y sacan cosas.

No hay modo 4:3 con marco negro ni ajustes de posición: se probaron y se retiraron en favor de un único modo a pantalla completa, el mismo criterio que el MSXnano.

**Scanlines**: en Ajustes, *Enable Scanlines* oscurece al 50 % una de cada tres líneas, el aspecto de un monitor de la época. Se cambia y se guarda desde el menú, sin reiniciar el core.

**50 Hz**: la salida es siempre 720p60. El software que pone el VDP en 50 Hz funciona, con la imagen convertida a 60; es el modo menos probado y su geometría no está medida, así que si algún juego europeo se ve raro en 50 Hz, es lo primero que mirar.

## 2. El panel F12

Con el firmware del BL616 grabado ([capítulo 02](02-instalacion.md)), **F12** congela el MSX y dibuja encima un panel en color con lo que el core dice de sí mismo: versión, Z80 y turbo, vídeo, tarjeta, los ajustes principales (scanlines, estéreo, segundo SCC), qué hay en cada USB-A, ventilador, bloqueo de mayúsculas y la orden para actualizar. Sale en el idioma del menú. F12 otra vez, o ESC, y el juego sigue donde estaba. Es de solo lectura.

Desde la v3.8 el panel lleva color (cada fila con sus combinaciones de fondo y tinta) y dibujos propios: marcos, iconos y letras con tilde. Un firmware del BL616 anterior se sigue viendo como antes, en amarillo y blanco sobre negro.

Porque F12 es del panel, el **turbo va en F11**.

## 3. El VDP

El VDP es un **V9958**, el del linaje OCM / ESE (`fpga/tn_vdp_v3_v9958`). Es el VDP de un MSX2+ normal: el software de siempre funciona igual, y los programas de diagnóstico lo ven como V9958. Su VRAM, de 128 KB, está en la SDRAM del dock, y la imagen sale por el puente HDMI de 720p.

## 4. Lo que no hay

- Salida analógica de ningún tipo: ni compuesto, ni RGB, ni VGA.
- Modo 4:3 con marco.
- Un V9990: es un plan, no una función.
