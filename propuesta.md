# Sistema web de gestión de contactos, visitas y publicaciones para Sharaon Garcia

**Propuesta de Proyecto Integrador**
Programa Académico Desconcentrado "Técnico Superior en Informática"
UMSA · Sede Colquencha

Autor: Victor Hugo Huanca I.
Fecha: noviembre de 2026

---

## Tipo de proyecto

**Proyecto integrador.** Se resuelve un problema concreto de un cliente real
construyendo un producto de software funcional, acompañado de la documentación
de ingeniería que respalda las decisiones tomadas.

No es una monografía: no se estudia el estado del arte de los CRM, se construye
uno. No es una investigación: no se responde una pregunta abierta, se resuelve
un problema conocido. Tampoco es un proyecto de grado: no se exige aporte
original ni defensa ante tribunal; este módulo es preparación para esa etapa.

---

## El punto de partida

Este proyecto continúa el sitio construido en Programación Web. Ya existe un
sitio público funcional de tres páginas: Inicio, Propiedades y Agenda una
visita. Incluye un catálogo con búsqueda, filtros, orden, favoritas y
comparación; el formulario de visita valida los datos y prepara un mensaje para
WhatsApp. La información de ejemplo está en `datos.json`; las propiedades se
cambian editando ese archivo, y el pedido de visita todavía no se guarda en el
sistema. La memoria del proyecto no confirma que el sitio esté publicado.

El trabajo de este módulo extiende ese producto con persistencia y herramientas
para la gestión diaria de la agente:

| Ya existe | Se construye este módulo |
|---|---|
| sitio público funcional, adaptable a pantallas desde 320 px | backend en PHP y base de datos MySQL |
| catálogo y zonas en `datos.json` | migración de propiedades y zonas a la base de datos |
| formulario que prepara un pedido para WhatsApp | registro del pedido de visita para su seguimiento |
| no hay un espacio de gestión para la agente | gestión de contactos, tareas, citas y publicaciones planificadas |
| funciones del sitio implementadas en Programación Web | requerimientos, matriz de pruebas, respaldo y despliegue, si la factibilidad se confirma |

---

## El cliente

**Sharaon Garcia**, agente inmobiliaria independiente en la ciudad de La Paz.
Consigue sus propios clientes, muestra propiedades y las promociona en
Facebook y TikTok.

**Cómo trabaja hoy:** responde consultas por WhatsApp y anota contactos y citas
en hojas sueltas o en un cuaderno. El sitio público presenta propiedades y
prepara pedidos de visita para enviar por WhatsApp, pero no conserva esos
pedidos. No existe en el sitio un espacio para que la agente centralice sus
contactos, seguimientos, citas y publicaciones.

**Fuente de esta información:** conversaciones iniciales con la cliente en
noviembre de 2026 y la memoria del sitio elaborado en Programación Web. La
frecuencia de las actividades, la cantidad de contactos y citas, las pérdidas
que pudiera haber y cualquier otro dato cuantitativo siguen pendientes de
validación en una entrevista formal. La relación laboral o comercial con una
franquicia también debe confirmarse antes de incluirla en el documento.

---

## Formulación del problema

Sharaon Garcia registra contactos y citas en hojas sueltas o en un cuaderno y
atiende consultas por WhatsApp. El sitio construido en Programación Web ayuda
a quienes buscan propiedades, pero no conserva las solicitudes de visita ni
ofrece a la agente un registro centralizado de contactos y actividades. La
planificación de publicaciones también queda fuera del sitio.

Con la información disponible se identifica una necesidad de centralización,
no una cantidad comprobada de pérdidas. La entrevista formal deberá confirmar
cómo se registran actualmente las consultas, los seguimientos y las citas,
cómo se organiza la promoción, y cuáles de esas dificultades son prioritarias
para la cliente.

### Árbol de problemas

```
   EFECTOS      Riesgo de perder el historial de consultas y seguimientos
                Dificultad para consultar las citas y actividades pendientes
                Falta de una vista central de publicaciones planificadas
                          ↑
   PROBLEMA     La agente no cuenta con un registro digital centralizado para
   CENTRAL      gestionar contactos, pedidos de visita y actividades
                          ↑
   CAUSAS       Los contactos y citas se anotan en hojas sueltas o en un cuaderno
                El sitio público prepara los pedidos de visita para WhatsApp,
                pero no los almacena
                El sitio no incluye herramientas para organizar seguimientos
                ni planificar publicaciones
```

### Problema central

> La agente inmobiliaria Sharaon Garcia no cuenta con un sistema digital
> centralizado para registrar y consultar sus contactos, pedidos de visita y
> actividades de seguimiento y promoción; la información disponible se
> distribuye entre anotaciones en papel, WhatsApp y un sitio público que no
> almacena los pedidos.

---

## Objetivos

### Objetivo general

Ampliar el sitio web construido en Programación Web con un backend y una base
de datos que permitan a la agente inmobiliaria Sharaon Garcia consultar el
catálogo existente y gestionar, desde su teléfono celular, los pedidos de
visita, contactos, seguimientos, citas y publicaciones planificadas.

### Objetivos específicos

1. Diseñar una base de datos relacional que incluya las propiedades y zonas
   existentes, además de pedidos de visita, contactos, tareas, citas y
   publicaciones planificadas.
2. Sustituir la lectura del catálogo desde `datos.json` por consultas al
   backend, preservando las funciones actuales de búsqueda, filtros y
   presentación de propiedades.
3. Registrar los pedidos de visita y permitir a la agente consultar y dar
   seguimiento a contactos y actividades.
4. Implementar una vista de actividades y citas por fecha, y un planificador de
   publicaciones con fecha, red social y estado.
