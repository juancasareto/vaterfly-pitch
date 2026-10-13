# Novedades del visor

Mensajes para quien trabaja en el repo. El más nuevo va arriba.
Después de cada `git pull`, Claude (y la terminal, si el aviso está activado) muestra lo nuevo.

---

## 12/10/2026 · de Juan para Bruno

Hola Bruno, estos son los cambios de hoy en el visor (ya publicados en deck.vaterfly.com/rendertest):

- **Calidad alta (HQ) en el visor principal:** torres, trusses, techo y marco de la pantalla ahora son caños de
  aluminio; piso, escenario, tarima, carpa y puertas tienen textura; hay reflectores reales con sombras.
  El botón **Vista técnica** vuelve a las líneas. La página `/rendertest-hq` se borró.
- **Capa Público** (casillero en la barra, aforo ≈ 120 / 280 / 450): gente que mira al escenario, esquiva la
  estructura y se abre cuando pasa la tarima.
- **Coreografía del público por escena:**
  - **Intro:** 4 técnicos de piso abren un círculo de Ø ≈ 7,2 m bajo el Toroide; el público queda concentrado,
    quieto, mirando.
  - **Monja:** la gente se abre al pasar la tarima y despeja la zona del revoleo (llega a ≈ 5,2 m de radio:
    hay que confirmarlo con el rigger).
  - **MOSH:** filas para el mosh y el tobogán, juegan al limbo, se agachan cuando pasan las performers aéreas,
    rodean la acción y filman con el celular.
- **Luces:** intensidad general al 60 % (`LUZ_GENERAL`) y las blancas a la mitad.
- **Para tu Claude:** todo esto está explicado en `CLAUDE.md` (secciones Calidad alta y Público).
  Para coreografiar otra escena se usa `PUB.despeje`, `PUB.animo` o `pubCoreo(...)`.
- **Próximo paso sugerido:** coreografiar el público de la **Presentación**.

Recordá: `git pull` antes de empezar y una sola compu editando el visor a la vez.
