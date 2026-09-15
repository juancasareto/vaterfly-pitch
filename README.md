# Vaterfly — Carpeta de Proyecto (HTML)

Workspace de trabajo para la presentación de Vaterfly (carpeta de proyecto de Absoluto para Club Media), convertida de PDF a HTML.

## Estructura

```
index.html          → la presentación completa, 8 secciones
assets/img/          → imágenes extraídas del PDF original
```

## Cómo editar

- `index.html` tiene todo el CSS inline en el `<head>`, sin dependencias externas.
- Para previsualizar local: `python3 -m http.server 8000` desde esta carpeta, y abrir `http://localhost:8000`.
- Cada sección del PDF original (`01/ Quiénes somos`, `02/ El proyecto`, etc.) es un `<section>` independiente en el HTML — fácil de ubicar y editar por separado.

## Publicar cambios (flujo de trabajo con git)

1. Hacer los cambios en `index.html` o en `assets/img/`
2. `git add -A`
3. `git commit -m "descripción corta del cambio"`
4. `git push`

Cada commit queda registrado con fecha, autor y qué cambió — así se puede ver el historial completo y volver atrás si hace falta (`git log`, `git diff`, `git revert`).

## Publicación (GitHub Pages)

El repo tiene GitHub Pages activado sobre la rama `main`. La versión pública queda en:

`https://juancasareto.github.io/vaterfly-pitch/`

Cada `git push` a `main` actualiza automáticamente esa URL (tarda ~1 minuto).
