# FamilyOS — Deploy to Cloudflare (Android / 1-click)

Esta versión NO necesita que copies manualmente un `database_id` ni que crees un bucket R2 antes del despliegue.
Cloudflare puede aprovisionar automáticamente D1 y R2 porque `wrangler.jsonc` declara únicamente los bindings `DB` y `FAMILYOS_FILES`.

## La forma más sencilla desde Android

### 1. Sube el contenido de este ZIP a GitHub

El repositorio debe contener en la raíz, entre otros:

- `package.json`
- `wrangler.jsonc`
- `worker/`
- `src/`
- `migrations/`
- `public/`

No subas el ZIP como único archivo si Cloudflare va a clonar el repositorio: los archivos deben estar extraídos.

### 2. Para el botón oficial “Deploy to Cloudflare”, el repositorio debe ser público

Cuando tu repositorio esté listo, usa esta dirección reemplazando `USUARIO` y `REPOSITORIO`:

https://deploy.workers.cloudflare.com/?url=https://github.com/USUARIO/REPOSITORIO

Ejemplo de formato:

https://deploy.workers.cloudflare.com/?url=https://github.com/tuusuario/FamilyOS

### 3. En la pantalla de Cloudflare

Cloudflare te permitirá elegir/confirmar:

- nombre del repositorio clonado
- nombre del Worker
- recursos requeridos
- secretos requeridos

La configuración de este proyecto permite que Cloudflare cree automáticamente:

- D1 para el binding `DB`
- R2 para el binding `FAMILYOS_FILES`

No necesitas pegar un UUID de D1.

### 4. Secretos

Introduce:

- `NVIDIA_API_KEY`: tu API key de NVIDIA
- `SESSION_SECRET`: una cadena aleatoria de al menos 32 caracteres

No guardes esos valores en GitHub.

### 5. Migraciones

El script de despliegue está preparado para ejecutar:

`wrangler d1 migrations apply DB --remote`

antes de publicar el Worker. Esto crea las tablas de FamilyOS utilizando los archivos de `migrations/`.

### 6. Abrir FamilyOS

Al finalizar, Cloudflare mostrará una URL `*.workers.dev` (o tu dominio si lo configuras).
Ábrela y completa el onboarding para crear tu familia y propietario.

## Si ya tienes un Worker conectado a GitHub

Puedes reemplazar el contenido de tu repositorio por esta versión y volver a desplegar. La clave es que `wrangler.jsonc` ya NO tiene `database_id` ni `bucket_name` fijos.

Si Cloudflare conserva bindings antiguos de un proyecto previo y da conflicto, crea un Worker nuevo mediante “Deploy to Cloudflare”; es el camino más limpio para esta versión.
