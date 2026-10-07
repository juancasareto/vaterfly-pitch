# Vaterfly · repo del deck y del visor 3D

Lo trabajan Juan y Bruno (producción). Responder en castellano rioplatense.
Este repo es **público** y se publica solo con GitHub Pages en `deck.vaterfly.com`.

## Qué hay

| Ruta | Qué es | URL |
|---|---|---|
| `index.html` + `assets/` | Pitch deck (ver README.md) | https://deck.vaterfly.com |
| `rendertest/index.html` | **Visor 3D técnico** del escenario: planta, escenas del guion, luces y mecanismos | https://deck.vaterfly.com/rendertest/ |

Las dos páginas tienen una barrera de contraseña **cosmética** (está en el código, el repo es público).

## Fuentes de verdad

- **Mecanismos:** Notion › VATERFLY › *Mecanismos y estructuras*. Una subpágina por mecanismo, la completa Bruno
  (ficha, descripción, funcionamiento, ubicación, especificaciones). Cuando cambia, se pasa al visor.
- **Guion:** el visor usa las 18 escenas del guion del 31/08 más la Presentación (escena 01, agregada por producción): 19 en total. El texto nuevo de Mariano (8 escenas) está en Notion /
  carpeta privada de Juan; pasar el visor a esas 8 escenas está pendiente.
- **Planta:** las decisiones de planta las da Juan (ver "Planta actual").

## Cómo está hecho el visor (`rendertest/index.html`)

Un solo HTML con Three.js 0.180 desde jsDelivr (importmap). Sin build.

- **Coordenadas en metros:** `x` = largo de la sala (0 = pared del fondo / backstage → 20 = pared de los accesos),
  `z` = ancho (0 → 13), `y` = alto. Todo vive dentro de `root`, que está **espejado en z** para que la vista
  isométrica coincida con el plano original: para cámaras usar `R(x, y, z)`.
- **Constantes de planta** (arriba del script): `W D H`, `SX` (fondo del backstage), `STAGE`, `SXE` (frente del escenario),
  `TELA` (área útil de la pantalla), `TEL` (marco Pelea telón), `PROJ` (proyector), `TOR` (techo/tornado y tubo),
  `CAB` (Esfera / Cabeza). Cambiar medidas acá, no números sueltos.
- **Estructura fija:** cada elemento se crea con `makeEl(id, info)`; `info` es la ficha que aparece al tocarlo.
- **Escenas:** array `SCENES` (texto del guion, `esp`, `tec`, `pend`, `build()`), y su luz en `LOOKS[n]`.
- **Mecanismos:** array `MECS` (pestaña Mecanismos). Cada uno tiene ficha con el texto de Notion, `st`/`range`
  (control deslizante), `build()` y `notes` (choques detectados). Los mecanismos del motor central y la cabeza
  se arman con `buildToroide`, `buildCajon`, `buildCabeza`, que también usan las escenas.
- **Luces:** `fixture(type, pos, rig, grupo)` + `applyLook(look)`. Rider en `showRider()`.
- **Personajes:** se están pasando de cápsula (`figure()`) a humano articulado (`humano()`, con `vestir()` y `posar()`). Todo personaje nuevo se crea con
  `humano(nombre, [x, y, z], { h, face, ropa })`: **nombre** + **referencia de vestuario** (la imagen que pasa
  producción) traducida a un objeto de ropa como `ROPA_70` (piel, pelo, remera, short, medias, zapatillas, accesorios).
  Altura sin dato = supuesto, marcado en la ficha. El movimiento va con acciones (`ACC`: poses clave alrededor de un
  contacto) y física real donde se nota (saltos y pelota con g = 9,81). Ejemplo: voleibolistas del Warm up (`pepper`).
  La foto de referencia **no** se sube al repo: el vestuario se modela en código.
- **Convención visual:** blanco = según plano / definido por producción · naranja = activo en la escena ·
  **violeta punteado = propuesta, a validar**. Los supuestos van en "Pendiente de definir" de cada ficha.

## Planta actual (resumen)

Sala 20 × 13 m, carpa a 15 m (supuesto). Backstage de 4 m. Escenario de 10 × 2,3 m con pasillos de 1,5 m a los lados.
Pantalla = Pelea telón, marco Layher 6 × 6 m (retroproyección desde el backstage). Torres A y B de 6 m enfrentadas
(x 11–13,6). Torre C de 3 m con truss de músicos. 2 accesos de público junto a la torre C. Techo con tela en tornado
(plano a 12 m), parrilla y tubo central Ø 2,5 m con el motor central (Agujero negro, Cajón, Toroide).
Trusses de luces laterales a 10 m (el del escenario se sacó).

## Cómo trabajar

1. **Antes de tocar nada: `git pull`.** Una sola persona edita el visor por vez (es un único archivo).
2. Probar local: `python3 -m http.server 8767` desde la raíz del repo y abrir `http://localhost:8767/rendertest/`.
   Revisar la consola: tiene que estar sin errores.
3. Chequeo rápido de sintaxis del script: extraer el `<script type="module">` y correr `node --check`.
4. Publicar: commit con mensaje claro en castellano + `git push`. GitHub Pages tarda 1–2 minutos;
   el navegador puede tener la versión anterior hasta 10 minutos (recargar con Cmd + Shift + R).
5. Al contar qué se hizo: separar lo que viene de Notion / de Juan de lo que es supuesto, y listar los choques nuevos.

## No hacer

- No subir fotos de vestuario, bocetos ni documentos internos: el repo es público.
- No editar el visor a la vez desde dos computadoras.
- No inventar medidas sin marcarlas como supuesto.
