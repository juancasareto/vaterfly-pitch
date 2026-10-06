# Setup para Claude · dejar esta compu lista para trabajar en Vaterfly

> **Para Claude.** La persona que te pasó este archivo quiere trabajar en el visor 3D de Vaterfly
> (repo `juancasareto/vaterfly-pitch`). Hacé los pasos en orden, verificando cada uno antes de seguir.
> Hablá en castellano rioplatense, explicá en una línea qué hacés en cada paso (es la primera vez que lo hace)
> y frená a pedirle ayuda solo en los pasos marcados **[PERSONA]**. Si algo ya está hecho, decilo y seguí.
> No cambies cuentas, contraseñas ni configuraciones de seguridad por tu cuenta.

## 1. Herramientas

1. **git:** `git --version`. Si falta, pedile **[PERSONA]** que corra `xcode-select --install`, acepte la ventana y avise cuando termine.
2. **Homebrew:** `brew --version`. Si falta, explicale que hace falta para instalar la herramienta de GitHub y pedile **[PERSONA]**
   que corra en la Terminal el instalador oficial de https://brew.sh (pide la contraseña de la Mac). Al terminar, seguí las
   instrucciones que imprime para agregar `brew` al PATH.
3. **GitHub CLI:** `gh --version`. Si falta: `brew install gh`.

## 2. Cuenta de GitHub

1. `gh auth status`. Si no hay sesión, pedile **[PERSONA]** que corra en la Terminal:
   `gh auth login --hostname github.com --git-protocol https --web`
   y siga el código que aparece en el navegador con **su** cuenta de GitHub.
2. Verificá el permiso de escritura sobre el repo:
   `gh api repos/juancasareto/vaterfly-pitch/collaborators/$(gh api user --jq .login)/permission --jq .permission`
   Tiene que decir `write` o `admin`. Si no, avisale que Juan lo tiene que invitar como colaborador (rol Write) y pará acá.
3. Si `git config --global user.name` o `user.email` están vacíos, preguntale su nombre y mail y configuralos.

## 3. Bajar el proyecto

- Si no existe `~/Desktop/vaterfly-pitch`: `gh repo clone juancasareto/vaterfly-pitch ~/Desktop/vaterfly-pitch`
- Si ya existe: `cd ~/Desktop/vaterfly-pitch && git pull`

## 4. Probar el visor en local

1. Desde `~/Desktop/vaterfly-pitch` levantá un servidor: `python3 -m http.server 8767` (en segundo plano).
2. Abrí `http://localhost:8767/rendertest/` en el navegador integrado si lo tenés; si no, pasale el link.
   La contraseña de la barrera es la que figura en `rendertest/index.html` (busca `PASSWORD`).
3. Confirmá que carga sin errores en consola y después cerrá el servidor.

## 5. Notion

Las fichas de los mecanismos están en Notion › VATERFLY › *Mecanismos y estructuras*.
Si no tenés herramientas de Notion disponibles, pedile **[PERSONA]** que en la app de Claude vaya a
**Configuración → Conectores → Notion**, autorice el workspace de VATERFLY y abra una sesión nueva.
Si ya las tenés, buscá la página "Mecanismos y estructuras" para confirmar que la ves.

## 6. Abrir el proyecto en Claude

Pedile **[PERSONA]** que, en la pestaña **Code** de la app, abra una sesión nueva eligiendo la carpeta
`~/Desktop/vaterfly-pitch`. Ahí Claude lee `CLAUDE.md`, que explica cómo está hecho el visor y cómo se publica.

## 7. Cierre

Mostrale un resumen con ✓ / ✗ de cada paso y proponele una primera prueba para la sesión nueva, por ejemplo:

> "Hacé git pull. Después, en el visor, cambiá la altura de la percha del Pelea telón a 8 m.
> Probalo local y mostrame cómo queda antes de publicar."

Recordale las reglas: **siempre `git pull` antes de empezar**, **una sola compu editando el visor a la vez**,
y **nada privado en el repo** (es público).
