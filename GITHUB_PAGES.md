# Publicar Counter Ledger en GitHub Pages

Este proyecto funciona como **frontend 100% estático**. El navegador contiene la lógica de selección de héroes, el ranking ponderado de counterpicks, las explicaciones del transcript y el cálculo de tesoros. No necesita Node, Express, una API, una base de datos ni un servidor ejecutándose después del build.

## Publicación automática

Sube el contenido del proyecto a un repositorio de GitHub y usa la rama `main`. El workflow `.github/workflows/deploy-pages.yml` instala las dependencias, ejecuta `pnpm build`, toma `dist/public` como artefacto y lo publica mediante GitHub Pages.

En el repositorio, abre **Settings → Pages → Build and deployment** y selecciona **GitHub Actions** como source. Después de cada push a `main`, GitHub volverá a construir y publicar el sitio.

## Publicación manual opcional

Si prefieres generar el sitio localmente, ejecuta:

```bash
pnpm install
pnpm build
```

El contenido publicable queda en `dist/public`. Puedes subir esa carpeta mediante cualquier flujo de Pages que acepte artefactos estáticos.

## Nota sobre rutas y assets

Vite está configurado con `base: "./"`, por lo que los bundles y las imágenes se cargan con rutas relativas. Los assets de marca están dentro de `client/public/assets` y se copian automáticamente a `dist/public/assets`; por eso el sitio no depende del proxy de almacenamiento de Manus.
