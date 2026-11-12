# Ruta Analista

App de estudio tipo Duolingo (ciberseguridad + inglés). Todo vive en `index.html`: HTML, CSS y JS sin dependencias ni build. Para verla, abre `index.html` en el navegador.

## Dónde está cada cosa (dentro de `<script>`)
- `TRACKS`: rutas `cyber` y `eng` → unidades → lecciones → tareas. Tarea = `[html, tipo]`, tipo: `g` modo juego, `t` prueba, `o` opcional.
- `EASY`: explicación simple de cada unidad (botón i).
- `DAILY` / `WEEKLY`: misiones diarias y semanales.
- `LIB`: Biblioteca. `DICT` + `DCATS`: Diccionario.
- `DEFAULT`, `reconcile()`, `gainXP()`: estado, racha, protectores y XP.
- `render*()`: una función por pestaña.

## Reglas
- Los ids de lección/tarea salen de su posición (`cyber-1-0-2`). Insertar o reordenar tareas cambia ids y desmarca progreso guardado; agrega al final cuando se pueda.
- Colores solo con las variables de `:root` (tema claro y oscuro).
- Formas inspiradas en plush-ui (plush-ui.pages.dev): superficies sin bordes con `--shadow-soft`, píldoras, y pulsar = `scale` con `--ease-spring`.
- Paleta de solo tres colores y sus tintes: crema (fondos), azul noche (`--accent`, texto, Ciber) y rojo (`--sel-fill`: progreso, lo hecho o elegido, Inglés). No agregar verdes, dorados ni otros tonos.
- Guardado: en local usa `localStorage`. Publicada como artifact de claude.ai usa la capacidad `db` (`window.claude.use('db')`) y sincroniza entre dispositivos.

## Publicar cambios
La versión en línea es el artifact "Ruta Analista" en claude.ai. Para actualizarlo, pide a Claude que lo republique desde este archivo (mismo artifact, capacidades `db` y `user`).
