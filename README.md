# Lluvia de ideas con QR

Página web para GitHub Pages. Quien la abre escribe una pregunta, se genera un QR, y cada persona que lo escanea responde con hasta 3 palabras (un envío por palabra). Las palabras aparecen en vivo en una nube de ideas, y las repetidas se ven más grandes. Las respuestas son anónimas.

## Archivos

- `index.html`: toda la página (HTML, CSS y JavaScript).
- `firestore.rules`: reglas de seguridad de Firebase (limitan a 3 palabras por persona).

## Puesta en marcha

### 1. Crear el proyecto en Firebase (gratis)

1. Entrá a https://console.firebase.google.com y creá un proyecto.
2. En **Build > Firestore Database**, creá la base de datos (modo producción).
3. En **Build > Authentication > Sign-in method**, activá **Anónimo**.
4. En **Authentication > Settings > Authorized domains**, agregá `TU_USUARIO.github.io`.
5. En **Project settings > Your apps**, registrá una app web y copiá el objeto `firebaseConfig`.

### 2. Pegar la configuración

Abrí `index.html`, buscá el bloque `firebaseConfig` y reemplazá los valores por los de tu proyecto.

### 3. Pegar las reglas

En **Firestore Database > Rules**, pegá el contenido de `firestore.rules` y publicá.

### 4. Publicar en GitHub Pages

1. Subí `index.html`, `firestore.rules` y este `README.md` a un repositorio nuevo.
2. En **Settings > Pages**, elegí la rama `main` y la carpeta `/ (root)`.
3. Abrí `https://TU_USUARIO.github.io/NOMBRE_DEL_REPO/`.

## Cómo se usa

1. Abrí la página, escribí la pregunta y tocá **Crear sala**.
2. Proyectá la pantalla: se ve la pregunta, el QR y la nube.
3. Cada persona escanea el QR, escribe una palabra y toca **Enviar palabra**. Puede repetir hasta 3 veces.

## Notas

- Las claves de `firebaseConfig` son públicas por diseño. La seguridad la dan las reglas de `firestore.rules`.
- El límite de 3 palabras se aplica por dispositivo y navegador: si alguien borra los datos del navegador o abre una ventana privada, recibe un usuario anónimo nuevo.
- Si cerrás la pestaña del anfitrión, volvé a abrir la misma dirección (`?s=CODIGO&host=1`) para ver la sala de nuevo.
