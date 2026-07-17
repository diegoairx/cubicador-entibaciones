# Cubicador de Entibaciones — Ngenco SpA

App web para cubicación de sistemas de entibación (muro berlinés anclado temporal, muro berlinés en voladizo, soil nailing, micropilotes, fabricación de anclajes de cable y movimiento de tierra), con Análisis de Precios Unitarios, informe ejecutivo para gerencia y base de datos de seguimiento por cliente.

## Arquitectura

- `index.html` — aplicación completa (single-file, sin build). Gráficos con Chart.js (CDN).
- Base de datos: Supabase, proyecto **Optimizador Pile** (`jhikhnciakulgwhfflyv`), tabla `cubicador_proyectos` + vista `cubicador_seguimiento`. La app usa la clave publicable (diseñada para uso en frontend).

## Publicación en línea (GitHub Pages)

1. Crear repositorio en GitHub (por ejemplo `cubicador-entibaciones`).
2. Subir el contenido de esta carpeta (`index.html`, `README.md`).
3. En el repositorio: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `(root)` → Save**.
4. En 1–2 minutos la app queda disponible en `https://<usuario>.github.io/cubicador-entibaciones/`.

## Actualización de la app en línea

Cada vez que se reemplace `index.html` en la rama `main` (commit o subida por la web de GitHub), GitHub Pages republica automáticamente la nueva versión en la misma URL. No requiere ningún paso adicional.

## Metodología de cálculo

Fórmulas replicadas y validadas contra las planillas de ingeniería:
- **MBA Siete Lagunas Rev.2** — muro berlinés anclado, movimiento de tierra.
- **MBA Anclajes (solicitud de fabricación)** — cable 0,6", separadores 2/6 vías, vainas, tubo de inyección, cuñas cónicas.

Los precios unitarios precargados son referenciales y editables; validar antes de cotizar.

## Seguridad y acceso

Acceso restringido con Supabase Auth (correo + contraseña). Las políticas RLS solo permiten leer/escribir a usuarios autenticados cuyo correo esté en la tabla `equipo_autorizado` (lista blanca gestionable desde la pestaña Base de Datos de la app). Crear cuenta no otorga acceso si el correo no está autorizado.

Flujo de alta de un integrante: (1) un miembro del equipo autoriza su correo en la app, (2) el integrante crea su cuenta con ese correo, (3) confirma el correo desde su email y (4) inicia sesión.

---
© Ngenco SpA — Servicios y Maquinarias · www.ngencospa.com
