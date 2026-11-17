# MEMORIA del proyecto: lo construido en Programación Web

**Cómo se usa este archivo.** Se copia a la carpeta del proyecto de Proyecto de Software. Ahí sirve de
contexto: para quien escribe el documento, que no tiene que recordar de memoria qué se hizo en el
módulo anterior, y para el asistente de IA del editor, que lo lee antes de ayudar. Se actualiza cada
vez que el proyecto cambia algo importante.

## El cliente

- **Quién es:** Sharaon Garcia, agente inmobiliaria independiente en La Paz. Consigue sus propios
  clientes, muestra las propiedades y las promociona en Facebook y TikTok.
- **Qué hace hoy:** publica cada propiedad en redes sociales y responde las consultas por WhatsApp,
  una por una. Anota contactos y citas en hojas sueltas o en un cuaderno.
- **Cómo se sabe:** conversaciones con la cliente en noviembre de 2026. Los números son estimaciones
  suyas, todavía sin validar.

## Lo que se construyó en Programación Web

Un sitio web público de tres páginas para quien busca una propiedad:

| Página | Qué hace |
|---|---|
| Inicio (`index.html`) | presenta a la agente, muestra tres propiedades destacadas y responde preguntas frecuentes |
| Propiedades (`propiedades.html`) | catálogo con buscador, filtros por operación y tipo, orden, favoritas, orden por cercanía y comparador de hasta tres propiedades |
| Agenda una visita (`contacto.html`) | formulario validado que arma el pedido de visita y lo deja listo para enviar por WhatsApp |

Tecnologías: HTML, CSS y JavaScript sin frameworks, jQuery 3.7.1 en la carpeta del proyecto, y las
APIs del navegador Geolocation, Drag & Drop, Canvas, `localStorage` y `sessionStorage`. Funciona
sin internet y se ve bien desde 320 px de ancho.

## Los datos

Viven en `datos.json` y se cargan con `fetch`. Todo es de ejemplo.

**`agente`**: un solo objeto.

| Campo | Tipo | Ejemplo |
|---|---|---|
| `nombre` | texto | "Sharaon Garcia" |
| `profesion` | texto | "Agente inmobiliaria" |
| `ciudad` | texto | "La Paz" |
| `whatsapp` | texto de 8 dígitos | "70000000" |
| `horario` | texto | "Lunes a sábado, de 9:00 a 19:00" |

**`zonas`**: un objeto por zona, con su nombre como clave y sus coordenadas aproximadas.

| Campo | Tipo | Ejemplo |
|---|---|---|
| clave | texto | "Sopocachi" |
| `lat` | número decimal | -16.5105 |
| `lon` | número decimal | -68.1265 |

**`propiedades`**: 9 propiedades.

| Campo | Tipo | Valores |
|---|---|---|
| `id` | entero | 1 a 9 |
| `titulo` | texto | "Casa con jardín" |
| `tipo` | texto | casa, departamento, terreno u oficina |
| `operacion` | texto | venta, alquiler o anticrético |
| `zona` | texto | el nombre de una de las `zonas` |
| `precio` | número | 210000 |
| `moneda` | texto | USD en venta y anticrético; Bs en alquiler, por mes |
| `dormitorios`, `banos` | entero | 0 en terrenos y oficinas |
| `superficie` | entero, en m² | 280 |
| `estado` | texto | disponible o reservada |
| `destacada` | sí o no | aparece en la portada |
| `imagen` | ruta | "img/casa.svg" |
| `descripcion` | texto | una o dos frases |

## Dónde se guarda cada cosa

| Qué | Dónde | Hasta cuándo |
|---|---|---|
| las propiedades | `datos.json` | se cambian editando el archivo a mano |
| favoritas, filtros y tema | `localStorage` del navegador | hasta que se borren los datos del navegador; solo en ese navegador |
| la comparación | `sessionStorage` | hasta cerrar la pestaña |
| el pedido de visita | **en ningún lado** | se arma el mensaje y se envía por WhatsApp; la agente lo anota a mano |

## Decisiones y por qué

- **El pedido va por WhatsApp.** La página no tiene dónde guardar un pedido, y la agente ya atiende
  por WhatsApp. Es una solución honesta para un sitio sin servidor.
- **El precio se ordena dentro de cada operación.** Un alquiler en Bs al mes y una venta en USD no
  se comparan.
- **Arrastrar tiene un botón de reemplazo.** Drag & Drop no funciona con el dedo, y la mayoría de
  las visitas llegan desde el celular.
- **La distancia es por zona**, en línea recta, no por dirección exacta: la dirección de una
  propiedad no se publica.

## Lo que el sitio no hace

- No guarda los pedidos de visita.
- No permite agregar ni editar propiedades sin tocar `datos.json`.
- No guarda nada en un servidor: las favoritas se pierden al cambiar de celular.
- Es solo para quien busca una propiedad. La agente no tiene una parte propia para su trabajo
  diario: contactos, seguimiento, citas y publicaciones.

## Lo que sigue en Proyecto de Software

- El problema que se formula en este módulo es el del trabajo diario de la agente. Los contactos,
  las citas y las publicaciones no están registrados en ningún lugar centralizado. Ver
  `propuesta.md`.
- Los datos pasan de `datos.json` a una base de datos MySQL. `propiedades` y `zonas` ya tienen la
  forma de una tabla, y `zona` es la candidata a clave foránea.
- El pedido de visita, que hoy no se guarda, es la primera fila que llega a la base.
- `fetch("datos.json")` pasa a pedir los datos a un backend en PHP, sin cambiar la forma de pintar
  las tarjetas.
