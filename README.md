# VozClara
Un lector de texto a voz con estética de biblioteca tranquila y español rioplatense. Frontend estático, sin cuentas ni backend, con Web Speech API y localStorage.

## Arrancar
```sh
npm install
npm run dev -- --port 3849
```
Abrí http://localhost:3849. Para producción: `npm run build`. Para revisar el resultado: `npm run preview`.

## Uso
Pegá texto o subí un archivo UTF-8 `.txt` / `.md` de hasta 2 MB. Elegí una voz del dispositivo, velocidad y tono. Reproducí, pausá, reanudá o detené. La vista de lectura resalta la oración actual; el control anterior retrocede una oración. Guardá textos en Biblioteca para volver a abrirlos. Ajustes permite cambiar el tamaño de lectura, exportar la biblioteca en JSON y borrarla.

El borrador, preferencias y textos guardados quedan en este navegador/origen. Borrar los datos del navegador los elimina. No hay sincronización ni importación del JSON exportado. No se admiten PDF ni DOCX.

## Offline y GitHub Pages
Subí el contenido de `dist/` a GitHub Pages o cualquier servidor estático. Vite usa rutas relativas para funcionar en subdirectorios. No necesita Node en producción. Navegación con hashes y meta `noindex,nofollow`.

El build genera un service worker que guarda la app y sus cuatro imágenes para usarla offline después de una primera visita completa. Requiere HTTPS o localhost. Las voces **locales** del sistema funcionan sin conexión; otras voces pueden necesitar internet. La disponibilidad y calidad de voces, pausa y reanudación dependen del navegador y sistema operativo. Si no hay Web Speech API se informa el problema, mientras editor y biblioteca siguen disponibles. Tiempo de escucha estimado a partir de palabras; progreso por oraciones.

## Verificar
Con el servidor de desarrollo en 3849:
```sh
npx playwright test --reporter=line
```
Los tests usan una voz simulada: verifican estados y callbacks, no la salida de audio física. Capturas en `tests/vozclara-1280.png` y `tests/vozclara-390.png`.

## Diseño e imágenes
Dirección y referencias en `spec.md`. Imágenes originales generadas con el tool integrado imagegen, guardadas en `assets/`: `hero-escucha.png`, `desk.png`, `headphones.png`, `bookmark.png`.
Prompts: fotografías editoriales de (1) libro abierto y auriculares verdes sobre escritorio junto a ventana; (2) escritorio de biblioteca con libro de lino y taza; (3) auriculares verdes sobre papel junto a libro; (4) señalador de tela verde entre páginas. Paleta crema, nogal y verde; luz natural, sin textos ni logos.
