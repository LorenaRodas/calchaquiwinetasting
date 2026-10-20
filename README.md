# Calchaquí Wine Tasting

Código fuente de la versión 47 publicada en Sites.

- Sitio: https://calchaquiwinetasting.com.ar
- Commit de origen en Sites: `ce177fc080af9c52374878e7d3a54df5f93e7155`
- Aplicación: Next.js / Vinext sobre Cloudflare Workers; datos en D1 y archivos en R2.
- Autenticación de socios: flujos de Supabase Auth para correo y Google, con activación independiente. SMTP y OAuth requieren configuración y pruebas reales antes de habilitarse.

## Alcance de esta copia

Incluye código, recursos estáticos, migraciones, documentación y pruebas. No incluye datos de producción, membresías, archivos adicionales de R2, identidades de Supabase, secretos ni variables de producción. No es un respaldo completo del servicio. El historial anterior permanece en el repositorio de Sites; esta copia comienza con una instantánea de la versión 47.

## Desarrollo

Se requiere Node.js >=22.13 y pnpm según `packageManager` en `package.json`. Instalar dependencias con `pnpm install --frozen-lockfile`. Consultar `docs/club-email-access.md` para la configuración de autenticación y sus límites.

Pruebas: `node scripts/club-email-smoke.mjs`, `node scripts/club-smoke.mjs` y `pnpm exec tsc --noEmit`. Las pruebas de autenticación usan un proveedor simulado; no certifican email o Google en producción.

## Publicación y datos

GitHub conserva esta copia del código. Subir un commit aquí no publica automáticamente el sitio: el despliegue actual se gestiona en Sites. No ejecutar migraciones ni cambiar los vínculos de D1/R2 sin revisar el entorno de destino. Conservar las migraciones existentes.

Los secretos se configuran en el servicio correspondiente. Nunca guardar un Personal Access Token administrativo, claves de Resend o secretos OAuth en este repositorio. `.env.example` contiene únicamente nombres y valores vacíos de referencia.
