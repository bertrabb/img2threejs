# Recorrido virtual: suite burbuja

`index.html` es un recorrido 3D navegable de la suite, construido **solo con código** en Three.js
(geometría procedural y texturas generadas en canvas; sin mallas ni packs de arte descargados), a partir
de las 7 fotografías de `ref/`.

## Modo render (v2)
- Trazado de rayos progresivo en el navegador (`three-gpu-pathtracer` 0.0.28 sobre Three.js 0.187): en cuanto la
  cámara se detiene, la imagen se refina con luz rebotada, sombras suaves y reflejos, como un render de arquitectura.
  Mientras la cámara se mueve se ve la vista rápida. El botón "Render" lo activa o desactiva.
- Cielo como mapa de entorno (día con nubes / noche con estrellas), que es la fuente de luz ambiental.
- Estatua y bustos esculpidos con campos de distancia (superficies continuas), colcha con caída y pliegues,
  hojas con nervios, tejidos con brillo de tela (sheen), olivos con copas orgánicas.
- Verificado en Chromium con WebGL por software (`evidence/renders-v2/`): unas 30-40 pasadas en 25 min, por eso
  las capturas tienen grano. En un equipo con tarjeta gráfica la imagen converge en segundos; no se ha medido
  en móviles reales.

## Qué incluye
- Cúpula geodésica 5V (banda de OSB opaca + paneles transparentes) con sombras de la estructura en el suelo.
- Tabique de mármol con split, fuente de león con laurel, jacuzzi revestido, repisa con estatua, copa y urna.
- Cama con colcha damasco, cojines oliva, albornoces, dosel de gasa dorada, columnas con bustos, arcón y silla de tijera.
- Rincón de mesa (mantel, sillas doradas tapizadas en salvia, consola barroca, lámpara de araña), puerta de entrada y estufa de pellets.
- Baño: lavabo dorado sobre columnas estriadas, espejo redondo, apliques y mampara.
- 7 paradas guiadas, puntos de interés clicables, recorrido automático y modo día/noche.
- Enlace de reserva configurable (`BOOKING_URL` dentro del script; si está vacío, el botón queda oculto).

## Estado de validación (honesto)
- La rúbrica de la skill (`grimoire/intake/validation_rubric.md`) **rechaza escenas** ("photo is a scene, not an
  object reference"). El recorrido se hizo a petición expresa como **recreación estilizada y aproximada**;
  medidas y distribución están estimadas a partir de las fotos.
- Admisión de referencias: 6 de 7 pasan (`evidence/admission-*.json`); IMG_0791 sale fragmentada.
- Capturas reales en navegador (Chromium/Playwright, WebGL por software): `evidence/renders/`.
- Hojas comparativas referencia/render: `evidence/cmp/sheet-*.png`.
- `diagnose_render.py` (Tier 1): **no pasa** en ninguna vista (`evidence/cmp/diagnose-*.json`). Sus métricas de
  silueta y encuadre están pensadas para un objeto aislado con cámara ajustada, no para un interior
  fotografiado con gran angular. **La puerta visual de la skill no se ha superado** y no se reclama.
- No se escribió sculpt spec, generador de factory ni las puertas de pases/turntable: la escena se escribió a mano.

## Limitaciones visibles
Estatua y bustos estilizados (no son retratos de las piezas reales), cúpula con menos triángulos que la real,
texturas procedurales en lugar de fotoproyección, entorno exterior genérico (olivos simplificados).
