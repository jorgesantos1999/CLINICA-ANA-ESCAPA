# Guía paso a paso: subir la web a Netlify y conectar clinicaanaescapa.es

Ya está listo por mi parte: el proyecto tiene un repositorio Git local con un primer
commit (`C:\CLAUDE CODE`), preparado para subir a GitHub y desplegar en Netlify. Los
pasos que quedan requieren que crees cuentas y pulses botones tú mismo (no puedo
crear cuentas ni introducir pagos en tu nombre), pero aquí tienes cada paso exacto.

## 1. Crear tu cuenta de GitHub (gratis, 2 minutos)

1. Ve a **github.com/join**.
2. Regístrate con el email de la clínica (o el tuyo) y una contraseña.
3. Verifica el email cuando te lo pidan.

## 2. Instalar GitHub Desktop (la forma más fácil de subir el proyecto, sin usar la terminal)

1. Descarga **GitHub Desktop** desde **desktop.github.com** e instálalo.
2. Ábrelo e inicia sesión con la cuenta de GitHub que acabas de crear.
3. Menú **File → Add local repository...**
4. Selecciona la carpeta `C:\CLAUDE CODE` (ya tiene el repositorio Git preparado).
5. GitHub Desktop mostrará un botón **"Publish repository"** arriba — púlsalo.
   - Puedes dejarlo como repositorio **público** (recomendado, es solo el código de
     una web, no hay datos sensibles) o marcarlo como privado si prefieres.
   - Esto crea el repositorio en tu cuenta de GitHub automáticamente, sin tener que
     crearlo antes en la web.

A partir de ahora, cada vez que yo (o tú) cambiéis algo en la web, en GitHub Desktop
aparecerá el cambio listo para "Commit" y "Push origin" — así de simple se actualiza
la web en el futuro.

## 3. Crear la cuenta de Netlify y desplegar la web

1. Ve a **app.netlify.com/signup**.
2. Elige **"Sign up with GitHub"** — así quedan conectadas las dos cuentas directamente
   (te pedirá autorizar el acceso, acéptalo).
3. En el panel de Netlify: **"Add new site" → "Import an existing project"**.
4. Elige **GitHub**, autoriza si te lo pide, y selecciona el repositorio que acabas de
   publicar (el nombre de la carpeta, algo como `CLAUDE-CODE` o el que le hayas puesto).
5. En la configuración de despliegue:
   - **Build command**: déjalo vacío.
   - **Publish directory**: pon un punto `.`
6. Pulsa **"Deploy site"**. En un minuto tendrás la web publicada en una URL temporal
   tipo `algo-aleatorio-123.netlify.app` — ábrela para comprobar que todo se ve bien.

## 4. Conectar tu dominio clinicaanaescapa.es

1. En el panel de tu sitio en Netlify: **"Domain settings" → "Add a domain"**.
2. Escribe `clinicaanaescapa.es` y confirma. Netlify comprobará que ya es tuyo (por
   estar registrado) y te ofrecerá dos formas de conectarlo — usa la **opción A**, es
   la más simple y la que recomiendo:

### Opción A (recomendada): usar los DNS de Netlify

1. Netlify te mostrará 4 "nameservers" (servidores de nombres), algo como:
   `dns1.p05.nsone.net`, `dns2.p05.nsone.net`, etc.
2. Entra en el panel de administración de tu dominio, en el proveedor donde lo
   compraste (busca una sección llamada **"Nameservers"**, **"Servidores DNS"** o
   **"Servidores de nombres"**).
3. Sustituye los que haya puestos por los 4 que te dio Netlify.
4. Guarda los cambios.

La propagación suele tardar entre unos minutos y pocas horas. Netlify detectará el
cambio automáticamente y activará el certificado HTTPS gratis (Let's Encrypt) sin que
tengas que hacer nada más.

### Opción B (alternativa, si tu proveedor no te deja cambiar los nameservers)

Añade estos dos registros en el DNS de tu proveedor, dejando el resto como está:

| Tipo  | Nombre/Host | Valor |
|-------|-------------|-------|
| A     | @ (o vacío) | `75.2.60.5` |
| CNAME | www         | `TU-SITIO.netlify.app` (el que te asignó Netlify en el paso 3) |

## 5. Verificar que todo funciona

- Entra en `https://clinicaanaescapa.es` — debería cargar la web con el candado de
  HTTPS activo (puede tardar hasta un par de horas en activarse el certificado tras
  la propagación del DNS).
- Si después de unas horas sigue sin funcionar, dime en qué paso te has quedado y el
  mensaje exacto que te aparece, y lo revisamos juntos.

## 6. Recibir los mensajes del formulario de contacto por email

El formulario de "Contacto" usa **Netlify Forms** (ya integrado en el código, gratis
hasta 100 envíos/mes, sin necesidad de crear ninguna cuenta externa). Solo falta decirle
a Netlify a qué email avisar cuando alguien lo rellene:

1. En el panel de Netlify, entra en tu sitio → **"Forms"** (en el menú lateral).
   La primera vez que hagas un deploy con el formulario, aparecerá listado ahí
   automáticamente como "contacto".
2. Ve a **"Settings" → "Forms" → "Form notifications" → "Add notification" →
   "Email notification"**.
3. En el campo de email, escribe `jorgesantosescapa@gmail.com`.
4. Guarda. A partir de ahí, cada vez que alguien rellene el formulario de la web,
   te llegará un email a esa dirección con el nombre, teléfono, email y mensaje.

Después de enviar el formulario, el visitante verá una página de agradecimiento propia
de la web (`gracias.html`), no la genérica de Netlify.

## 7. Vincular con Google (una vez la web esté online con el dominio final)

1. **Google Search Console** (search.google.com/search-console) → añade la propiedad
   `https://www.clinicaanaescapa.es` → copia el código de verificación que te da →
   pégamelo y lo añado yo en el `<meta name="google-site-verification">` que ya está
   preparado en `index.html`.
2. **Google Business Profile** → edita la ficha del negocio → añade
   `https://www.clinicaanaescapa.es` como web.
3. (Opcional) **Google Analytics** → crea una propiedad → pégame el script `gtag.js`
   que te den y lo integro en la web.

## 8. Actualizar la web en el futuro

Cualquier cambio que hagamos en los archivos locales solo hay que:
1. Abrir GitHub Desktop → verás los cambios listados → escribe un resumen breve →
   **"Commit to master"** → **"Push origin"**.
2. Netlify detecta el push y vuelve a publicar la web automáticamente en 1-2 minutos.
