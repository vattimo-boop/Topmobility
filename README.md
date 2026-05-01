# Topmobility PWA

Aplicación de taxis premium para Madrid. Progressive Web App instalable en iOS y Android.

---

## Archivos incluidos

```
topmobility/
├── index.html        ← App completa
├── manifest.json     ← Config PWA (nombre, icono, colores)
├── sw.js             ← Service Worker (modo offline)
├── icons/
│   ├── icon-192.png  ← Icono app (192×192px) — AÑADIR
│   └── icon-512.png  ← Icono app (512×512px) — AÑADIR
└── README.md
```

> **Importante:** Debes añadir los iconos de la app en la carpeta `icons/`.
> Usa el logo de Topmobility en fondo oscuro (#1a1a2e), formato PNG.
> Puedes generarlos en: https://favicon.io o https://realfavicongenerator.net

---

## Cómo publicar (3 opciones)

### Opción A — Netlify (gratis, 5 minutos)
1. Ve a https://netlify.com y crea una cuenta gratuita
2. Arrastra la carpeta `topmobility/` al panel de Netlify
3. Tu app estará en `https://topmobility.netlify.app`
4. Para dominio propio (topmobility.es): en Netlify → Domain settings → Add custom domain

### Opción B — GitHub Pages (gratis)
1. Crea un repositorio en https://github.com
2. Sube todos los archivos
3. Ve a Settings → Pages → Branch: main → Save
4. URL: `https://tuusuario.github.io/topmobility`

### Opción C — Hosting propio
1. Contrata hosting en Hostinger, SiteGround, etc. (~3-5€/mes)
2. Sube los archivos por FTP o panel de control
3. Apunta el dominio topmobility.es al hosting

---

## Cómo instalar la app en el móvil

### Android (Chrome)
- Al abrir la web, aparece banner automático "Instalar app"
- O bien: menú (⋮) → "Añadir a pantalla de inicio"

### iPhone / iPad (Safari)
- Abrir la web en Safari
- Pulsar el botón compartir (□↑)
- "Añadir a pantalla de inicio"
- La app aparece con icono propio, sin barra del navegador

---

## Contraseña administrador
`calabaza1972`

Para cambiarla: editar `index.html`, buscar `calabaza1972` y reemplazar.

---

## Próximos pasos recomendados

- [ ] Añadir base de datos real (Firebase, Supabase) para que los datos persistan
- [ ] Notificaciones push reales al cliente (vía OneSignal o Firebase)
- [ ] Envío de SMS con la matrícula (vía Twilio)
- [ ] Panel de gestión de conductores
- [ ] Historial con filtros por fecha
