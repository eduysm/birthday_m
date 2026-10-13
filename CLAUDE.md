# Web de cumpleaños de Muskaan (25 años)

Regalo interactivo para móvil y PC, publicado con GitHub Pages desde `git@github.com:eduysm/birthday_m.git` (rama `main`, repo público).

## Estructura
- `index.html`: todo el código (HTML + CSS + JS vanilla, sin librerías). Fuentes de Google: Baloo 2, Luckiest Guy, Caveat.
- `fotos/`: `foto1.jpeg`, `foto2.jpeg`, `foto3.mp4`, `foto4.jpeg` → tarjetas del rasca (nivel 2).
- `fotos/dump/`: `dump1..5.jpeg` → foto dump (nivel 1). Convención de nombres sin espacios.
- `memes/`: `meme1..8` (jpeg, mp4, gif) → meme wall (nivel 3).
- `musica/`: `musica1.mp3` (pantalla de entrada), `musica2.mp3` (resto). Los `.mpeg` originales se ignoran en git.

## Configuración (bloque `CONFIGURACIÓN` en el `<script>`)
`ENLACE_SPA`, `MENSAJE_FINAL`, `FOTO_DUMP`, `TARJETAS_RASCA`, `MEMES`, `PALABRAS_COMIC`. Los contadores y textos "x/N" son dinámicos según la longitud de estos arrays.

## Flujo
Entrada (música) → mapa de niveles → 1 Foto dump (polaroids apiladas) → 2 Rasca y gana → 3 Meme wall → 4 Final boss (botón "Regalo" que esquiva 3 veces y a la 4.ª abre el enlace del spa).

## Pendiente
- `ENLACE_SPA` real y `MENSAJE_FINAL` personalizado.
- Mensajes definitivos del foto dump (los actuales son provisionales).
- Probar en navegador y móvil reales; nunca se ha verificado visualmente.
- `musica2.mp3` pesa ~8,3 MB; riesgo de copyright al ser repo público.

## Notas técnicas
- Los medios se cargan con `cargarMedio(ruta, alCargar, alFallar)`: mp4/webm/mov → `<video muted loop autoplay playsinline>`, resto → `Image`.
- Foto dump y rasca adaptan su tamaño a la proporción real de cada foto/vídeo (para que no se corten).
- El botón regalo se reparenta a `body` con `position:fixed` (evita el bug del `backdrop-filter` de `.tarjeta`).
- Verificar sintaxis tras editar: extraer el `<script>` y ejecutar `new Function(script)` con node.
- Editar `index.html` con sustituciones exactas; es un archivo grande.
- No hacer commit/push salvo que se pida, y añadir archivos concretos (evitar `git add -A`: hay archivos sueltos de WhatsApp en la raíz).
