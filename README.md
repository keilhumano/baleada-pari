# Baleada Pari 🫓

Invitación para la Baleada Pari — sábado 25 de julio, casa de Keil.
Página estática con una lista en vivo (quién trae qué) respaldada por Firebase Realtime Database.

**En vivo:** https://keilhumano.github.io/baleada-pari/

## Cómo funciona

- `index.html` — toda la página (HTML + CSS + JS en un solo archivo, imagen embebida en base64).
- La lista de "quién trae qué" se guarda en Firebase Realtime Database bajo `entries/`.
- Cualquiera con el link puede agregar y eliminar entradas (lista abierta, basada en confianza).

## Configuración de Firebase

El bloque `firebaseConfig` dentro de `index.html` apunta al proyecto de Firebase.
La `apiKey` de una app web **no es secreta** — es un identificador público. La seguridad
real vive en las reglas de la base de datos (`database.rules.json`), no en ocultar la config.

Las reglas permiten leer/escribir solo bajo `entries/` y validan que cada entrada tenga
`name` (≤80), `source` (≤120) y `order` (número). Todo lo demás queda bloqueado.

Para aplicar las reglas: Firebase Console → Realtime Database → pestaña **Rules** →
pegar el contenido de `database.rules.json` → **Publish**.
