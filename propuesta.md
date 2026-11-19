# Sistema web de gestión de contactos, visitas y publicaciones para Sharaon Garcia

**Propuesta de Proyecto Integrador**
Programa Académico Desconcentrado "Técnico Superior en Informática"
UMSA · Sede Colquencha

Autor: Victor Hugo Huanca I.
Fecha: noviembre de 2026

---

## Resumen

Sharaon Garcia es una agente inmobiliaria independiente en La Paz. Actualmente
atiende consultas por WhatsApp y registra contactos y citas en hojas sueltas o
en un cuaderno. El sitio web desarrollado en Programación Web presenta
propiedades y prepara solicitudes de visita para enviarlas por WhatsApp, pero
no conserva esas solicitudes ni cuenta con herramientas para gestionar el
trabajo diario de la agente.

El proyecto propone ampliar el sitio existente con un backend en PHP y una
base de datos MySQL para consultar el catálogo y gestionar solicitudes de
visita, contactos, seguimientos, citas y publicaciones planificadas. El acceso
al espacio de gestión se protegerá y se documentará un procedimiento de
respaldo. La prioridad de las funciones, las condiciones de uso y la
factibilidad del despliegue se validarán mediante una entrevista formal antes
de cerrar los requerimientos. El sistema se verificará con casos de prueba y
pruebas de uso móvil.

## Introducción

Este documento presenta el proyecto integrador del módulo Proyecto de
Software del Programa Académico Desconcentrado "Técnico Superior en
Informática" de la UMSA, Sede Colquencha. El trabajo continúa el sitio web
construido para Sharaon Garcia en el módulo de Programación Web y aborda la
falta de un registro centralizado para sus contactos, solicitudes de visita y
actividades.

La propuesta describe el contexto del cliente, el problema identificado, los
objetivos, la justificación, la factibilidad, el alcance y el cronograma. La
entrevista formal todavía está pendiente; por ello, las necesidades y
condiciones que aún no se han confirmado se presentan como aspectos por
validar, no como resultados comprobados. El análisis y la construcción
posteriores definirán los requerimientos, el modelo de datos, la
implementación, las pruebas y, si se confirma su viabilidad, el despliegue.

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

Ampliar el sitio web existente con un backend y una base de datos para que
Sharaon Garcia gestione contactos, visitas y publicaciones desde su celular.

### Objetivos específicos

1. Diseñar una base de datos relacional para las propiedades, zonas, pedidos
   de visita, contactos, tareas, citas y publicaciones planificadas.
2. Conectar el catálogo existente al backend, preservando sus funciones, y
   registrar los pedidos de visita para su consulta por la agente.
3. Implementar la gestión de contactos, seguimientos, citas y publicaciones
   planificadas en vistas adaptadas al uso móvil.
4. Proteger el acceso y respaldar los datos; verificar los flujos principales,
   los casos de error y la visualización móvil mediante pruebas.

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

## Cronograma de actividades

### Descomposición del trabajo

```
1. Propuesta y validación
   1.1 Revisar el sitio existente y la memoria del proyecto
   1.2 Entrevistar a la cliente y validar el problema
   1.3 Priorizar requisitos y delimitar el alcance

2. Análisis y diseño
   2.1 Documentar requisitos funcionales y no funcionales
   2.2 Diseñar la base de datos y las vistas de gestión
   2.3 Definir casos de prueba y criterios de aceptación

3. Construcción
   3.1 Migrar propiedades y zonas desde datos.json a MySQL
   3.2 Implementar el backend y conectar el catálogo existente
   3.3 Implementar solicitudes de visita, contactos, actividades y publicaciones
   3.4 Proteger el acceso al espacio de gestión

4. Verificación y cierre
   4.1 Ejecutar pruebas funcionales, de errores y de uso móvil
   4.2 Documentar el respaldo y corregir los hallazgos
   4.3 Preparar la documentación y evaluar el despliegue
```

### Cronograma (4 semanas, 20 clases)

| Semana | Actividades |
|---|---|
| 1 | Entrevista formal; validación del problema, requisitos y datos; revisión del sitio existente; diseño de la base de datos y de las vistas móviles. **Entregable:** requisitos priorizados y diseño inicial. |
| 2 | Implementación del backend; migración de propiedades y zonas; consulta del catálogo desde MySQL y pruebas de regresión de las funciones existentes. **Entregable:** catálogo conectado a la base de datos. |
| 3 | Registro de solicitudes de visita; gestión de contactos, seguimientos y citas; implementación del planificador de publicaciones. **Entregable:** flujos principales implementados. |
| 4 | Protección del espacio de gestión; respaldo; matriz de pruebas y validación móvil con la cliente; correcciones, documentación y despliegue si se confirma su factibilidad. **Entregable:** sistema probado y documentación final. |

---

**Aspectos pendientes de validación.** La entrevista formal con la cliente debe
confirmar las tareas prioritarias, el proceso actual, los datos necesarios y
las condiciones de uso. Los costos son estimaciones preliminares y la
factibilidad del despliegue depende de verificar un proveedor compatible. No se
presentan cifras de operación ni resultados de observación que todavía no se
hayan recopilado.