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
- Diseño: el gusto del usuario, registro **sereno** (skill `mi-gusto`; copia en `gusto/`, empieza por `gusto/LEEME-PRIMERO.md`). Manda sobre cualquier otra idea de estilo.
- Todo valor sale de los tokens de `:root` (tema claro y oscuro): colores, radios (`--r-*`), espaciado (`--e*`, base 4) y movimiento (`--t-*`, `--salida`, `--rebote`…). Nada suelto.
- Capas por tono, sin bordes: `--lienzo` → `--panel` (cada unidad de la ruta, la barra lateral) → `--tarjeta`. Sombras solo `--sombra-1/2`.
- Un solo acento por vista: `--tinta` (negro) en píldora para la acción principal. En el móvil esa acción es la píldora `#cta`, encima de la barra de pestañas; en escritorio, el botón "Abrir lección" del bloque "Sigue aquí". Excepciones elegidas por el usuario: el riel de rutas, el día de hoy y el contador de misiones también van en negro.
- Pasteles solo con significado, con su texto oscuro: `--cielo` = Ciber, `--durazno` = Inglés (vía `--p`/`--p-t`, que pone `body[data-track]` o `.cat-*`), `--menta` = meta del día cumplida. Nada más lleva color; sin degradados salvo la única pieza de arte (`.arte`, en Perfil).
- Tomado de la referencia 1 del gusto: saludo con dos cifras grandes arriba de la Ruta; el riel negro (`.riel`, un anillo por ruta) como selector Ciber/Inglés; en escritorio la barra lateral (marca, grupos Estudio/Consulta, cuenta al pie) va sobre un panel de vidrio con tinte (`.fondo`) y el contenido en una ventana blanca (`#app`, ahí los bloques bajan a `--hundido`) que se desplaza por dentro (usa `toTop()`, no `scrollTo`); hoy en negro en Perfil; contador negro de misiones pendientes en la pestaña.
- Letra: Geist (400/500/600) y Geist Mono para comandos y etiquetas técnicas. Iconos de trazo de un solo juego. Sin emojis, sin confeti.
- Antes de dar por bueno un cambio visual: `gusto/herramientas/medir.js` a 360, 375, 430, 1024 y 1440 px. En escritorio el aviso de márgenes desiguales es esperado (barra lateral fija).
- Guardado: en local usa `localStorage`. Publicada como artifact de claude.ai usa la capacidad `db` (`window.claude.use('db')`) y sincroniza entre dispositivos.

## Versión en GitHub Pages (con cuenta)
- Repo: github.com/benamy3311-art/ruta-analista (rama `main`, Pages desde la raíz). Sitio: https://benamy3311-art.github.io/ruta-analista/. Publicar = `git push`; tarda ~1 min.
- Login con Google y guardado en Firestore (proyecto Firebase `ruta-analista-19495`, plan Spark): el bloque `<script type="module">` al final de `index.html`. Solo corre en http(s) y si NO existe `window.claude` (en el artifact se usa `db`).
- Datos en `users/{uid}`; reglas: cada usuario solo lee y escribe su documento. Dominios autorizados en Authentication: localhost, *.firebaseapp.com, *.web.app y benamy3311-art.github.io. Si cambia el dominio, agrégalo ahí o el login falla.
- La config web de Firebase (apiKey incluida) es pública por diseño; no es un secreto.

## Publicar cambios
La versión en línea es el artifact "Ruta Analista" en claude.ai. Para actualizarlo, pide a Claude que lo republique desde este archivo (mismo artifact, capacidades `db` y `user`).
