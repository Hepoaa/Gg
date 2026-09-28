# Desplegar FamilyOS en Cloudflare

## Recomendado: Deploy to Cloudflare

Esta edición usa el aprovisionamiento automático de Cloudflare. No necesitas crear D1/R2 manualmente ni copiar un `database_id`.

Desde Android sigue `ANDROID-QUICKSTART.md` o `DEPLOY-ONE-CLICK.md`.

## Qué crea Cloudflare

El archivo `wrangler.jsonc` declara:

- `DB` como binding D1, sin ID fijo.
- `FAMILYOS_FILES` como binding R2, sin bucket fijo.
- `ASSETS` para la PWA/SPA.

Cloudflare puede crear y enlazar esos recursos durante el flujo de despliegue.

## Secretos obligatorios

Configura en Cloudflare:

- `NVIDIA_API_KEY`: tu clave NVIDIA.
- `SESSION_SECRET`: texto aleatorio de al menos 32 caracteres.

Nunca los subas a GitHub.

## Migraciones

El script `npm run deploy` ejecuta las migraciones del binding `DB` y despliega el Worker.

## Alternativa manual

Si desarrollas desde una computadora:

```bash
npm install
npx wrangler login
npm run typecheck
npm run test
npm run build
npm run deploy
```

Wrangler 4.45+ soporta aprovisionamiento automático de D1/R2 cuando los bindings no incluyen IDs/nombres específicos.
