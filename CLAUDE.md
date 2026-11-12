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

## Versión en GitHub Pages (con cuenta)
- Repo: github.com/benamy3311-art/ruta-analista (rama `main`, Pages desde la raíz). Sitio: https://benamy3311-art.github.io/ruta-analista/. Publicar = `git push`; tarda ~1 min.
- Login con Google y guardado en Firestore (proyecto Firebase `ruta-analista-19495`, plan Spark): el bloque `<script type="module">` al final de `index.html`. Solo corre en http(s) y si NO existe `window.claude` (en el artifact se usa `db`).
- Datos en `users/{uid}`; reglas: cada usuario solo lee y escribe su documento. Dominios autorizados en Authentication: localhost, *.firebaseapp.com, *.web.app y benamy3311-art.github.io. Si cambia el dominio, agrégalo ahí o el login falla.
- La config web de Firebase (apiKey incluida) es pública por diseño; no es un secreto.

## Publicar cambios
La versión en línea es el artifact "Ruta Analista" en claude.ai. Para actualizarlo, pide a Claude que lo republique desde este archivo (mismo artifact, capacidades `db` y `user`).
