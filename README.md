# CompraInclusiva (frontend)

Tienda en línea accesible: "Compra sin barreras, para todos". Proyecto de la materia Modelado Ágil del Software (ULEAM, 5.º "B"), basado en el prototipo de CompraFácil Inclusiva.

- **Sitio desplegado (Azure):** https://compra-inclusiva-web-fhardecbgrath0cr.brazilsouth-01.azurewebsites.net
- **Repositorio:** https://github.com/JordyMacias/frontend-CompraInclusiva

## Tecnologías

React + TypeScript + Vite + Tailwind CSS (PostCSS). Despliegue continuo con GitHub Actions hacia Azure App Service (Linux, Node 24 LTS).

## Requisitos de ejecución

| Herramienta | Versión |
|---|---|
| Node.js | 24 LTS (la misma que usa Azure) |
| npm | la que incluye Node 24 |
| Git | cualquier versión reciente |

## Cómo ejecutarlo en local

```bash
git clone https://github.com/JordyMacias/frontend-CompraInclusiva.git
cd frontend-CompraInclusiva
npm install
npm run dev        # servidor de desarrollo (Vite), normalmente en http://localhost:5173
```

Para generar la versión de producción (la misma que ejecuta el workflow):

```bash
npm run build      # ejecuta "tsc -b && vite build" y crea la carpeta dist/
```

> Ajustar si en `package.json` los nombres de los scripts son distintos.

## Estrategia de ramas

Se usa un flujo simple basado en ramas cortas y Pull Request (GitHub Flow):

| Rama | Uso |
|---|---|
| `main` | Siempre estable. Cada push o merge despliega automáticamente a Azure. Protegida: solo se cambia mediante Pull Request. |
| `feature/<nombre-corto>` | Una historia de usuario o mejora (ej. `feature/menu-accesibilidad`). |
| `fix/<nombre-corto>` | Corrección de un error (ej. `fix/prueba-carrito`). |

Reglas:

1. Crear la rama desde `main` actualizada.
2. Hacer commits pequeños con mensajes del tipo `feat(...)`, `fix(...)`, `test(...)`, `chore(...)`.
3. Abrir un Pull Request hacia `main` indicando la historia de usuario y el criterio de aceptación que cubre.
4. El PR debe pasar los checks de GitHub Actions y ser revisado por al menos un compañero antes de fusionarse.
5. Borrar la rama después del merge.

## Funcionalidad verificable

**Menú de accesibilidad**

1. Abrir el sitio (local o Azure).
2. Pulsar el botón circular de accesibilidad, ubicado en la esquina inferior izquierda.
3. Debe abrirse el menú de opciones, organizado por categorías.
4. Activar una opción (por ejemplo, aumentar el tamaño del texto o el alto contraste) y comprobar que el cambio se aplica a toda la página.
5. Cerrar el menú y comprobar que la configuración se mantiene.

Esta funcionalidad se valida con pruebas automáticas ejecutadas en el workflow (ver sección siguiente de la práctica).

## Estructura del proyecto

```
.github/workflows/   Workflow de CI/CD (build + deploy a Azure)
public/              Recursos públicos
src/                 Código fuente de la aplicación
index.html           Punto de entrada
package.json         Dependencias y scripts
```

## Autor

Jordy Leodan Macías Lucas, docente: Ing. Israel Julio Gómez Calderón.
