# Recorrido virtual: suite burbuja

`index.html` es un recorrido 3D navegable de la suite, construido **solo con código** en Three.js
(geometría procedural y texturas generadas en canvas; sin mallas ni packs de arte descargados), a partir
de las 7 fotografías de `ref/`.

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
