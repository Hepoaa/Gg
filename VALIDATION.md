# Validación — FamilyOS Cloudflare OneClick

Fecha: 2026-09-27.

## Validaciones realizadas

- `package.json`, `package-lock.json`, `wrangler.jsonc` y `manifest.webmanifest` son JSON válido.
- Las migraciones `0001_initial.sql` y `0002_categories.sql` se aplicaron juntas en SQLite en memoria con foreign keys activadas.
- Se verificaron las 27 tablas funcionales del esquema, incluidas auth, finanzas, familia, documentos, IA, notificaciones y auditoría.
- `wrangler.jsonc` no contiene `database_id` ni `bucket_name`: D1 y R2 quedan preparados para autoaprovisionamiento.
- No hay NVIDIA API keys reales ni `SESSION_SECRET` real dentro del paquete.
- `.dev.vars.example` contiene únicamente nombres de secretos vacíos.
- `node_modules`, `.git`, `.dev.vars` y cachés no se incluyen en el ZIP.
- Las versiones npm se fijaron a las versiones que el build de Cloudflare instaló correctamente durante la prueba previa del proyecto (TypeScript se mantiene en 5.9.3).

## Nota de compilación local

Este entorno no pudo completar una nueva descarga de npm por restricciones de red. El código base anterior sí llegó a completar `vite build` correctamente en Cloudflare Workers Builds; esta edición conserva el código de aplicación y cambia principalmente el aprovisionamiento/configuración de despliegue.