5. Proteger el acceso al espacio de gestión y respaldar los datos registrados.
6. Verificar el sistema mediante casos de prueba para sus flujos principales,
   errores y visualización móvil.

---

## Justificación

**Práctica.** La propuesta extiende una página pública que ya permite consultar
propiedades y preparar pedidos de visita. Al persistir esos pedidos y ofrecer
un espacio de gestión, la agente podrá consultar en un solo sistema los
contactos y actividades que registre. El proyecto no presupone que hoy se
pierdan citas ni promete que el sistema aumentará las ventas; esos resultados
y la prioridad de las funciones se validarán con la cliente.

**Técnica.** Se mantiene el formato web del producto existente, que ya se
adapta a pantallas desde 320 px. Se propone PHP y MySQL para guardar los datos
que hoy están en JSON o no se guardan; la compatibilidad con el hosting, el
acceso protegido al panel y el uso desde el teléfono se comprobarán antes del
despliegue. No se requiere una aplicación nativa.

**Social.** Un registro consultable puede facilitar la organización del trabajo
de la agente y la atención de las personas interesadas. El beneficio para la
agente, sus clientes y los propietarios dependerá de que las funciones
respondan a sus necesidades reales y se incorporen a su rutina.

---

## Factibilidad

**Técnica.** El frontend ya está construido y usa HTML, CSS, JavaScript,
jQuery 3.7.1 y `datos.json`; el sitio funciona sin depender de un CDN. Se
propone desarrollar y probar el backend con PHP y MySQL en un entorno local
(por ejemplo, XAMPP), y verificar en ese entorno la migración de datos y los
flujos que ya existen. El despliegue dependerá de confirmar un hosting
compatible. El sitio actual no equivale todavía a un sistema con persistencia:
las propiedades se actualizan editando el JSON, y el pedido de visita no se
guarda.

**Operativa.** El sistema se diseña para la agente y para el uso desde un
teléfono. Antes de cerrar las pantallas y el flujo diario, se validarán con
ella las tareas prioritarias y su disposición a registrar los datos. El tiempo
de registro y la facilidad de uso se medirán con pruebas, no se darán por
supuestos.

*Riesgos identificados:* que el sistema no se adapte al uso real de la agente,
que el flujo móvil resulte lento o que los datos de contacto queden expuestos.
Se mitigarán validando los requisitos con la cliente, probando las pantallas en
un teléfono y limitando el acceso al espacio de gestión. El umbral de tiempo
aceptable para registrar una actividad se acordará con ella durante la
validación.

**Económica.** El desarrollo se realiza como parte del módulo, sin costo para
la cliente. La operación anual estimada es:

| Concepto | Costo anual (Bs) |
|---|---|
| Hosting compartido compatible con PHP y MySQL | 350 |
| Dominio | 250 |
| **Total** | **600** |

Estos montos son estimaciones preliminares, no cotizaciones. Se confirmarán
con proveedores antes de recomendar el despliegue. No se calcula retorno de
inversión mientras no haya datos validados para estimarlo.

---

## Alcances y límites

### Alcance

El sistema entregado incluye, sujeto a validar los requisitos con la cliente:

- el catálogo público y las zonas cargados desde MySQL en lugar de `datos.json`
- registro de pedidos de visita enviados desde el sitio, para su consulta por
  la agente
- gestión de contactos y tareas de seguimiento con fecha y estado
- consulta de citas y actividades por día
- planificador de publicaciones para Facebook o TikTok, con fecha y estado;
  la publicación se realiza manualmente
- acceso protegido al espacio de gestión y procedimiento de respaldo de la base
  de datos
- diseño responsive comprobado en un teléfono móvil

### Límites

El sistema **no** incluye, y en cada caso se indica por qué:

- **Publicación automática en redes sociales.** El sistema solo genera
  recordatorios de publicación; la publicación la hace la cliente. La
  publicación automática requiere integración con las APIs de Facebook y
  TikTok, que excede el alcance del módulo.
- **Gestión de contratos ni cobranzas.** La necesidad identificada se centra
  en organizar contactos y actividades, no en la parte legal o financiera de
  las operaciones inmobiliarias.
- **Múltiples usuarios ni roles.** El sistema es de uso personal de una sola
  agente; incluir roles multiplicaría el diseño sin atacar el problema
  central.
- **Aplicación nativa para celular.** Una aplicación web responsive cubre la
  necesidad de consulta desde el teléfono sin desarrollo nativo ni tiendas de
  aplicaciones.
- **Alta y edición de propiedades desde un panel administrativo.** La primera
  versión migrará el catálogo existente a MySQL; la necesidad de administrar
  propiedades desde una interfaz se validará y, si excede el tiempo disponible,
  quedará para una versión posterior.

---

## Cronograma (4 semanas, 20 clases)

| Semana | Actividades |
|---|---|
| 1 | Entrevista formal; validación del problema, requisitos y datos; revisión del sitio existente; diseño de la base de datos y de las vistas móviles |
| 2 | Implementación del backend; migración de propiedades y zonas; consulta del catálogo desde MySQL y pruebas de regresión de las funciones existentes |
| 3 | Registro de pedidos de visita; gestión de contactos, seguimientos y citas; implementación del planificador de publicaciones |
| 4 | Protección del espacio de gestión; respaldo; matriz de pruebas y validación móvil con la cliente; correcciones, documentación y despliegue si se confirma su factibilidad |

---

*(Documento en construcción: la entrevista formal con la cliente está pendiente. Las cifras de operación, los costos, la prioridad de los requisitos y la factibilidad del despliegue deben validarse antes de cerrar la propuesta.)*