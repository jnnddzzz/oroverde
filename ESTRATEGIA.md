# Estrategia de la campaña "Róbale el descuento al duende" · El Oro Verde

Tarea 4X01 · Héroe y villano, un juego como estrategia de marketing.
Este documento resume la estrategia en 6 diapositivas y explica cómo encaja cada pieza (landing, email e Instagram).

---

## Diapositiva 1 · Empresa y objetivo

- **Empresa:** El Oro Verde (https://www.eloroverde.com/), tienda online de accesorios para fumadores y productos de CBD. Envía a península, Baleares, Canarias y Portugal, con envío gratis desde 45 €.
- **Público:** personas mayores de 18 años, sobre todo jóvenes adultos (18-35) que compran online y usan Instagram.
- **Objetivo principal:** **captar contactos**, es decir, conseguir emails con consentimiento para poder comunicarse con ellos.
- **Objetivo secundario:** **vender más**, porque cada jugador se lleva un código de hasta un 15 % que empuja a hacer la primera compra.
- **Fidelizar:** los jugadores que aceptan recibir ofertas entran en la lista de email para futuras campañas.

## Diapositiva 2 · Personajes

- **Héroe: Suertecillo.** Es la mascota de la marca: un trébol de cuatro hojas pequeño, miedoso pero muy listo, con zapatillas rojas. El trébol representa la suerte y el verde de la marca. Cuando planea con sus hojas convertidas en hélice, muestra que es ingenioso.
- **Villano: Don Chistera.** Es un duende cazatréboles con chistera verde y un trébol robado. Representa el problema que resuelve la marca: **pagar de más**. Se queda con el oro (el descuento) y el cliente se lo quita jugando.
- Los dos personajes son **dibujos a mano de Jano, digitalizados** y animados en el juego.

## Diapositiva 3 · Recorrido del cliente

1. **Lo descubre:** ve la publicación de Instagram o recibe el email de la campaña.
2. **Hace clic:** pulsa "Enlace en la bio" o el botón "¡Jugar mi partida!" del email. Los enlaces llevan una etiqueta (`utm_source`) para saber de qué canal viene.
3. **Llega a la landing:** confirma que es mayor de 18 años y ve cómo funciona el juego.
4. **Se registra:** escribe nombre y email (el teléfono es opcional), acepta la política de privacidad y, si quiere, acepta también recibir ofertas. **Sin registro no se puede jugar.**
5. **Juega su única partida:** cada moneda suma un 1 %, hasta el 15 %. Con un golpe se acaba.
6. **Recibe el código:** le sale en pantalla y además le llega por email, gracias a una automatización de MailerLite.
7. **Compra:** usa el código en la tienda. Es de un solo uso por cliente.
8. **Vuelve:** si aceptó recibir ofertas, le llegan nuevas campañas. Si vuelve a la landing, ve su código, pero no puede volver a jugar.

**Llamada a la acción en cada canal:**

| Canal | Mensaje | Llamada a la acción |
|---|---|---|
| Instagram | "Róbale el descuento al duende: hasta -15 %" | "Enlace en la bio" |
| Email | Mismo titular, con los 3 pasos | Botón "¡Jugar mi partida!" |
| Landing | "Paso 1: regístrate para jugar" | "Registrarme y jugar" → "Empezar mi partida" |

## Diapositiva 4 · Datos y RGPD

**Qué datos se piden y por qué** (minimización: solo lo necesario):

| Dato | Obligatorio | Para qué |
|---|---|---|
| Nombre | Sí | Personalizar el email del código |
| Email | Sí | Identificar la partida y enviar el código |
| Teléfono | No | Contacto opcional |
| Resultado y código | Automático | Saber qué descuento ganó |
| Origen (email, Instagram…) | Automático | Medir qué canal funciona |

**Cómo se cumple el RGPD:**

- **Dos casillas separadas y sin marcar:**
  - Una obligatoria para aceptar la política de privacidad, porque sin ella no se puede gestionar la partida.
  - Otra opcional para recibir ofertas. El consentimiento comercial no se puede exigir para jugar.
- **Información en el formulario:** debajo aparece la información básica (responsable, finalidad y cómo ejercer los derechos), con enlace a la **política de privacidad completa** (`privacidad.html`). Esa política explica la legitimación (consentimiento), el encargado (MailerLite, en la UE), cuánto tiempo se guardan los datos y los derechos, incluida la opción de reclamar ante la AEPD.
- **Solo mayores de 18 años:** hay un aviso de edad al entrar.
- **Baja en cada email:** todos los correos tienen enlace para darse de baja.
- **Uso de los datos:** las campañas comerciales solo se mandan a quien tenga `acepta_comercial = si`.

**Dónde se guarda el registro:** la landing está en GitHub Pages y envía los datos a **MailerLite**:

- Al registrarse, el jugador entra en el grupo **"Oro Verde · Jugadores registrados"** con `partida = registrada`.
- Al terminar, pasa al grupo **"Oro Verde · Partida terminada"** con `partida = terminada`, `descuento` y `codigo`.

**Cómo se controla que cada persona juegue una sola vez:**

1. **Registro obligatorio:** sin email no hay partida, así que cada jugador queda identificado en MailerLite.
2. **Un código por email:** la automatización que envía el código se activa una sola vez por suscriptor. Si alguien repite con el mismo email, no recibe otro.
3. **Bloqueo en el navegador:** se guarda en el navegador que ya jugó, así que al recargar ve su resultado y no puede volver a jugar.
4. **En la tienda:** cada código es de un solo uso por cliente, y la tienda puede comprobar en MailerLite si el email del pedido es de un jugador registrado.
- **Límite reconocido:** quien use otro email y otro navegador podría volver a jugar. Para evitarlo del todo haría falta un servidor propio que valide la partida antes de empezar. Se acepta este riesgo porque el descuento es bajo y cada nuevo email también es un contacto nuevo.

## Diapositiva 5 · Medición

| Qué medir | Dónde | Indicador |
|---|---|---|
| Alcance e interacción | Instagram (estadísticas) | Alcance, me gusta, guardados, clics en el enlace de la bio |
| Respuesta al email | MailerLite (informe de campaña) | Tasa de apertura, tasa de clics |
| Captación | Grupo "Jugadores registrados" | Nº de registros; % que acepta ofertas |
| Participación | Grupo "Partida terminada" | Nº de partidas; descuento medio |
| Canal que más aporta | Campo `origen` en MailerLite | Registros por canal (instagram / mailerlite / directo) |
| Ventas | Tienda | Nº de pedidos con códigos `VERDE01`… `VERDE15`, importe medio |

**Fórmulas clave:**
- Conversión de la landing = registros ÷ visitas.
- Canje = pedidos con código ÷ partidas terminadas.

## Diapositiva 6 · Entregables

- **Dibujos digitalizados:** Suertecillo y Don Chistera.
- **Landing con juego, registro con consentimiento y cupón:** https://jnnddzzz.github.io/oroverde/
- **Política de privacidad:** https://jnnddzzz.github.io/oroverde/privacidad.html
- **Email de campaña (MailerLite):** imagen y botón que llevan a la landing. El juego no se juega dentro del correo.
- **Email automático con el código:** se envía al terminar la partida.
- **Publicación de Instagram:** imagen y "enlace en la bio" a la landing (ver `instagram-brief.md`).
