# Subir FamilyOS desde Android

## Método fácil

1. Descarga y extrae `FamilyOS-Cloudflare-OneClick.zip`.
2. Sube todos los archivos y carpetas extraídos a la raíz de tu repositorio GitHub.
3. Verifica que GitHub muestre `worker/`, `src/`, `public/` y `migrations/`.
4. No necesitas editar `database_id`: esta versión no tiene uno.
5. Para usar el botón oficial de despliegue, el repositorio debe ser público.
6. Abre en Chrome:

`https://deploy.workers.cloudflare.com/?url=https://github.com/USUARIO/REPOSITORIO`

7. Sigue la pantalla de Cloudflare y configura los secretos solicitados.

## Si GitHub móvil no conserva carpetas

Sube el ZIP al repositorio y usa un Codespace:

```bash
unzip -o FamilyOS-Cloudflare-OneClick.zip
rm FamilyOS-Cloudflare-OneClick.zip
git add -A
git commit -m "FamilyOS one-click Cloudflare"
git push
```

Después confirma que las carpetas aparecen normalmente en GitHub.
