# El Oro Verde · Róbale el descuento al duende

Landing promocional de [El Oro Verde](https://www.eloroverde.com/) con un videojuego de plataformas incluido: el jugador recoge monedas de descuento y puede conseguir hasta un 15 % en su compra.

Todo está en un único `index.html` autocontenido (CSS, JavaScript e imágenes en base64).

## Publicación (GitHub Pages)

Settings → Pages → *Deploy from a branch* → rama `main`, carpeta `/ (root)`.
La landing queda en `https://<usuario>.github.io/oroverde/`.

## Secciones

Aviso +18, barra de envío gratis desde 45 €, cabecera con logo, menú, portada, cómo funciona (3 pasos), el videojuego, 3 productos, ventajas de la tienda y pie con contacto.

## El juego

- **Suertecillo**, un trébol de cuatro hojas, corre solo. Saltar: espacio, flecha arriba, W o toque. Mantener pulsado en el aire para planear con la hélice (se recarga en el suelo).
- **Don Chistera**, el duende, ataca con sombrero bumerán, brazo elástico y red; su rabia sube en 5 niveles según la distancia. También hay cepos y hoyos.
- Cada moneda "1%" suma un 1 % de descuento, hasta el 15 %. Una sola vida.
- Una sola partida por navegador, guardada en `localStorage` (clave `oroverde-partida`). Al volver se muestra el código conseguido.

## Configuración

Objeto `CONFIG` al principio del `<script>` en `index.html`:

| Clave | Para qué sirve |
|---|---|
| `tiendaURL` | Enlace a la tienda. |
| `maxDescuento` | Tope de descuento (15). |
| `permitirReinicio` | Con `true`, añadir `#reiniciar` a la URL borra la partida guardada. **Ponlo en `false` antes de enseñárselo a clientes.** |
| `codigos` | Un código por porcentaje, del 1 al 15 (`VERDE01-KQ` … `VERDE15-BZ`). **Cada uno debe existir en la tienda** como descuento de ese porcentaje, de un solo uso por cliente. |
| `productos` | Nombre, imagen, precios, etiquetas, texto y `url`. Las `url` apuntan ahora a la portada; cámbialas por los enlaces reales de cada producto. |

## Limitaciones conocidas

- La partida única se controla por navegador: en otro dispositivo o en incógnito se puede volver a jugar.
- Los códigos están en el código fuente; se compensa limitándolos a un uso por cliente en la tienda.
- Para algo más estricto haría falta un pequeño servidor que valide la partida (por ejemplo, pidiendo el email antes de jugar).
