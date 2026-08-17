# Radar MP

Monitorea Compra Agil de Mercado Publico por palabras clave, 3 veces al dia, gratis.

## Instalar (una sola vez)

1. Crea un repo nuevo en GitHub (puede ser privado): https://github.com/new
2. Sube estos archivos completos (arrastra la carpeta entera a la pagina del repo,
   o usa "Add file" -> "Upload files").
3. Ve a **Settings -> Secrets and variables -> Actions -> New repository secret**.
   Nombre: `MP_TICKET`. Valor: tu ticket de api.mercadopublico.cl.
4. Ve a **Settings -> Pages**. En "Source" elige la rama `main` y carpeta `/ (root)`.
   Guarda. GitHub te va a dar una URL tipo
   `https://tu-usuario.github.io/tu-repo/` -- esa es la que abres en el iPhone.
5. Ve a la pestaña **Actions** del repo, entra a "Radar MP" y click en
   **Run workflow** para generar el primer reporte a mano (no esperes al cron).

## Uso diario

- El workflow corre solo a las 07:00, 13:00 y 19:00 hora Chile.
- Para cambiar las palabras clave: edita `keywords.txt` directo en GitHub
  (icono de lapiz), una palabra por linea, sin necesidad de tocar codigo.
- La pagina (`index.html`) siempre muestra el ultimo `reporte.json` generado.

## Nota sobre el modelo de probabilidad

El "termometro" hoy usa reglas simples (dias para cerrar, cotizaciones ya
recibidas, rango de monto). Para afinarlo con tu historial real de licitaciones
ganadas/perdidas, avisale a Claude en el chat para ajustar `calcular_probabilidad()`
en `mp_client.py`.
