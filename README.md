# FamilyOS

FamilyOS es una PWA familiar privada construida con React, TypeScript, Vite y Cloudflare Workers, D1 y R2.

## Despliegue recomendado

Esta edición está preparada para **Deploy to Cloudflare** con aprovisionamiento automático de D1 y R2. No necesitas copiar manualmente un `database_id`.

Lee primero: **`DEPLOY-ONE-CLICK.md`**.

Para usar el botón oficial, sube este proyecto a un repositorio público de GitHub y abre:

`https://deploy.workers.cloudflare.com/?url=https://github.com/USUARIO/REPOSITORIO`

## Secretos

Cloudflare debe almacenar como secretos:

- `NVIDIA_API_KEY`
- `SESSION_SECRET`

Nunca los pongas en React, `wrangler.jsonc`, GitHub o `public/`.

## Desarrollo local

```bash
npm install
npm run dev
```

Copia `.dev.vars.example` a `.dev.vars` sólo en tu máquina y completa los secretos locales. `.dev.vars` está ignorado por Git.

## Verificación

```bash
npm run typecheck
npm run lint
npm run test
npm run build
```

## Despliegue manual alternativo

```bash
npm run deploy
```

El script aplica las migraciones remotas de D1 y después despliega el Worker.
