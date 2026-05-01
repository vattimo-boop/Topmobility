# 🔧 Guía de configuración Firebase para Topmobility

Sigue estos pasos exactos para activar la base de datos. Tarda unos 10 minutos.

---

## PASO 1 — Crear proyecto Firebase

1. Ve a https://console.firebase.google.com
2. Pulsa **"Añadir proyecto"**
3. Nombre: `topmobility` → Continuar
4. Desactiva Google Analytics (no lo necesitas) → **Crear proyecto**
5. Espera a que se cree → pulsa **Continuar**

---

## PASO 2 — Obtener tus credenciales

1. En el panel de Firebase, pulsa el icono **`</>`** (Web)
2. Nombre de la app: `topmobility-web` → **Registrar app**
3. Verás un bloque de código como este:

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "topmobility-xxxxx.firebaseapp.com",
  projectId: "topmobility-xxxxx",
  storageBucket: "topmobility-xxxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

4. **Copia ese bloque completo**

---

## PASO 3 — Pegar credenciales en index.html

1. Abre el archivo `index.html` con cualquier editor de texto
   (Notepad, TextEdit, VS Code, etc.)
2. Busca este bloque (línea ~20):

```js
const firebaseConfig = {
  apiKey:            "TU_API_KEY",
  authDomain:        "TU_PROJECT.firebaseapp.com",
  ...
```

3. **Reemplaza ese bloque** con el que copiaste de Firebase
4. Guarda el archivo

---

## PASO 4 — Crear la base de datos Firestore

1. En Firebase Console → menú izquierdo → **Firestore Database**
2. Pulsa **"Crear base de datos"**
3. Selecciona **"Comenzar en modo de prueba"** → Siguiente
4. Elige región: **`eur3 (europe-west)`** → **Listo**

---

## PASO 5 — Configurar permisos (reglas)

1. En Firestore → pestaña **"Reglas"**
2. Reemplaza el contenido con estas reglas:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /_ping/{doc} {
      allow read, write: if true;
    }
    match /requests/{doc} {
      allow read, write: if true;
    }
    match /history/{doc} {
      allow read, write: if true;
    }
  }
}
```

3. Pulsa **"Publicar"**

> Nota: Estas reglas son abiertas para empezar. Cuando tengas más usuarios,
> añade autenticación para mayor seguridad.

---

## PASO 6 — Publicar la app

### Opción rápida: Netlify (gratis)
1. Ve a https://netlify.com → crea cuenta gratuita
2. Arrastra la carpeta `topmobility/` al panel de Netlify
3. ¡Listo! Tu app estará en `https://topmobility.netlify.app`

### Dominio propio (topmobility.es)
- En Netlify → Domain settings → Add custom domain
- Coste del dominio: ~10€/año en https://dondominio.com

---

## ✅ Resultado final

Una vez configurado:
- Las solicitudes se guardan en la nube automáticamente
- El administrador ve las nuevas solicitudes al instante (tiempo real)
- El historial no se pierde nunca al cerrar el navegador
- Funciona en todos los dispositivos a la vez

---

## ❓ ¿Problemas?

- **"Error al leer datos"** → Revisa que las credenciales en index.html son correctas
- **"Permission denied"** → Revisa las reglas de Firestore (Paso 5)
- **La app no carga** → Asegúrate de publicar todos los archivos (index.html, manifest.json, sw.js, icons/)
