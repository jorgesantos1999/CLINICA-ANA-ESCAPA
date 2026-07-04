# Guía paso a paso: dominio, hosting y Google

Esto es lo único que **tienes que hacer tú** (requiere pagar y crear cuentas, así que no
puedo hacerlo por ti) — pero te dejo cada paso exacto para que sea rápido. Cuando lo
tengas, dime y te ayudo con la parte técnica (DNS, verificación, etc.).

## 1. Comprar el dominio

Recomendado: **`clinicaanaescapa.es`** (coincide con el nombre del negocio y con
@clinicaanaescapa de Instagram — ideal para SEO local y para que Google lo reconozca
como la web oficial). Comprobado disponible hoy.

Dónde comprarlo:

- **Nominalia** — registrador español, especializado en dominios `.es`, buena opción si
  quieres soporte en español y todo (dominio + hosting) en el mismo sitio.
- **IONOS** — también español/alemán, con planes de hosting incluidos si no quieres usar
  Netlify.
- **Namecheap** — más internacional, también soporta `.es`.

⚠️ Los dominios `.es` exigen que el titular tenga NIF/NIE/CIF o sea residente de la UE —
tu madre, como autónoma/empresa en España, cumple esto sin problema. Te pedirán ese dato
al comprar.

El precio del primer año suele estar rebajado (a veces por debajo de 5€) y la renovación
anual ronda los 10-15€/año — compara el precio de renovación, no solo el de bienvenida.

Compra también, si quieres, la versión `.com` (`clinicaanaescapa.com`) para redirigirla
al `.es` y evitar que otro la registre — es opcional pero barato y recomendable a largo
plazo.

## 2. Elegir hosting (dónde "vive" la web)

Como esta web es estática (HTML/CSS/JS, sin base de datos), lo más simple y sin coste es:

- **Netlify** o **Vercel** (gratis, HTTPS automático, arrastras la carpeta del proyecto y
  ya está online). Recomendado si quieres la opción más rápida y sin mantenimiento.
- Si prefieres todo con el mismo proveedor español (factura única, soporte en español),
  el hosting de **IONOS** o **Nominalia** también sirve perfectamente para esta web.

## 3. Conectar el dominio comprado con el hosting

1. En Netlify/Vercel: "Add custom domain" → escribe `clinicaanaescapa.es`.
2. Te darán 1-2 registros DNS (normalmente un registro tipo `A` o `CNAME`).
3. Entra en el panel de tu registrador (Nominalia/IONOS/Namecheap) → gestión de DNS del
   dominio → añade esos registros tal cual te los den.
4. Espera unas horas (a veces minutos) a que se propague. El propio hosting activará el
   HTTPS automáticamente en cuanto detecte el dominio apuntando bien.

## 4. Vincular con Google

1. **Google Search Console** (search.google.com/search-console) → "Añadir propiedad" →
   pon `https://www.clinicaanaescapa.es` → te dará un código de verificación → pégalo en
   `index.html`, en esta línea que ya está preparada (solo quítale el comentario):
   ```html
   <meta name="google-site-verification" content="TU_CODIGO_AQUI">
   ```
2. **Google Business Profile** (antes Google My Business) → edita la ficha del negocio →
   añade `https://www.clinicaanaescapa.es` como sitio web. Esto es lo que hace que la web
   aparezca enlazada desde Google Maps y desde la ficha que sale al buscar "Clínica Ana
   Escapa" en Google.
3. (Opcional) **Google Analytics** → crea una propiedad → te da un script `gtag.js` →
   pégalo justo antes de `</head>` en `index.html` y dime, te lo integro yo si prefieres.

## 5. Cuando tengas el dominio comprado

Dímelo y yo me encargo de:
- Actualizar todas las URLs del sitio (`index.html`, `sitemap.xml`, `robots.txt`, JSON-LD)
  si cambia el nombre final del dominio.
- Ayudarte a configurar los registros DNS exactos.
- Integrar el código de verificación de Google y/o Analytics.
