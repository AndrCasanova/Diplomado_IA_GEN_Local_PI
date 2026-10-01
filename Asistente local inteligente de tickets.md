# Asistente local inteligente para la gestión de tickets de parqueaderos y plataforma web de pagos en línea

Sep 30, 2026 · @casanova

## Portada

**Corporación Universitaria Comfacauca — Unicomfacauca**

**Diplomado en Inteligencia Artificial Generativa Local, Agentes Autónomos y Sistemas Multimodales**

**Proyecto integrador IA 5.0 Lab**

**Título provisional:** Asistente local inteligente para la gestión de tickets de parqueaderos y plataforma web de pagos en línea para establecimientos de parqueo en Popayán

**Módulo 1:** Fundamentos, soberanía tecnológica y gobernanza de IA

**Tipo de documento:** Planteamiento inicial del proyecto integrador

**Autor:** \[campo editable\]

**Docente o director:** \[campo editable\]

**Ciudad:** Popayán, Cauca

**Fecha:** septiembre de 2026

## Resumen

Los establecimientos de parqueo urbanos administran ingresos, salidas, tickets, tarifas, cobros y novedades mediante procesos que, según la información disponible, pueden ser manuales o poco integrados. Esta situación puede ocasionar demoras en los puntos de pago, errores de registro, dificultades para validar pagos y conciliar el cierre de turno, y dependencia de la experiencia individual del operario. El presente documento formula, en la fase correspondiente al Módulo 1 del diplomado, un proyecto integrador orientado a diseñar una solución local-first compuesta por un núcleo de gestión de tickets, una página web de consulta y pago en línea y un asistente local basado en inteligencia artificial generativa. Los usuarios principales son los operarios, cajeros y administradores del establecimiento de parqueo objeto de estudio, así como los conductores que consultan y pagan sus tickets. La formulación caracteriza el caso de uso, identifica actores, clasifica los datos, describe un flujo preliminar de información, delimita alcance y exclusiones, define requisitos iniciales y criterios de éxito, y construye una matriz inicial de riesgos basada en el NIST AI Risk Management Framework. Se otorga prioridad a la seguridad, la trazabilidad, la privacidad y la supervisión humana. La inteligencia artificial se limita a funciones de consulta de procedimientos, orientación y apoyo documental: no autorizará pagos, no modificará tarifas, no abrirá barreras ni permitirá la salida de vehículos de manera autónoma. Toda integración de pagos reales queda sujeta a validación técnica, contractual, financiera, legal y de seguridad.

**Palabras clave:** arquitectura local-first; gestión de tickets de parqueaderos; pagos en línea; inteligencia artificial generativa local; gobernanza de IA; NIST AI RMF; trazabilidad.

### Convenciones de lectura

Para diferenciar de forma visible la naturaleza de cada afirmación, el documento emplea las siguientes etiquetas:

| Etiqueta | Significado | Uso en el documento |
| --- | --- | --- |
| \[HP\] Hecho proporcionado | Información suministrada en la descripción inicial del proyecto | Título, alcance general, restricciones a la IA, componentes previstos |
| \[SUP\] Supuesto de trabajo | Condición que se asume para avanzar y que debe confirmarse | Disponibilidad de establecimiento, datos sintéticos, entorno local |
| \[PA\] Propuesta de arquitectura | Decisión de diseño planteada por el equipo, aún no implementada | Componentes, módulos, separación de servicios |
| \[RPV\] Requisito por validar | Requisito cuya pertinencia depende de usuarios, propietarios o terceros | Pasarela de pagos, notificaciones, OCR, barreras |
| \[RI\] Riesgo identificado | Evento potencial con efectos negativos registrado en la matriz | Capítulo 10 y referencias cruzadas |
| \[DIP\] Decisión institucional pendiente | Asunto que debe decidir el establecimiento, la institución o un asesor | Retención, proveedor de pagos, políticas de tarifas |

## 1. Introducción

La operación de un parqueadero de atención al público combina actividades de control físico, registro de información y manejo de dinero. Cada vehículo que ingresa genera un ticket, una hora de entrada, una tarifa aplicable, un cobro y, eventualmente, una novedad. Cuando estas actividades se registran de forma manual o en herramientas desconectadas entre sí, la información puede quedar dispersa, la validación de pagos puede depender del criterio individual del operario y el cierre de turno puede requerir reconstrucciones manuales. La digitalización de estos procesos se plantea, por tanto, como una vía para estandarizar registros y mejorar la trazabilidad, entendida como la capacidad de reconstruir quién hizo qué, cuándo y sobre qué registro.

El control conjunto de tickets, tarifas, ingresos, salidas, pagos y novedades constituye el núcleo del problema. Un ticket sin relación verificable con su pago, una tarifa aplicada sin una regla documentada o una novedad resuelta sin registro dificultan la conciliación operativa y la rendición de cuentas. En ese contexto, una página web de consulta y pago en línea podría ofrecer a los conductores una alternativa al pago presencial y reducir la congestión en los puntos de cobro, hipótesis que debe verificarse con el establecimiento y con los usuarios. Esta línea es coherente con la problemática que el autor ha identificado previamente en su trabajo académico: la demora en los puntos de pago de parqueaderos en Popayán, cuyo levantamiento de evidencia mediante encuesta se encuentra pendiente de aplicación.

El proyecto adopta un enfoque local-first. Una arquitectura local-first es aquella en la que los datos y el procesamiento principal residen en infraestructura controlada por la organización, de modo que las funciones esenciales pueden operar sin depender permanentemente de servicios externos. Este enfoque busca preservar la continuidad operativa ante fallas de conectividad, mantener el control sobre la información y reducir la dependencia de terceros. No implica ausencia total de servicios externos: el pago en línea, por su naturaleza, requiere conexión con un proveedor de pagos autorizado, integración que queda sujeta a validación técnica, contractual y de seguridad.

La inteligencia artificial generativa cumple un papel deliberadamente limitado. Se propone un asistente basado en un modelo de lenguaje ejecutado localmente que apoye al operario en la consulta de procedimientos, reglamentos y tarifas autorizadas, en la redacción de resúmenes de novedades y en tareas documentales. Para ello puede emplearse RAG (*Retrieval-Augmented Generation*, generación aumentada por recuperación), técnica en la que el modelo responde con base en fragmentos recuperados de una colección documental controlada. El asistente no tendrá autoridad para autorizar pagos, modificar tarifas, alterar estados, abrir barreras ni permitir salidas de vehículos.

Este documento corresponde a la fase de formulación del Módulo 1, *Fundamentos, soberanía tecnológica y gobernanza de IA*. Su propósito es caracterizar el caso de uso, delimitar el alcance y establecer requisitos, criterios de éxito y riesgos iniciales que orienten las fases posteriores de diseño, construcción, evaluación y sustentación. No describe una solución desplegada, no reporta resultados medidos y no corresponde a un sistema validado en producción.

## 2. Planteamiento del problema

### 2.1 Contexto del problema

Un parqueadero urbano de atención al público en Popayán recibe vehículos de distinto tipo, los resguarda durante un tiempo variable y cobra un valor determinado por reglas tarifarias. Este documento no describe un establecimiento particular: el establecimiento de parqueo objeto de estudio y su operación concreta están \[por validar en el levantamiento de requisitos\]. Los procesos que se enumeran a continuación constituyen una referencia de análisis construida a partir de la operación típica del servicio y deben confirmarse con el propietario o administrador.

| Proceso de referencia | Descripción general | Aspecto por validar |
| --- | --- | --- |
| Registro de entrada | El operario registra el vehículo al ingresar | Datos registrados, medio de registro y responsable |
| Emisión de ticket | Se entrega un ticket físico o digital que identifica la estancia | Formato, contenido y numeración del ticket |
| Registro de hora de ingreso y salida | Se anota la hora de entrada y, al salir, la de salida | Fuente de la hora, precisión y posibilidad de corrección |
| Consulta de tarifas | Se determina la tarifa según tipo de vehículo, tiempo u otras reglas | Reglas vigentes, fracciones, tarifas especiales y responsables |
| Cobro presencial o digital | Se recibe el pago por los medios aceptados | Medios aceptados y existencia de cobro digital |
| Validación de pago | Se verifica que el ticket esté pago antes de la salida | Quién valida y con qué evidencia |
| Resolución de novedades | Se atienden ticket perdido, inconsistencia horaria, salida no registrada o pago pendiente | Procedimiento vigente y nivel de autorización requerido |
| Registro de eventos | Se documentan acciones relevantes del turno | Existencia y formato del registro |
| Cierre de turno | Se totalizan cobros y tickets del turno | Procedimiento, responsables y soportes |
| Conciliación operativa | Se contrastan tickets, cobros y dinero recibido | Periodicidad, herramientas y diferencias aceptadas |

### 2.2 Situación problemática

Según la información disponible \[HP\], los parqueaderos pueden enfrentar procesos manuales o poco integrados para registrar tickets, controlar pagos, consultar tarifas, resolver novedades y verificar salidas. El análisis causal parte de esa descripción y plantea relaciones que deben validarse con evidencia; ninguna de ellas se presenta como hecho demostrado.

El registro manual o fragmentado puede generar errores al anotar la hora de entrada o salida, pérdida o duplicidad de tickets y dificultad para recuperar información histórica. Cuando el cálculo de tarifas depende de la memoria del operario o de tablas no actualizadas, podrían producirse cobros inconsistentes entre turnos. Si el pago no queda vinculado al ticket de forma verificable, la validación previa a la salida se vuelve más lenta y más propensa a error, lo cual podría contribuir a demoras en la atención, en especial en los momentos de mayor afluencia.

Las novedades representan un foco particular de riesgo potencial. La pérdida de un ticket, una inconsistencia en horarios, una salida no registrada o un pago pendiente exigen decisiones que, sin un procedimiento documentado, dependen de la experiencia individual de cada operario. La falta de registro de estas decisiones limita la trazabilidad y dificulta el cierre de turno y la conciliación.

La incorporación de pagos en línea introduce riesgos adicionales: confirmaciones de pago incorrectas o falsificadas, exposición de identificadores de transacción, dependencia de una plataforma externa e interrupciones por conectividad limitada. A ello se suma el riesgo de acceso no autorizado a información operativa o financiera cuando no existen controles de acceso por rol. Estos efectos deben validarse mediante observación del proceso, entrevistas y el instrumento de encuesta previsto por el autor.

### 2.3 Consecuencias

| Dimensión | Impactos potenciales | Evidencia que se debe recolectar |
| --- | --- | --- |
| Operativa y de experiencia del usuario | Demoras en el punto de pago y en la salida; filas en horas de mayor afluencia; respuestas distintas ante la misma novedad; insatisfacción del conductor | Tiempos de atención observados \[métrica por definir en pruebas\]; percepción de usuarios mediante encuesta; frecuencia de novedades por turno |
| Administrativa y financiera | Diferencias entre tickets y dinero recaudado; dificultad en cierre de turno; cobros inconsistentes; reconstrucción manual de información | Procedimiento actual de cierre; registros de diferencias si existen y se autoriza su consulta; descripción de las reglas tarifarias |
| Tecnológica y de seguridad | Pérdida de registros; ausencia de respaldo; accesos sin control por rol; dependencia de conectividad y de terceros; uso no controlado de herramientas externas | Inventario de herramientas actuales; prácticas de respaldo; calidad de la conectividad \[dato por validar\]; control de accesos vigente |
| Privacidad, confianza y cumplimiento | Tratamiento de placas y datos de contacto sin finalidad definida; exposición de comprobantes; pérdida de confianza del usuario; posibles incumplimientos de obligaciones de protección de datos | Datos personales que se recolectan hoy; existencia de política de tratamiento de datos; avisos al titular; requisitos contractuales de medios de pago \[por validar con asesor\] |

### 2.4 Análisis de causas

| Causa | Manifestación en el proceso | Efecto potencial | Evidencia o dato por recolectar |
| --- | --- | --- | --- |
| Registro manual o disperso | Tickets, horas y cobros anotados en papel, hojas de cálculo o cuadernos separados | Errores de transcripción, pérdida de información, consulta histórica limitada | Medios de registro utilizados y su conservación |
| Falta de estandarización de tickets | Tickets sin numeración única o con contenido variable | Duplicidad, suplantación o dificultad para validar | Muestra de tickets reales anonimizados, si se autoriza |
| Falta de validación automática controlada | La verificación del ticket y del pago depende de inspección visual | Errores de validación y demoras | Descripción del paso de validación previo a la salida |
| Procesos de pago desconectados de los tickets | El cobro se registra aparte del ticket o no se registra | Dificultad para conciliar; pagos no asociados | Forma en que se relaciona hoy cada cobro con su ticket |
| Ausencia de trazabilidad de eventos | No queda registro de quién creó, modificó o cerró un ticket | Imposibilidad de reconstruir incidentes | Existencia de bitácoras o registros de turno |
| Falta de controles de acceso por rol | Varias personas usan la misma cuenta o equipo sin restricciones | Accesos indebidos y responsabilidad difusa | Usuarios, cuentas y permisos actuales |
| Dependencia de conectividad | Herramientas que solo funcionan con Internet | Interrupción de la operación ante fallas | Frecuencia de fallas de conectividad \[dato por validar\] |
| Insuficiente respaldo de información | Registros sin copias ni pruebas de restauración | Pérdida irreversible de datos | Prácticas de respaldo existentes |
| Falta de indicadores de operación | No se mide tiempo de atención, novedades ni diferencias | Decisiones sin evidencia | Indicadores que el administrador considera útiles |
| Ausencia de procedimientos definidos para novedades | Cada operario resuelve el ticket perdido o la inconsistencia a su criterio | Trato desigual, cobros arbitrarios, conflictos | Procedimientos escritos o verbales vigentes |
| Uso no controlado de herramientas externas | Uso de mensajería o asistentes públicos con datos operativos | Fuga de información y pérdida de control | Herramientas usadas informalmente por el personal |
| Falta de documentación de tarifas, reglas y políticas | Tarifas conocidas solo por tradición oral o carteles | Cobros inconsistentes y dificultad de capacitación | Documentos de tarifas y reglamentos disponibles |

### 2.5 Formulación del problema

Con base en el análisis anterior, se formula la siguiente pregunta central de ingeniería:

> ¿Cómo diseñar una solución local-first que integre la gestión de tickets de parqueaderos, una página web de consulta y pago en línea y un asistente local de inteligencia artificial generativa de apoyo, de manera que mejore la trazabilidad operativa y el control de novedades en establecimientos de parqueo de Popayán, bajo criterios de seguridad, privacidad y auditoría, con supervisión humana y sin delegar a la inteligencia artificial decisiones críticas sobre pagos, tarifas, barreras o salida de vehículos?

De la pregunta central se derivan preguntas orientadoras: ¿qué procesos y datos del establecimiento deben digitalizarse primero?, ¿qué funciones pueden operar localmente sin Internet?, ¿qué controles reducen los riesgos de la integración de pagos? y ¿qué tareas puede apoyar el asistente sin exceder su función de orientación?

### 2.6 Árbol de problemas

La siguiente tabla representa el árbol de problemas de forma textual, desde los efectos indirectos (parte superior) hasta las causas indirectas (parte inferior).

| Nivel | Elementos |
| --- | --- |
| Efectos indirectos | Pérdida de confianza de conductores y propietarios; decisiones administrativas sin evidencia; exposición a reclamaciones y posibles incumplimientos en protección de datos; dificultad para adoptar pagos digitales de forma segura |
| Efectos directos | Demoras en el punto de pago y en la salida; errores de registro y de cobro; dificultad en cierre de turno y conciliación; novedades resueltas sin trazabilidad; pérdida de registros |
| **Problema central** | **Gestión de tickets, tarifas, pagos y novedades poco integrada y con baja trazabilidad en el establecimiento de parqueo objeto de estudio \[por validar\]** |
| Causas directas | Registro manual o disperso; tickets no estandarizados; pagos desconectados de los tickets; ausencia de registro de eventos; procedimientos de novedades no definidos; falta de control de acceso por rol |
| Causas indirectas | Falta de documentación de tarifas y políticas; ausencia de indicadores; respaldo insuficiente; dependencia de conectividad; uso no controlado de herramientas externas; capacitación basada en la experiencia individual |

## 3. Justificación

### 3.1 Justificación operativa

Una gestión digital y trazable de tickets permitiría que cada estancia quede representada por un registro único con hora de ingreso, tarifa aplicada, estado de pago y novedades asociadas. Esta estandarización facilitaría la consulta de información durante el turno, la capacitación de nuevos operarios y la aplicación de procedimientos homogéneos ante novedades. El proyecto plantea como hipótesis verificables, y no como resultados esperados de forma automática, que: (a) el registro estructurado reduce los errores de transcripción frente al registro manual; (b) la vinculación entre ticket y pago reduce el tiempo de validación previo a la salida; y (c) la disponibilidad de procedimientos consultables mediante el asistente local disminuye la variabilidad en la resolución de novedades. Estas hipótesis se contrastarán con datos de prueba y, si se autoriza, con observación en el establecimiento \[métrica por definir en pruebas\].

### 3.2 Justificación administrativa y financiera

Relacionar tickets, tarifas, pagos y registros de auditoría en un mismo modelo de datos podría facilitar el cierre de turno, la identificación de diferencias y la conciliación operativa, entendida como el contraste interno entre tickets cerrados, valores cobrados y estados de pago. Esta conciliación operativa no equivale a la conciliación bancaria definitiva, que depende de los extractos y reportes del proveedor de pagos o de la entidad financiera. El sistema propuesto no reemplaza los procesos contables, fiscales, tributarios, bancarios ni de auditoría profesional; se limita a ofrecer información operativa trazable que estos procesos podrían utilizar, previa validación por los responsables contables del establecimiento.

### 3.3 Justificación tecnológica

| Elemento propuesto \[PA\] | Pertinencia para el proyecto |
| --- | --- |
| Arquitectura local-first | Permite que el registro de ingresos, salidas y consultas continúe ante fallas de Internet y mantiene los datos bajo control del establecimiento |
| Base de datos local o institucional controlada | Centraliza tickets, pagos, novedades y auditoría con integridad referencial y control de acceso |
| API local | Una API (*Application Programming Interface*, interfaz de programación de aplicaciones) expone las funciones del núcleo a las interfaces de forma uniforme y permite aplicar autorización en un solo punto |
| Interfaz web para operarios y administradores | Facilita el acceso desde equipos de la red local sin instalación compleja |
| Página web de pago | Ofrece al conductor una vía de consulta y pago del ticket; su exposición a Internet exige controles adicionales |
| Registro de eventos | Soporta la trazabilidad y la investigación de incidentes |
| Validación de reglas | Hace que las tarifas y los cambios de estado obedezcan reglas configuradas y verificables, no criterios ad hoc |
| Control de acceso por roles | Aplica el principio de mínimo privilegio, según el cual cada usuario recibe solo los permisos necesarios para su función |
| Copias de respaldo | Reduce el impacto de pérdida o corrupción de datos |
| Diseño modular | Permite incorporar o excluir componentes (pagos, IA, notificaciones) según su validación |
| Modelo de lenguaje local | Permite consultar procedimientos y apoyar tareas documentales sin enviar información operativa a servicios públicos |

### 3.4 Justificación de seguridad y privacidad

El sistema puede tratar información asociada a placas vehiculares, horarios de ingreso y salida, identificadores de tickets, montos cobrados, medios de contacto y comprobantes de pago. Combinados, estos datos podrían revelar patrones de desplazamiento de personas identificables, por lo cual requieren finalidad definida, minimización y control de acceso. La ejecución local puede reducir transferencias innecesarias de información a terceros; sin embargo, no elimina los riesgos de acceso interno indebido, errores de configuración, robo o daño de equipos, pérdida de datos, vulnerabilidades del software ni tratamiento indebido de la información. Por ello, la seguridad y la privacidad se abordan como requisitos de diseño desde la formulación y no como añadidos posteriores.

### 3.5 Justificación territorial

Popayán presenta, como otras ciudades intermedias colombianas, necesidades de digitalización en servicios de atención al público y en pequeños y medianos negocios. Un proyecto que proponga una solución de bajo costo de infraestructura, operable localmente y documentada de forma reproducible podría servir como referencia para establecimientos de la región. Este documento no afirma que todos los parqueaderos de la ciudad presenten los mismos problemas ni aporta cifras locales; la pertinencia territorial se validará con el establecimiento participante y con el instrumento de encuesta previsto.

### 3.6 Justificación académica

| Competencia del diplomado | Relación con el proyecto |
| --- | --- |
| IA local | Ejecución de un modelo de lenguaje en infraestructura controlada |
| RAG y bases de conocimiento | Consulta de manuales, tarifas y reglamentos autorizados con citación de fuentes |
| Agentes controlados | Eventual uso de herramientas delimitadas de solo lectura, con registro de invocaciones y aprobación humana |
| APIs y software AI-native | Integración del asistente con el núcleo mediante una API con permisos acotados |
| Seguridad | Control de acceso, gestión de secretos, protección frente a prompt injection |
| Gobernanza | Aplicación de NIST AI RMF y del perfil NIST AI 600-1; definición de responsables y límites |
| Evaluación | Criterios de éxito, pruebas funcionales y de calidad de respuestas |
| Reproducibilidad | Documentación de instalación, versiones de modelos y dependencias |
| Contexto regional | Solución aplicada a establecimientos de parqueo de Popayán |

## 4. Objetivos

### 4.1 Objetivo general

Diseñar una solución local-first para la gestión de tickets de parqueaderos, integrada con una página web de consulta y pago en línea y con un asistente local de inteligencia artificial generativa de apoyo, que contribuya a la trazabilidad operativa y al control de novedades en establecimientos de parqueo de Popayán, bajo criterios de seguridad, privacidad, auditoría y supervisión humana definidos a partir del NIST AI Risk Management Framework.

### 4.2 Objetivos específicos

1. Caracterizar el proceso actual de gestión de tickets, tarifas, pagos y novedades del establecimiento de parqueo objeto de estudio, mediante entrevistas, observación y el instrumento de encuesta previsto.
2. Identificar los actores, usuarios y partes interesadas de la solución, junto con sus necesidades, responsabilidades y niveles de acceso.
3. Clasificar los datos e información que trataría la solución según su sensibilidad y finalidad, y definir el flujo preliminar de datos con la delimitación entre procesamiento local, híbrido y remoto.
4. Establecer el alcance, las exclusiones, los requisitos funcionales y no funcionales y los límites de autonomía del asistente de inteligencia artificial.
5. Diseñar una arquitectura conceptual local-first que separe el núcleo operativo, la página de pagos, la integración con terceros y el motor local de IA.
6. Identificar y valorar los riesgos iniciales del proyecto mediante las funciones Govern, Map, Measure y Manage del NIST AI RMF, complementadas con el perfil NIST AI 600-1.
7. Proponer controles preliminares de gobernanza, privacidad, seguridad y trazabilidad para las fases de construcción y evaluación.
8. Definir criterios de éxito e indicadores que permitan evaluar preliminarmente el prototipo en fases posteriores.

## 5. Usuarios, actores y partes interesadas

Las clasificaciones empleadas son: **usuario primario** (interactúa a diario con la solución para cumplir su función), **usuario secundario** (interactúa de forma ocasional o limitada), **administrador** (configura y gestiona la solución), **titular de datos** (persona a quien se refieren los datos personales), **actor externo** (tercero fuera de la organización) y **actor de supervisión** (revisa o audita sin operar). Un mismo actor puede tener más de una clasificación. Todo acceso descrito está condicionado a rol, autorización y necesidad operativa, y debe confirmarse con el propietario o administrador \[DIP\].

| Actor o usuario | Clasificación | Rol | Necesidades principales | Nivel de acceso o interacción | Responsabilidades y riesgos |
| --- | --- | --- | --- | --- | --- |
| Conductor o cliente del parqueadero | Usuario secundario; titular de datos | Recibe el ticket, consulta su estado y paga | Pago ágil, información clara de tarifa y valor, protección de sus datos | Página web: solo su propio ticket mediante código; sin acceso a datos de otros usuarios | Custodiar su ticket; riesgo de suplantación o de consulta de tickets ajenos por enumeración de códigos |
| Operario de ingreso o salida | Usuario primario | Registra ingresos y salidas, valida tickets, registra novedades | Registro rápido, validación clara del pago, procedimientos a la mano | Crear tickets, consultar tickets activos, registrar salida tras validación, registrar novedades; consultar el asistente | Registrar con exactitud; riesgo de errores, manipulación o uso de cuenta ajena |
| Cajero o encargado de cobro, si aplica | Usuario primario | Recibe pagos presenciales y registra el estado de pago | Cálculo correcto del valor, registro del pago y cierre de turno | Registrar pagos presenciales y consultar el cierre de su turno; sin modificar tarifas | Custodia de dinero; riesgo de registro incorrecto de pagos |
| Administrador del parqueadero | Administrador; usuario primario | Supervisa la operación, autoriza novedades y consulta reportes | Visión del turno, reportes, control de novedades | Aprobar acciones sensibles, consultar reportes y auditoría operativa, gestionar tarifas según delegación del propietario | Autorizar excepciones; riesgo de concentración de permisos |
| Propietario o responsable del negocio | Actor de supervisión; decisor | Define tarifas, políticas y alcance | Control del negocio, trazabilidad y cumplimiento | Aprobación de tarifas y políticas; acceso a reportes consolidados | Responsable del tratamiento de datos \[por validar\]; decisiones institucionales pendientes |
| Personal de soporte técnico | Usuario secundario | Atiende fallas de equipos y red | Diagnóstico de errores | Registros técnicos de errores; sin acceso a datos de negocio salvo autorización puntual | Riesgo de acceso privilegiado indebido |
| Administrador del sistema | Administrador | Gestiona usuarios, roles, configuración, respaldos y modelos | Configuración segura y recuperable | Gestión de cuentas y configuración; acceso a datos de negocio solo cuando sea necesario y quede registrado | Gestión de secretos y respaldos; riesgo alto por privilegios elevados |
| Responsable de protección de datos, si existe | Actor de supervisión | Vela por el tratamiento adecuado de datos personales | Inventario de datos, finalidades, retención | Consulta de políticas, inventarios y registros de auditoría relacionados | Atender solicitudes de titulares; riesgo de incumplimiento si no se designa |
| Proveedor o pasarela de pagos | Actor externo \[RPV\] | Procesa pagos en línea | Integración conforme a sus requisitos técnicos y contractuales | Recibe solo los datos mínimos del pago; envía confirmaciones al sistema | Sujeto a evaluación técnica, contractual y de seguridad; riesgo de dependencia y de falla de integración |
| Entidad financiera | Actor externo indirecto | Liquida fondos a través del proveedor de pagos | — | Sin interacción directa con la solución | Fuera del alcance del prototipo |
| Equipo desarrollador o estudiantes | Usuario secundario | Diseña, construye y prueba el prototipo | Requisitos claros y datos de prueba | Entorno de desarrollo con datos sintéticos; sin acceso a datos reales salvo autorización expresa | Riesgo de exposición de secretos o uso indebido de datos reales |
| Auditor interno o externo, cuando se encuentre autorizado | Actor de supervisión | Revisa trazabilidad y controles | Registros íntegros y documentación | Solo lectura de auditoría y reportes, por periodo y alcance autorizados | Confidencialidad de lo revisado |

## 6. Datos y flujo de información

### 6.1 Clasificación de datos

Se proponen cuatro niveles de sensibilidad \[PA\]: **Público** (puede divulgarse sin restricción), **Interno** (uso operativo dentro del establecimiento), **Confidencial** (datos personales o comerciales cuyo acceso se limita por rol) y **Restringido** (datos cuya exposición causaría daño grave; acceso mínimo y controlado). La clasificación definitiva es una decisión institucional pendiente \[DIP\].

| Tipo de dato | Ejemplos | Nivel de sensibilidad | Finalidad | Tratamiento permitido | Controles requeridos |
| --- | --- | --- | --- | --- | --- |
| Identificador del ticket | Código único, código QR o alfanumérico | Interno | Identificar la estancia y permitir su consulta | Generar, consultar, validar, cerrar | Identificador no predecible; limitación de intentos de consulta en la web |
| Placa del vehículo | Placa registrada al ingreso | Confidencial | Asociar el vehículo con el ticket y apoyar la validación de salida | Registrar y consultar por personal autorizado; no publicar en la web completa | Acceso por rol; enmascaramiento en la página web; retención limitada; tratarla como dato potencialmente personal |
| Tipo de vehículo, si aplica | Automóvil, motocicleta, otro \[por validar\] | Interno | Determinar la tarifa | Registrar y consultar | Lista controlada de valores |
| Fecha y hora de ingreso | Marca de tiempo | Confidencial en conjunto con la placa | Calcular tiempo y tarifa | Registrar automáticamente; corrección solo con aprobación | Hora del servidor; auditoría de correcciones |
| Fecha y hora de salida | Marca de tiempo | Confidencial en conjunto con la placa | Cerrar el ticket y calcular el valor | Registrar tras validación de pago | Auditoría; no editable sin aprobación |
| Tarifa aplicable | Regla y valor vigente | Interno | Calcular el valor a cobrar | Configurar solo por responsable autorizado; consultar | Versionamiento de tarifas; aprobación administrativa |
| Valor facturado o cobrado | Monto calculado y monto recibido | Confidencial | Cobro, cierre de turno y conciliación operativa | Calcular por reglas; registrar | Integridad; auditoría; acceso por rol |
| Estado del pago | Pendiente, pagado, rechazado, anulado | Confidencial | Validar la salida | Cambiar solo por confirmación verificada o acción humana autorizada | Máquina de estados; auditoría; la IA no puede modificarlo |
| Identificador de transacción | Referencia del proveedor de pagos | Confidencial | Conciliar con el proveedor | Almacenar referencia mínima | Acceso restringido; sin datos de tarjeta |
| Comprobante de pago | Constancia emitida por el proveedor o el establecimiento | Confidencial | Soporte ante reclamaciones | Consultar por el titular y por personal autorizado | Retención definida; no confundir con el ticket |
| Medio de contacto del usuario, si se solicita | Correo o teléfono para envío de comprobante | Confidencial (dato personal) | Envío de comprobante, solo si se aprueba | Recolectar con autorización y finalidad informada | Opcional; minimización; aviso de privacidad \[por validar con asesor\] |
| Novedades del ticket | Ticket perdido, inconsistencia horaria, pago pendiente | Interno o Confidencial según contenido | Trazabilidad y resolución | Registrar, aprobar, resumir con apoyo del asistente | Texto libre tratado como entrada no confiable; auditoría |
| Usuario u operario que realizó una acción | Identificador de cuenta | Interno | Trazabilidad | Registrar automáticamente | No editable; cuentas individuales |
| Registros de auditoría | Evento, actor, fecha, objeto, valor anterior y nuevo | Restringido | Reconstrucción de hechos e investigación de incidentes | Escritura automática; lectura por roles de supervisión | Protección contra alteración; respaldo; retención definida |
| Información de configuración | Parámetros del sistema, roles, reglas | Interno | Operación del sistema | Modificar por administrador del sistema | Control de versiones y de cambios |
| Credenciales y secretos técnicos | Contraseñas, claves API, tokens, llaves de firma | Restringido | Autenticación entre componentes y con terceros | Uso por los servicios que los requieren | Gestor de secretos o variables protegidas; nunca en repositorios ni en prompts; rotación |
| Documentos operativos autorizados | Reglamento, tarifas publicadas, manuales y procedimientos | Interno o Público | Base de conocimiento del asistente | Indexar solo documentos aprobados | Control de versiones; aprobación previa a la indexación |
| Datos sintéticos para pruebas | Tickets y placas ficticias | Interno | Desarrollo y evaluación | Uso libre en entornos de prueba | Marcado como sintético; separación de entornos |

Consideraciones transversales:

- Las credenciales, claves API, tokens y secretos no deben almacenarse en repositorios públicos ni exponerse en prompts del asistente.
- La placa puede ser un dato personal o identificable según el contexto, en particular cuando se combina con horarios o datos de contacto; debe tratarse con controles adecuados. Su registro no implica autorización ilimitada para cualquier uso.
- El proyecto trabajará inicialmente con datos ficticios, sintéticos, anonimizados o expresamente autorizados \[SUP\].
- Los datos financieros o de pago deben minimizarse. El sistema no almacenará números completos de tarjetas ni datos de autenticación de medios de pago; esa información, si existe, permanecería en el proveedor de pagos.

### 6.2 Flujo preliminar de datos

1. **Registro de ingreso.** Un usuario autorizado (operario) registra el vehículo: placa, tipo de vehículo si aplica y hora tomada del servidor.
2. **Generación de ticket único.** El núcleo genera un identificador no predecible y asocia la estancia.
3. **Almacenamiento controlado.** El ticket se guarda en la base de datos local o institucional y se registra el evento de auditoría.
4. **Consulta del ticket.** El operario o administrador consulta según su rol; el conductor consulta desde la página web solo su ticket y con la placa enmascarada.
5. **Cálculo de tarifa.** El motor de reglas aplica la tarifa vigente configurada; el valor queda registrado con la versión de la regla aplicada.
6. **Pago en línea, si se implementa.** La página redirige o conecta de forma segura con un mecanismo de pago aprobado \[integración sujeta a validación técnica, contractual y de seguridad\]; el sistema envía solo los datos mínimos: referencia del ticket y valor.
7. **Recepción y validación del estado de pago.** La confirmación del proveedor se verifica (por ejemplo, autenticidad del mensaje, coincidencia de referencia y valor, y no repetición) antes de actualizar el estado.
8. **Confirmación antes del cierre.** El cierre del ticket requiere confirmación humana o una regla autorizada por el establecimiento; las excepciones requieren aprobación del administrador.
9. **Registro de salida y cierre.** Se registra la hora de salida y el ticket pasa a estado cerrado.
10. **Auditoría.** Cada acción relevante genera un registro protegido con actor, fecha, objeto y cambio.
11. **Respaldo, retención y eliminación.** Los datos se respaldan y se eliminan o anonimizan según la política definida \[DIP\].
12. **Uso del asistente local.** El asistente solo consulta procedimientos, explica reglas, resume novedades o apoya tareas documentales; no escribe en la base de datos de negocio.

**Información que no debe enviarse a modelos públicos, APIs no autorizadas ni servicios externos sin evaluación previa:** placas, horarios asociados a placas, identificadores de tickets activos, montos y estados de pago, identificadores de transacción, comprobantes, datos de contacto, registros de auditoría, configuración, credenciales y secretos, así como los documentos internos no publicados. Hacia el proveedor de pagos solo se envían los datos mínimos necesarios para procesar el pago, según el contrato y la documentación técnica que se valide.

| Procesamiento | Componentes | Justificación |
| --- | --- | --- |
| Local | Núcleo de tickets, motor de reglas, base de datos, auditoría, interfaces de operario y administrador, motor de IA y base RAG | Continuidad operativa y control de datos |
| Híbrido | Página web de consulta y pago (expuesta a Internet, alimentada por el núcleo), respaldos fuera del sitio si se aprueban | Acceso del conductor desde su dispositivo; resiliencia de respaldos |
| Remoto | Proveedor de pagos; servicio de notificaciones si se aprueba | Funciones que dependen de terceros \[RPV\] |

### 6.3 Arquitectura conceptual local-first

La arquitectura se describe en capas y sin asumir tecnologías definitivas. Cada componente indica su estado: **Confirmado por el contexto** \[HP\], **Propuesta arquitectónica** \[PA\], **Sujeto a validación** \[RPV\] o **Integración externa sujeta a evaluación técnica, contractual y de seguridad**.

| Capa | Componente | Función | Estado |
| --- | --- | --- | --- |
| Presentación | Interfaz de operario | Registro de ingreso, salida, validación y novedades; acceso al asistente | Confirmado por el contexto |
| Presentación | Interfaz administrativa | Tarifas, usuarios, roles, aprobaciones, reportes y auditoría | Propuesta arquitectónica |
| Presentación | Página web de consulta y pagos | Consulta del ticket por el conductor y solicitud de pago | Confirmado por el contexto; publicación en Internet sujeta a validación |
| Seguridad | Módulo de autenticación | Verificación de identidad de usuarios internos | Propuesta arquitectónica |
| Seguridad | Autorización basada en roles | Aplicación de permisos mínimos en la API | Propuesta arquitectónica |
| Negocio | Gestión de tickets | Ciclo de vida del ticket mediante estados definidos | Confirmado por el contexto |
| Negocio | Motor de reglas de tarifas | Cálculo determinista con reglas versionadas | Confirmado por el contexto; reglas por definir con el propietario |
| Negocio | Gestión de novedades | Registro, aprobación y cierre de novedades | Confirmado por el contexto |
| Negocio | Módulo de revisión humana | Cola de acciones sensibles pendientes de aprobación | Propuesta arquitectónica |
| Integración | Integración de pagos, si procede | Conexión con proveedor aprobado y validación de confirmaciones | Integración externa sujeta a evaluación técnica, contractual y de seguridad |
| Integración | Servicio de notificaciones, si se aprueba | Envío de comprobantes o avisos | Sujeto a validación |
| Datos | Base de datos local o institucional | Persistencia de tickets, pagos, novedades y configuración | Propuesta arquitectónica |
| Datos | Módulo de auditoría | Registro protegido de eventos | Propuesta arquitectónica |
| IA | Motor local de IA | Modelo de lenguaje ejecutado localmente; solo lectura y redacción | Propuesta arquitectónica; modelo y hardware por validar |
| IA | Base de conocimiento RAG local | Índice de manuales, tarifas y procedimientos autorizados, con citación de fuente | Propuesta arquitectónica |
| Operación | Mecanismo de copias de respaldo | Respaldo periódico y pruebas de restauración | Propuesta arquitectónica |
| Operación | Operación de contingencia | Registro local de ingresos y salidas sin Internet; sincronización posterior de pagos | Propuesta arquitectónica; alcance por validar |
| Operación | Monitoreo técnico y registro de errores | Detección de fallas y diagnóstico | Propuesta arquitectónica |

Principios de interacción entre componentes \[PA\]:

- Toda escritura sobre tickets, tarifas y pagos pasa por la API del núcleo, que aplica autorización y reglas de negocio.
- El asistente de IA se conecta al núcleo, si llega a hacerlo, mediante herramientas de solo lectura acotadas a los permisos del usuario que lo consulta, con registro de cada invocación. Si en fases posteriores se propone un agente, sus herramientas serán delimitadas y cualquier acción sensible requerirá aprobación humana explícita.
- La página web pública consulta un subconjunto mínimo de datos y no accede directamente a la base de datos.
- Las confirmaciones de pago se reciben por un punto de integración aislado y se validan antes de cambiar el estado del ticket.

## 7. Alcance, exclusiones y limitaciones

### 7.1 Alcance funcional

El alcance corresponde a un prototipo académico funcional y reproducible \[SUP\], que podrá incluir:

- Registro de tickets de entrada y salida.
- Consulta y validación de tickets.
- Gestión del estado de pago mediante estados definidos.
- Aplicación de tarifas predefinidas por responsables autorizados.
- Registro y aprobación de novedades.
- Generación de reportes operativos básicos (tickets por turno, novedades, estados de pago).
- Página web para consulta de ticket y solicitud de pago.
- Integración simulada o controlada con un flujo de pago, en ambiente de pruebas del proveedor que se valide, según viabilidad y autorización.
- Asistente local para consulta de procedimientos y orientación al operario, con citación de fuentes.
- Registro de auditoría.
- Gestión de usuarios y roles.
- Pruebas con información sintética o expresamente autorizada.

### 7.2 Exclusiones obligatorias

El sistema propuesto **no**:

- Autoriza la salida de vehículos sin los controles definidos por el establecimiento.
- Abre barreras de manera autónoma.
- Toma decisiones económicas autónomas.
- Modifica tarifas sin autorización administrativa.
- Realiza cobros sin confirmación o sin un mecanismo de pago autorizado.
- Almacena de forma innecesaria datos completos de tarjetas bancarias.
- Sustituye una pasarela de pago certificada.
- Sustituye obligaciones contables, tributarias o legales.
- Reemplaza al administrador, cajero u operario.
- Ofrece asesoría legal, financiera o contable.
- Utiliza modelos públicos para procesar datos operativos sin autorización.
- Permite a la IA modificar registros, precios, tickets o estados de pago sin supervisión humana.
- Garantiza por sí solo la prevención de fraude, pérdida o errores.
- Se presenta como un sistema de producción certificado.

Quedan fuera del alcance inicial, salvo validación posterior \[RPV\]: integración con barreras físicas, cámaras, OCR (*Optical Character Recognition*, reconocimiento óptico de caracteres) o reconocimiento automático de placas; facturación electrónica; integración con sistemas contables; y pagos reales en producción.

### 7.3 Alcance técnico

La versión inicial priorizará:

- Un prototipo funcional y reproducible.
- Un modelo de lenguaje local pequeño o mediano, si la IA se incluye, seleccionado según el hardware disponible \[valor sujeto a capacidad de hardware\].
- Hardware disponible por validar.
- Una base de conocimiento restringida a documentos autorizados.
- Datos de prueba controlados y marcados como sintéticos.
- Una interfaz mínima viable.
- Seguridad básica implementada y documentada: autenticación, roles, gestión de secretos y validación de entradas.
- Registro de auditoría.
- Pruebas de roles, permisos, errores y riesgos de prompt injection, entendida como la manipulación del comportamiento del modelo mediante instrucciones ocultas en textos que procesa.
- Documentación de instalación local-first, con versiones de modelos y dependencias.

### 7.4 Limitaciones

| Limitación | Implicación para el proyecto |
| --- | --- |
| Hardware disponible por validar | El tamaño del modelo y el rendimiento del asistente dependen del equipo disponible |
| Calidad limitada o variable de las respuestas del modelo | Las respuestas requieren verificación humana y citación de fuentes |
| Riesgo de alucinaciones | El modelo puede generar contenido plausible pero incorrecto; se mitiga con RAG, límites y advertencias, sin eliminarlo |
| Dependencia de reglas de tarifas correctamente configuradas | Un error de configuración produce cobros erróneos aunque el software funcione correctamente |
| Posible necesidad de conectividad para pagos externos | El pago en línea no opera sin Internet; la contingencia cubre el núcleo, no el pago en línea |
| Alcance limitado de la integración de pagos | En la fase académica se prevé integración simulada o en ambiente de pruebas |
| No disponibilidad de datos reales | Las pruebas con datos sintéticos pueden no reflejar todos los casos reales |
| Necesidad de validación con usuarios y propietarios | Los requisitos pueden cambiar tras el levantamiento de información |
| Posibles restricciones de interoperabilidad | Equipos o sistemas existentes podrían no permitir integración |
| Revisión de requisitos legales y contractuales | Protección de datos y contratos con proveedores de pago requieren asesoría especializada |
| Riesgos de seguridad aun con procesamiento local | Persisten riesgos internos, de configuración, físicos y de software |

## 8. Requisitos del sistema

Los requisitos son iniciales. La prioridad se expresa como Alta (indispensable para el prototipo), Media (deseable) o Baja (posterior). El estado es **Propuesto** cuando se deriva del contexto proporcionado y debe confirmarse en el levantamiento, o **Por validar** cuando depende de terceros, de datos personales o de decisiones institucionales pendientes.

### 8.1 Requisitos funcionales

| Código | Requisito | Descripción | Prioridad | Criterio de aceptación preliminar | Estado |
| --- | --- | --- | --- | --- | --- |
| RF-01 | Autenticación de usuarios | Los usuarios internos acceden con cuenta individual | Alta | Ningún usuario interno accede a funciones sin autenticarse | Propuesto |
| RF-02 | Autorización basada en roles | Cada función se habilita según el rol | Alta | Las pruebas de permisos muestran que cada rol accede solo a lo asignado | Propuesto |
| RF-03 | Registro de ingreso de vehículo | El operario registra placa, tipo de vehículo y hora del servidor | Alta | El ingreso queda registrado con actor y hora | Propuesto |
| RF-04 | Generación de ticket único | Se genera un identificador único y no predecible | Alta | No se presentan duplicados en el conjunto de prueba | Propuesto |
| RF-05 | Consulta de ticket | Personal autorizado consulta tickets según su rol | Alta | La consulta retorna el estado correcto del ticket de prueba | Propuesto |
| RF-06 | Registro de salida | Se registra la salida solo tras validar el estado de pago o la aprobación de una excepción | Alta | No es posible cerrar un ticket pendiente sin aprobación registrada | Propuesto |
| RF-07 | Consulta de tarifas autorizadas | Usuarios consultan la tarifa vigente | Alta | La tarifa mostrada coincide con la configuración vigente | Propuesto |
| RF-08 | Aplicación de reglas de tarifa configuradas | El motor calcula el valor con reglas versionadas | Alta | Los casos de prueba de tarifa producen el valor esperado | Propuesto; reglas por definir con el propietario |
| RF-09 | Registro de pagos o estado de pago | Se registra el pago presencial o el estado recibido del proveedor | Alta | Cada cambio de estado queda auditado | Propuesto |
| RF-10 | Página de consulta y pago de ticket | El conductor consulta su ticket y solicita el pago | Alta | La página muestra solo el ticket consultado, con placa enmascarada | Por validar (pasarela de pagos) |
| RF-11 | Validación de confirmación de pago | Se verifica autenticidad, referencia, valor y no repetición de la confirmación | Alta | Las confirmaciones alteradas o repetidas son rechazadas en pruebas | Por validar (pasarela de pagos) |
| RF-12 | Registro de novedades | Se registran novedades con tipo, descripción y actor | Alta | La novedad queda asociada al ticket y auditada | Propuesto |
| RF-13 | Gestión de tickets perdidos o inconsistentes | Se tramitan según reglas autorizadas y con aprobación del administrador | Alta | Ninguna novedad se cierra sin aprobación cuando la regla lo exige | Propuesto; reglas por definir con el propietario |
| RF-14 | Reportes operativos básicos | Reportes de tickets, pagos y novedades por turno | Media | Los totales del reporte coinciden con los datos de prueba | Propuesto |
| RF-15 | Registro de auditoría | Se registran actor, fecha, objeto y cambio de cada acción relevante | Alta | Toda acción sensible de prueba aparece en la auditoría | Propuesto |
| RF-16 | Gestión de usuarios y roles | El administrador del sistema crea, desactiva y asigna roles | Alta | Los cambios de rol quedan auditados | Propuesto |
| RF-17 | Consulta de procedimientos mediante asistente local | El operario formula preguntas sobre procedimientos | Media | El asistente responde con base en documentos autorizados \[por validar con usuarios\] | Propuesto |
| RF-18 | Consulta de documentos autorizados mediante RAG local, si se implementa | Las respuestas citan el documento y la sección fuente | Media | Las respuestas de prueba incluyen fuente verificable | Propuesto |
| RF-19 | Advertencias y límites del asistente | El asistente indica que es apoyo, que puede equivocarse y qué no puede hacer | Alta | La advertencia es visible en cada sesión | Propuesto |
| RF-20 | Revisión humana para acciones sensibles | Las acciones sensibles pasan por aprobación explícita | Alta | Las acciones sensibles de prueba quedan pendientes hasta aprobación | Propuesto |
| RF-21 | Copias de respaldo o exportación controlada | Respaldo periódico y exportación restringida a roles autorizados | Alta | Una restauración de prueba recupera los datos | Propuesto |
| RF-22 | Funcionamiento básico ante conectividad limitada | Ingreso, salida y consulta operan en la red local sin Internet | Alta | En prueba sin Internet se registran ingresos y salidas | Propuesto; alcance de contingencia por validar |
| RF-23 | Registro y visualización de errores operativos | Los errores se registran y se muestran a roles técnicos | Media | Los errores provocados en prueba quedan registrados | Propuesto |
| RF-24 | Retención y eliminación controlada | Eliminación o anonimización según política | Media | Los datos vencidos de prueba se eliminan o anonimizan según la regla configurada | Por validar (uso de datos personales; política por definir) |
| RF-25 | Envío de comprobante al usuario | Envío por correo o mensaje con autorización del titular | Baja | — | Por validar (notificaciones externas y datos personales) |
| RF-26 | Integración con barreras físicas | Señal hacia barreras controlada por reglas y humanos, nunca por la IA | Baja | — | Por validar |
| RF-27 | Facturación electrónica | Emisión de documentos tributarios | Baja | — | Por validar; fuera del alcance inicial |
| RF-28 | Integración con sistemas contables | Exportación hacia herramientas contables | Baja | — | Por validar |
| RF-29 | Cámaras, OCR o reconocimiento de placas | Captura automática de placas | Baja | — | Por validar; fuera del alcance inicial |

### 8.2 Requisitos no funcionales

| Código | Categoría | Requisito | Método de verificación | Estado |
| --- | --- | --- | --- | --- |
| RNF-01 | Seguridad | Las contraseñas se almacenan con funciones de derivación robustas y las sesiones expiran por inactividad \[tiempo por validar con usuarios\] | Revisión de código y pruebas de sesión | Propuesto |
| RNF-02 | Privacidad | Se recolectan solo los datos necesarios para cada finalidad; la placa se enmascara en la página pública | Revisión de modelo de datos e inspección de la interfaz | Propuesto |
| RNF-03 | Confidencialidad | Las comunicaciones fuera del equipo local y la página pública usan canales cifrados | Inspección de configuración | Propuesto |
| RNF-04 | Integridad | Los cambios de estado siguen una máquina de estados y no admiten transiciones inválidas | Pruebas unitarias de transición | Propuesto |
| RNF-05 | Disponibilidad | El núcleo opera durante el horario del establecimiento \[SLA por acordar con el establecimiento\] | Pruebas de operación continua | Por validar |
| RNF-06 | Trazabilidad | Cada registro de negocio puede asociarse con su historial de acciones | Muestreo de registros en pruebas | Propuesto |
| RNF-07 | Auditoría | Los registros de auditoría no pueden modificarse desde la aplicación y se respaldan | Intento controlado de alteración en pruebas | Propuesto |
| RNF-08 | Rendimiento | El registro de ingreso y salida responde en un tiempo aceptable para la operación \[métrica por definir en pruebas\] | Pruebas de carga con datos sintéticos | Por validar |
| RNF-09 | Rendimiento del asistente | El tiempo de respuesta del asistente es compatible con la atención \[valor sujeto a capacidad de hardware\] | Medición en el hardware disponible | Por validar |
| RNF-10 | Usabilidad | El operario completa ingreso y salida con pocos pasos \[por validar con usuarios\] | Pruebas con usuarios representativos | Por validar |
| RNF-11 | Accesibilidad | La página pública sigue pautas de accesibilidad web reconocidas (contraste, etiquetas, navegación por teclado) | Revisión con lista de chequeo | Propuesto |
| RNF-12 | Operación local-first | Las funciones del núcleo no dependen de servicios externos | Prueba con Internet desconectado | Propuesto |
| RNF-13 | Modo de contingencia | Ante falla de Internet, la página de pago informa indisponibilidad y el cobro se realiza presencialmente | Simulación de falla | Propuesto |
| RNF-14 | Mantenibilidad | Código modular, documentado y con pruebas automatizadas | Revisión de repositorio | Propuesto |
| RNF-15 | Escalabilidad | El diseño admite más de un punto de atención o establecimiento sin rediseño completo | Revisión de arquitectura | Por validar |
| RNF-16 | Interoperabilidad | La API usa formatos abiertos y documentados | Revisión de especificación de la API | Propuesto |
| RNF-17 | Reproducibilidad | La instalación se reproduce desde la documentación con versiones fijadas de dependencias y modelos | Instalación en equipo limpio | Propuesto |
| RNF-18 | Gestión de errores | Los errores muestran mensajes claros sin revelar información interna | Pruebas de errores provocados | Propuesto |
| RNF-19 | Respaldo y recuperación | Respaldos periódicos con restauración verificada \[frecuencia por definir con el propietario\] | Prueba de restauración | Propuesto |
| RNF-20 | Gestión de secretos | Los secretos se mantienen fuera del código y del repositorio y no se incluyen en prompts | Escaneo del repositorio e inspección de configuración | Propuesto |
| RNF-21 | Licenciamiento | Modelos, bibliotecas y datos tienen licencias compatibles con el uso previsto | Inventario de licencias | Propuesto |
| RNF-22 | Transparencia | El asistente se identifica como sistema de IA, cita fuentes y advierte sus límites | Inspección de la interfaz | Propuesto |
| RNF-23 | Supervisión humana | Ninguna acción sensible se ejecuta sin aprobación humana registrada | Pruebas de flujo de aprobación | Propuesto |
| RNF-24 | Resistencia a prompt injection | El asistente trata documentos, novedades y entradas de usuario como datos no confiables y carece de herramientas de escritura | Conjunto de pruebas adversariales | Propuesto |
| RNF-25 | Eficiencia computacional | El modelo seleccionado opera en el hardware disponible sin degradar el núcleo operativo | Medición de uso de recursos \[valor sujeto a capacidad de hardware\] | Por validar |

## 9. Criterios de éxito

Los criterios se clasifican en tres tipos: **Prototipo** (verificables por el equipo en ambiente de pruebas), **Operativo** (requieren participación del establecimiento) y **Validación externa** (requieren validación comercial, financiera, contractual o regulatoria). Ninguna meta ha sido alcanzada; todas son preliminares o están por validar.

| Código | Criterio de éxito | Indicador | Método de verificación | Meta preliminar | Tipo de criterio | Estado |
| --- | --- | --- | --- | --- | --- | --- |
| CE-01 | Registro correcto de tickets de prueba | Proporción de tickets de prueba registrados con todos los campos correctos | Ejecución de casos de prueba con datos sintéticos | \[meta preliminar: totalidad de los casos definidos\] | Prototipo | Por validar |
| CE-02 | Unicidad de identificadores | Número de identificadores duplicados | Generación masiva en prueba | \[meta preliminar: ningún duplicado\] | Prototipo | Por validar |
| CE-03 | Consulta y recuperación de tickets | Proporción de consultas que retornan el ticket y estado correctos | Casos de prueba de consulta | \[meta preliminar\] | Prototipo | Por validar |
| CE-04 | Aplicación consistente de tarifas | Coincidencia entre valor calculado y valor esperado por regla | Tabla de casos de tarifa elaborada con el propietario | \[meta preliminar: coincidencia en todos los casos acordados\] | Prototipo y Operativo | Por validar |
| CE-05 | Registro de novedades | Novedades de prueba registradas, aprobadas y auditadas | Escenarios de ticket perdido, inconsistencia y pago pendiente | \[meta preliminar\] | Prototipo | Por validar |
| CE-06 | Trazabilidad de acciones | Proporción de acciones sensibles con registro de auditoría completo | Muestreo de auditoría | \[meta preliminar: todas las acciones sensibles\] | Prototipo | Por validar |
| CE-07 | Operación local del núcleo | Funciones del núcleo disponibles sin Internet | Prueba con Internet desconectado | \[meta preliminar\] | Prototipo | Por validar |
| CE-08 | Manejo de conectividad limitada | Comportamiento correcto de la página de pago y del núcleo ante falla | Simulación de falla de red | \[meta preliminar\] | Prototipo | Por validar |
| CE-09 | Protección de información sensible | Ausencia de placas completas y datos internos en la página pública | Inspección y pruebas de consulta | \[meta preliminar\] | Prototipo | Por validar |
| CE-10 | Separación de roles | Intentos de acceso no autorizado bloqueados | Matriz de pruebas de permisos por rol | \[meta preliminar: todos los intentos bloqueados\] | Prototipo | Por validar |
| CE-11 | Ausencia de exposición de secretos | Secretos encontrados en repositorio, registros o prompts | Escaneo automatizado y revisión manual | \[meta preliminar: ninguno\] | Prototipo | Por validar |
| CE-12 | Confirmación controlada del estado de pago | Confirmaciones alteradas, repetidas o con valor distinto rechazadas | Pruebas en ambiente simulado o de pruebas del proveedor | \[meta preliminar\] | Prototipo; Validación externa para pagos reales | Por validar |
| CE-13 | Utilidad percibida por el operario | Valoración de utilidad en instrumento de evaluación | Encuesta o entrevista con operarios representativos | \[por validar con usuarios\] | Operativo | Por validar |
| CE-14 | Claridad de la interfaz | Tareas completadas sin ayuda en prueba de usabilidad | Prueba de usabilidad con tareas definidas | \[por validar con usuarios\] | Operativo | Por validar |
| CE-15 | Reportes básicos | Coincidencia de totales del reporte con datos de prueba | Comparación con cálculo independiente | \[meta preliminar\] | Prototipo | Por validar |
| CE-16 | Calidad de respuestas del asistente | Proporción de respuestas correctas y fundamentadas en un banco de preguntas | Evaluación con banco de preguntas y revisión humana | \[métrica por definir en pruebas\] | Prototipo | Por validar |
| CE-17 | Trazabilidad de fuentes RAG | Proporción de respuestas con cita verificable | Revisión de respuestas del banco de preguntas | \[meta preliminar\] | Prototipo | Por validar |
| CE-18 | Resistencia básica a prompt injection | Casos adversariales en los que el asistente no ejecuta instrucciones inyectadas ni revela información fuera de permisos | Conjunto de pruebas adversariales | \[métrica por definir en pruebas\] | Prototipo | Por validar |
| CE-19 | Reproducibilidad de instalación | Instalación exitosa en equipo limpio siguiendo la documentación | Instalación por una persona distinta al desarrollador | \[meta preliminar\] | Prototipo | Por validar |
| CE-20 | Documentación técnica y de usuario | Existencia y revisión de manual técnico, manual de usuario y guía de gobierno | Revisión por el docente o director | \[meta preliminar\] | Prototipo | Por validar |
| CE-21 | Viabilidad de integración de pagos reales | Aprobación técnica y contractual de un proveedor | Revisión con proveedor y asesor | \[por validar\] | Validación externa | Por validar |
| CE-22 | Conformidad del tratamiento de datos | Concepto favorable del responsable de datos o asesor | Revisión jurídica | \[por validar\] | Validación externa | Por validar |

## 10. Matriz inicial de riesgos según NIST AI RMF

El NIST AI Risk Management Framework 1.0 (NIST, 2023) organiza la gestión de riesgos de IA en cuatro funciones; el perfil NIST AI 600-1 (NIST, 2024) las complementa con riesgos propios de la IA generativa, como la confabulación (alucinación), la seguridad de la información y la cadena de valor de componentes. Aunque el marco se orienta a sistemas de IA, el proyecto lo aplica al sistema completo, porque los riesgos del asistente no pueden separarse de los datos y procesos a los que accede.

| Función | Aplicación al proyecto |
| --- | --- |
| Govern (Gobernar) | Políticas de uso, asignación de responsables, inventario de modelos y dependencias, licencias, definición de roles, aprobación humana y documentación |
| Map (Mapear) | Contexto del parqueadero, usuarios, datos, dependencias de terceros, escenarios de impacto y amenazas |
| Measure (Medir) | Pruebas funcionales, de seguridad, de permisos y de calidad de respuestas; verificación de auditoría y de flujos de pago |
| Manage (Gestionar) | Controles y mitigaciones, límites de autonomía, respuesta a incidentes, respaldo, monitoreo y mejora continua |

**Escalas.** Probabilidad: Baja, Media, Alta. Impacto: Bajo, Medio, Alto, Crítico. El nivel inherente combina ambas antes de controles; el riesgo residual es una estimación preliminar posterior a la aplicación de controles y debe recalcularse con evidencia de pruebas. Las valoraciones son juicios iniciales del equipo \[RI\], no mediciones.

| ID | Función NIST AI RMF | Riesgo | Causa | Evento de riesgo | Consecuencia | Probabilidad | Impacto | Nivel inherente | Controles propuestos | Evidencia o indicador | Responsable | Tratamiento | Riesgo residual |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| R-01 | Map / Manage | Acceso no autorizado a tickets, placas, pagos o reportes | Cuentas compartidas, permisos amplios, sesiones abiertas | Un usuario consulta o extrae datos sin necesidad operativa | Exposición de datos personales y comerciales | Media | Alto | Alto | Autenticación robusta; cuentas individuales; roles y mínimo privilegio; gestión de sesiones; auditoría de consultas | Pruebas de permisos; auditoría de accesos | Administrador del sistema | Mitigar | Medio |
| R-02 | Map / Manage | Exposición de identificadores de pago o comprobantes | Página pública con datos excesivos; registros sin control | Terceros obtienen referencias o comprobantes ajenos | Fraude potencial, reclamaciones, pérdida de confianza | Media | Alto | Alto | Minimización en la página; identificadores no predecibles; limitación de intentos; acceso por rol | Pruebas de enumeración; inspección de la interfaz | Equipo desarrollador | Mitigar | Medio |
| R-03 | Govern / Manage | Almacenamiento indebido de datos financieros sensibles | Diseño que guarda datos de tarjeta o de autenticación de pago | Datos de tarjetas almacenados localmente | Daño grave a titulares; incumplimiento contractual | Baja | Crítico | Alto | Prohibición de almacenar datos de tarjeta; pago en el proveedor; revisión del modelo de datos | Revisión del esquema y del flujo | Equipo desarrollador; propietario | Evitar | Bajo |
| R-04 | Govern / Manage | Uso o exposición de credenciales, claves API o secretos | Secretos en código, repositorio, registros o prompts | Un secreto se publica o se filtra | Acceso indebido al sistema o al proveedor | Media | Crítico | Crítico | Gestión de secretos fuera del código; escaneo de repositorio; rotación; secretos fuera de prompts | Resultados de escaneo; registro de rotaciones | Administrador del sistema | Mitigar | Medio |
| R-05 | Manage | Alteración de tickets, tarifas, pagos o registros | Permisos excesivos; ausencia de auditoría; acceso directo a la base | Un registro se modifica sin autorización | Cobros indebidos; pérdida de integridad | Media | Alto | Alto | Escritura solo por API; máquina de estados; separación de funciones; auditoría protegida; aprobación para correcciones | Auditoría de cambios; pruebas de integridad | Administrador del parqueadero; administrador del sistema | Mitigar | Medio |
| R-06 | Measure / Manage | Duplicidad de tickets o inconsistencia de estados | Generación de identificadores deficiente; concurrencia; sincronización tras contingencia | Dos tickets iguales o estados contradictorios | Cobros erróneos; conflictos con conductores | Media | Medio | Medio | Identificadores únicos con restricción en base de datos; transacciones; pruebas de concurrencia | Pruebas de unicidad y concurrencia | Equipo desarrollador | Mitigar | Bajo |
| R-07 | Map / Measure | Error en aplicación de tarifas configuradas | Reglas mal definidas o mal configuradas | Se cobra un valor distinto al autorizado | Reclamaciones y pérdidas | Media | Alto | Alto | Reglas versionadas y aprobadas; casos de prueba acordados con el propietario; vista previa antes de activar | Resultados de casos de tarifa | Propietario; administrador del parqueadero | Mitigar | Medio |
| R-08 | Measure / Manage | Confirmación incorrecta de un pago | Confirmaciones no verificadas; mensajes falsificados o repetidos | Un ticket queda pagado sin pago real | Pérdida económica; salida indebida | Media | Crítico | Crítico | Validación de autenticidad de confirmaciones o webhooks según el proveedor; verificación de referencia y valor; control de repetición; consulta de estado al proveedor | Pruebas con confirmaciones manipuladas | Equipo desarrollador; proveedor de pagos | Mitigar | Medio |
| R-09 | Map / Manage | Desconexión o falla en la integración de pagos | Caída del proveedor o de Internet | El pago en línea no se completa o su estado queda incierto | Demoras; pagos sin confirmar | Media | Medio | Medio | Estado intermedio de pago pendiente; reconciliación posterior; cobro presencial como contingencia | Simulación de fallas | Administrador del parqueadero | Mitigar | Bajo |
| R-10 | Govern / Map | Dependencia de un tercero o pasarela de pago | Concentración en un solo proveedor | Cambios de condiciones, costos o retiro del servicio | Interrupción del pago en línea | Media | Medio | Medio | Integración desacoplada; evaluación de proveedores; cláusulas contractuales revisadas | Informe de evaluación de proveedor | Propietario | Transferir parcialmente y mitigar | Medio |
| R-11 | Govern / Measure | Falta de trazabilidad de acciones | Auditoría incompleta o desactivable | No es posible reconstruir un incidente | Responsabilidad difusa; investigación imposible | Media | Alto | Alto | Auditoría obligatoria de acciones sensibles; registro de invocaciones del asistente; revisión periódica | Muestreo de auditoría | Administrador del sistema | Mitigar | Bajo |
| R-12 | Manage | Pérdida o corrupción de registros | Fallas de disco, errores de software, ataques | Datos irrecuperables | Interrupción y pérdida de evidencia | Media | Alto | Alto | Respaldos periódicos; verificación de integridad; transacciones | Pruebas de restauración | Administrador del sistema | Mitigar | Medio |
| R-13 | Manage | Copias de respaldo insuficientes | Respaldos no probados o en el mismo equipo | El respaldo falla al restaurar | Pérdida de información | Media | Alto | Alto | Política de respaldo; copia en medio separado; pruebas de restauración periódicas | Registro de pruebas de restauración | Administrador del sistema | Mitigar | Bajo |
| R-14 | Map / Manage | Operación indebida ante conectividad limitada | Procedimientos de contingencia no definidos | Se permiten salidas sin validar pago o se pierden registros | Pérdidas y conflictos | Media | Alto | Alto | Modo de contingencia documentado; registro local; pago presencial; sincronización controlada | Simulacros de contingencia | Administrador del parqueadero | Mitigar | Medio |
| R-15 | Govern | Uso no autorizado de datos reales para pruebas | Conveniencia del equipo; ausencia de política | Datos reales en entornos de desarrollo | Exposición de datos personales | Media | Alto | Alto | Política de datos sintéticos; separación de entornos; autorización expresa para datos reales | Revisión de conjuntos de datos | Docente o director; equipo desarrollador | Evitar | Bajo |
| R-16 | Govern / Map | Tratamiento inadecuado de placas o datos de contacto | Finalidad no definida; retención indefinida | Uso de datos para fines no informados | Afectación a titulares; posibles incumplimientos | Media | Alto | Alto | Finalidades documentadas; minimización; retención limitada; aviso de privacidad revisado por asesor | Inventario de datos; política aprobada | Propietario; responsable de datos | Mitigar | Medio |
| R-17 | Manage | Configuración incorrecta de roles o permisos | Roles mal definidos o no revisados | Usuarios con permisos excesivos | Accesos y cambios indebidos | Media | Alto | Alto | Matriz de roles aprobada; pruebas de permisos; revisión periódica de cuentas | Pruebas por rol; actas de revisión | Administrador del sistema | Mitigar | Bajo |
| R-18 | Govern / Manage | Uso del asistente para tomar decisiones no autorizadas | Confianza excesiva del operario en la IA | Se decide una excepción o un cobro con base en la respuesta del asistente | Decisiones incorrectas sin responsable claro | Media | Alto | Alto | Asistente sin herramientas de escritura; advertencias; aprobación humana; capacitación | Revisión de registros del asistente | Administrador del parqueadero | Mitigar | Medio |
| R-19 | Measure / Manage | Alucinaciones o respuestas incorrectas del asistente | Limitaciones del modelo; recuperación deficiente | El asistente inventa un procedimiento o tarifa | Orientación errónea al operario | Alta | Medio | Alto | RAG con citación obligatoria; respuesta de no saber ante falta de fuente; tarifas consultadas del motor de reglas y no generadas; evaluación con banco de preguntas | Tasa de respuestas fundamentadas \[métrica por definir en pruebas\] | Equipo desarrollador | Mitigar | Medio |
| R-20 | Measure / Manage | Prompt injection en documentos, tickets o entradas | Texto malicioso en novedades, documentos o preguntas | El asistente sigue instrucciones inyectadas o revela información | Fuga de información u orientación manipulada | Media | Alto | Alto | Tratar entradas como datos no confiables; separación de instrucciones y contexto; sin herramientas de escritura; filtrado; red teaming | Resultados de pruebas adversariales | Equipo desarrollador | Mitigar | Medio |
| R-21 | Map / Manage | Fuga de información desde la base de conocimiento RAG | Indexación de documentos no autorizados; recuperación sin control de permisos | El asistente expone contenido restringido | Exposición de información interna | Media | Alto | Alto | Indexar solo documentos aprobados; sin datos personales en el índice; control de acceso en la recuperación | Inventario del índice; pruebas de consulta | Administrador del sistema | Mitigar | Bajo |
| R-22 | Govern | Dependencias o modelos con licencias incompatibles | Selección sin revisión de licencias | Uso no permitido de un modelo o biblioteca | Riesgo legal; reemplazo forzoso | Media | Medio | Medio | Inventario de modelos, dependencias y licencias; revisión previa a la adopción | Inventario actualizado | Equipo desarrollador | Evitar | Bajo |
| R-23 | Govern / Measure | Vulnerabilidades en la cadena de suministro de software y modelos | Paquetes o modelos de origen no verificado | Se introduce código o modelo comprometido | Compromiso del sistema | Media | Alto | Alto | Fuentes oficiales; verificación de integridad; versiones fijadas; revisión de vulnerabilidades | Reportes de análisis de dependencias | Administrador del sistema | Mitigar | Medio |
| R-24 | Manage | Uso de componentes desactualizados | Ausencia de proceso de actualización | Explotación de vulnerabilidades conocidas | Compromiso del sistema | Media | Alto | Alto | Plan de actualización; monitoreo de avisos de seguridad; pruebas antes de actualizar | Registro de actualizaciones | Administrador del sistema | Mitigar | Medio |
| R-25 | Govern / Manage | Modificación no autorizada de procedimientos o documentos fuente | Repositorio documental sin control | Un documento alterado orienta mal al operario | Procedimientos erróneos | Baja | Alto | Medio | Versionamiento; aprobación de cambios; verificación de integridad antes de indexar | Historial de versiones | Administrador del parqueadero | Mitigar | Bajo |
| R-26 | Govern / Manage | Falta de supervisión humana en acciones sensibles | Flujos que omiten aprobación por conveniencia | Excepciones o correcciones sin aprobación | Pérdidas y abuso | Media | Alto | Alto | Módulo de revisión humana; separación de funciones; auditoría de aprobaciones | Pruebas de flujo de aprobación | Administrador del parqueadero | Mitigar | Bajo |
| R-27 | Govern | Uso del sistema fuera del alcance aprobado | Expansión informal de funciones | El sistema se usa para vigilancia, perfiles o fines no previstos | Afectación de derechos; incumplimiento | Baja | Alto | Medio | Política de uso aceptable; alcance documentado; revisión de cambios | Registro de solicitudes de cambio | Propietario | Evitar | Bajo |
| R-28 | Map / Manage | Afectación de la confianza del usuario por información errónea | Errores en página pública o en orientación | El conductor recibe un valor o estado incorrecto | Reclamaciones y pérdida de reputación | Media | Medio | Medio | Valores tomados del motor de reglas; mensajes claros; canal de reclamación | Registro de reclamaciones \[dato por validar\] | Administrador del parqueadero | Mitigar | Bajo |
| R-29 | Manage | Falla de disponibilidad durante la operación | Fallas de hardware, energía o software | El sistema no está disponible en el turno | Retorno a registro manual; demoras | Media | Alto | Alto | Procedimiento manual de contingencia; respaldo; monitoreo; equipo de reemplazo \[por validar\] | Simulacros; registro de incidentes | Administrador del sistema | Mitigar | Medio |
| R-30 | Map / Manage | Fraude operativo o manipulación de tickets | Colusión, abuso de permisos, tickets falsificados | Salidas sin pago o cobros desviados | Pérdidas económicas | Media | Alto | Alto | Separación de funciones; auditoría; identificadores no predecibles; aprobación de excepciones; reportes de anomalías. El sistema no garantiza prevenir el fraude por sí solo | Revisión de auditoría y novedades | Propietario; administrador del parqueadero | Mitigar | Medio |
| R-31 | Govern | Incumplimiento contractual o de privacidad en la integración de pagos | Integración sin revisión contractual ni de requisitos del proveedor | Se incumplen condiciones del proveedor o normas de datos | Sanciones, suspensión del servicio | Media | Alto | Alto | Revisión jurídica y contractual previa; cumplimiento de requisitos técnicos del proveedor; integración real solo tras validación | Concepto del asesor; aprobación del proveedor | Propietario; asesor jurídico | Evitar hasta validar | Bajo |
| R-32 | Govern / Map | Falsa sensación de seguridad por usar infraestructura local | Suponer que local equivale a seguro | Se omiten controles internos y físicos | Incidentes no previstos | Media | Alto | Alto | Capacitación; controles físicos y lógicos; evaluaciones periódicas de seguridad | Lista de chequeo de seguridad | Administrador del sistema; propietario | Mitigar | Medio |

El uso de IA local reduce parte del riesgo de transferencia de datos a terceros, pero no elimina los riesgos de acceso interno indebido, configuración incorrecta, robo o daño de equipos, vulnerabilidades, errores de software, malos usos, alucinaciones ni fallas de seguridad. La matriz se actualizará en cada módulo del diplomado con la evidencia que produzcan las pruebas.

## 11. Gobierno, seguridad, privacidad y uso responsable

Los lineamientos siguientes son preliminares \[PA\]. No constituyen asesoría legal definitiva y deben ser revisados por el establecimiento, los responsables de datos, los asesores jurídicos, los responsables contables y, cuando corresponda, el proveedor de pagos.

### 11.1 Gobierno del sistema y responsables

- **Gobierno del sistema.** Se propone un registro de gobierno que documente alcance aprobado, responsables, modelos y versiones en uso, documentos indexados, roles vigentes y decisiones tomadas, actualizado en cada fase.
- **Asignación de responsables.** El propietario aprueba tarifas, políticas y alcance; el administrador del parqueadero aprueba excepciones y novedades; el administrador del sistema gestiona cuentas, configuración, respaldos y secretos; el equipo desarrollador mantiene el inventario técnico; el docente o director valida el avance académico. La designación de responsable del tratamiento de datos es una decisión pendiente \[DIP\].

### 11.2 Control de acceso

- **Mínimo privilegio.** Cada rol recibe solo los permisos necesarios para su función; los permisos se revisan periódicamente \[frecuencia por definir con el propietario\].
- **Separación de funciones.** Quien registra una novedad o excepción no la aprueba; quien configura tarifas no las aprueba unilateralmente; quien administra el sistema no altera registros de auditoría.
- **Autenticación y autorización.** Cuentas individuales, contraseñas robustas, expiración de sesiones y, si es viable, un segundo factor para roles administrativos \[por validar\]. La autorización se aplica en la API y no solo en la interfaz.

### 11.3 Datos personales e información

- **Clasificación de datos.** Se aplica la clasificación del capítulo 6.1, revisable por el responsable de datos.
- **Finalidad y minimización.** Cada dato tiene una finalidad documentada; no se recolectan datos sin necesidad operativa. Los datos de contacto son opcionales y requieren autorización del titular.
- **Retención, respaldo y eliminación.** Los plazos de retención por tipo de dato son una decisión pendiente \[DIP\]; al vencer, los datos se eliminan o anonimizan, y los respaldos siguen la misma política.
- **Manejo de información de usuarios.** El tratamiento de datos personales debe revisarse frente a la Ley 1581 de 2012 y su reglamentación, incluyendo política de tratamiento, autorización y atención de solicitudes de titulares \[por validar con asesor jurídico\].
- **Datos sintéticos y validación institucional.** En la etapa académica se usan datos sintéticos o ficticios. El uso de datos reales requiere autorización expresa del establecimiento, revisión del responsable de datos y aprobación del docente o director.

### 11.4 Trazabilidad, incidentes y secretos

- **Auditoría y trazabilidad.** Las acciones sensibles, las aprobaciones y las invocaciones del asistente se registran con actor, fecha y objeto; los registros se protegen contra alteración.
- **Gestión de incidentes.** Se propone un plan básico: detección, contención, notificación a los responsables, análisis con base en auditoría, recuperación y lecciones aprendidas. Las obligaciones de notificación externa deben precisarse con el asesor jurídico \[DIP\].
- **Gestión de secretos.** Los secretos se mantienen fuera del código, del repositorio y de los prompts; se rotan ante sospecha de exposición y al cambiar el personal con acceso.

### 11.5 Componentes, modelos e integraciones

- **Revisión de modelos y dependencias.** Se mantiene un inventario con origen, versión, propósito y verificación de integridad de cada modelo y dependencia.
- **Revisión de licencias.** Ningún modelo, biblioteca o conjunto de datos se adopta sin verificar que su licencia permite el uso previsto, incluido un eventual uso comercial.
- **Seguridad en integraciones de pago.** Toda integración de pago real queda sujeta a validación técnica, contractual, financiera, legal y de seguridad. El sistema no almacena datos de tarjetas; delega el procesamiento al proveedor y verifica cada confirmación. Si se procesan pagos con tarjeta, los requisitos del estándar PCI DSS aplicables deben precisarse con el proveedor \[por validar\].
- **Revisión jurídica, comercial y contractual.** Antes de integrar pagos reales se revisan contrato, costos, responsabilidades, requisitos técnicos del proveedor y obligaciones contables y tributarias con los asesores correspondientes.

### 11.6 Uso responsable del asistente de IA

- **Transparencia.** El asistente se identifica como sistema de IA, informa que sus respuestas son orientativas y cita los documentos en que se basa.
- **Advertencias sobre contenido generado.** Cada respuesta indica que debe verificarse con el procedimiento vigente o con el administrador; ante falta de fuente, el asistente declara que no tiene información suficiente.
- **Supervisión humana.** Las decisiones sobre cobros, excepciones, salidas y correcciones son siempre humanas y quedan registradas.
- **Prohibición de delegar decisiones críticas.** El asistente no puede modificar tarifas, alterar estados de pago, autorizar salidas, ejecutar pagos, abrir barreras, crear o cancelar tickets críticos ni consultar datos fuera de los permisos del usuario. Esta restricción se implementa técnicamente (sin herramientas de escritura) y no solo mediante instrucciones al modelo.
- **Agentes.** Si en fases posteriores se propone un agente, este tendrá herramientas delimitadas, registro de cada invocación y aprobación humana explícita para cualquier acción sensible.

## 12. Supuestos, dependencias y preguntas abiertas

### 12.1 Supuestos

| Código | Supuesto de trabajo \[SUP\] |
| --- | --- |
| SUP-01 | Se contará con la participación de un establecimiento de parqueo o de usuarios representativos para el levantamiento de requisitos |
| SUP-02 | El desarrollo inicial se realizará con datos sintéticos, ficticios, anonimizados o expresamente autorizados |
| SUP-03 | Se podrá identificar y analizar un proceso real de gestión de tickets |
| SUP-04 | Se dispondrá de un entorno local o institucional controlado para desarrollo y pruebas |
| SUP-05 | La IA se empleará como apoyo y no como autoridad autónoma |
| SUP-06 | Las tarifas serán definidas y aprobadas por responsables autorizados del establecimiento |
| SUP-07 | La integración de pagos reales requerirá validación posterior; en la fase académica será simulada o en ambiente de pruebas |
| SUP-08 | El alcance inicial será el de un prototipo académico |
| SUP-09 | El instrumento de encuesta previsto por el autor podrá aplicarse a conductores y operarios para recolectar evidencia del problema |

### 12.2 Dependencias

| Dependencia | Afecta a | Responsable de resolverla |
| --- | --- | --- |
| Disponibilidad de usuarios para el levantamiento de requisitos | Caracterización, requisitos, criterios operativos | Autor; establecimiento |
| Definición de tarifas y reglas de negocio | Motor de reglas, RF-08, CE-04 | Propietario |
| Disponibilidad de hardware y red | Arquitectura, modelo local, rendimiento | Autor; institución |
| Selección de modelo local, si se usa IA | Asistente, RNF-09, RNF-25 | Equipo desarrollador |
| Disponibilidad de documentación operativa | Base RAG, RF-17, RF-18 | Administrador del parqueadero |
| Definición de roles | Control de acceso, RF-02 | Propietario; administrador del sistema |
| Acceso a ambiente de pruebas | Construcción y evaluación | Institución; equipo desarrollador |
| Posible aprobación de proveedor de pagos | RF-10, RF-11, CE-21 | Propietario; proveedor |
| Revisión de seguridad | Controles y riesgo residual | Docente o director; responsable de tecnología |
| Revisión jurídica, contable y contractual | Datos personales, pagos, retención | Asesores del establecimiento |
| Capacidad de soporte técnico | Disponibilidad y mantenimiento | Establecimiento |
| Acceso a mecanismos de respaldo | RF-21, RNF-19 | Administrador del sistema |

### 12.3 Preguntas abiertas

**Operación y tarifas**

1. ¿Qué tipos de vehículos y tarifas maneja el establecimiento?
2. ¿Qué información contiene actualmente un ticket y en qué formato se emite?
3. ¿Cómo se calculan las tarifas (fracciones, mínimos, tarifas especiales o mensualidades)?
4. ¿Cómo se gestionan hoy los tickets perdidos y quién lo autoriza?
5. ¿Quién puede modificar tarifas y con qué aprobación?
6. ¿Cómo se realiza el cierre de turno y qué soportes se generan?
7. ¿Qué situaciones requieren autorización explícita del administrador?
8. ¿Qué indicadores operativos se utilizarán para evaluar el prototipo?

**Página de pago e integración**

9. ¿Qué información debe aparecer en la página de pago?
10. ¿Qué datos puede consultar un usuario con un código de ticket?
11. ¿Qué proveedor de pagos se consideraría, si se implementa, y qué requisitos técnicos y contractuales impone?
12. ¿Se requiere integración con barreras, cámaras, OCR o lectores?

**Datos, seguridad y continuidad**

13. ¿Qué información se podrá almacenar y por cuánto tiempo?
14. ¿Qué usuarios tendrán acceso a reportes?
15. ¿Qué operación debe mantenerse disponible sin Internet?
16. ¿Qué medidas de autenticación estarán disponibles?
17. ¿Qué políticas de respaldo y recuperación existen actualmente?
18. ¿Existe una política de tratamiento de datos personales en el establecimiento?

**Asistente de IA y cumplimiento**

19. ¿Qué información y documentos puede consultar el asistente local?
20. ¿Qué acciones debe tener estrictamente prohibidas la IA, además de las ya definidas?
21. ¿Cuáles requisitos requieren revisión jurídica o contractual?

## 13. Conclusiones preliminares

1. La gestión de tickets, tarifas, pagos y novedades en establecimientos de parqueo puede presentar una baja integración que afecta la trazabilidad, la conciliación operativa y la atención en los puntos de pago. Este planteamiento se sustenta en un análisis causal razonado que debe contrastarse con evidencia recolectada en el establecimiento participante y mediante el instrumento de encuesta previsto.
2. Una arquitectura local-first resulta pertinente para mantener la continuidad del núcleo operativo ante fallas de conectividad y para conservar el control de la información. No obstante, el pago en línea exige un componente expuesto a Internet y un proveedor externo, por lo que la solución es híbrida en ese punto y requiere controles específicos.
3. La formulación separa la automatización operativa basada en reglas verificables de las decisiones sensibles, que permanecen en manos humanas con aprobación registrada. La inteligencia artificial cumple una función de apoyo documental y de orientación; no tiene autoridad sobre pagos, tarifas, barreras ni salida de vehículos, y esa restricción se implementa técnicamente.
4. La seguridad, la trazabilidad y la privacidad se incorporan desde la formulación mediante control de acceso por rol, auditoría protegida, minimización de datos y una matriz de 32 riesgos estructurada según las funciones Govern, Map, Measure y Manage del NIST AI RMF. El procesamiento local reduce algunos riesgos, pero no reemplaza estos controles.
5. El proyecto requiere validación con usuarios y establecimientos reales, y cualquier integración de pagos reales debe evaluarse técnica, contractual, financiera, legal y de seguridad antes de su implementación. Hasta entonces, el alcance corresponde a un prototipo académico con datos sintéticos.
6. Este documento cumple los entregables del Módulo 1 —caracterización del caso de uso, actores, clasificación de datos, flujo preliminar, delimitación local, híbrida y remota, requisitos, criterios de éxito, matriz de riesgos y decisiones preliminares de gobernanza— y constituye el insumo para las fases de diseño detallado, construcción y evaluación. El sistema no está implementado, validado ni certificado.

## 14. Referencias preliminares

Congreso de Colombia. (2012). *Ley Estatutaria 1581 de 2012, por la cual se dictan disposiciones generales para la protección de datos personales*. Diario Oficial No. 48.587.

Departamento Nacional de Planeación. (2025). *Documento CONPES 4144: Política Nacional de Inteligencia Artificial*. Consejo Nacional de Política Económica y Social. \[Enlace por validar\]

Lewis, P., Perez, E., Piktus, A., Petroni, F., Karpukhin, V., Goyal, N., Küttler, H., Lewis, M., Yih, W., Rocktäschel, T., Riedel, S., & Kiela, D. (2020). Retrieval-augmented generation for knowledge-intensive NLP tasks. *Advances in Neural Information Processing Systems, 33*, 9459–9474.

Ministerio de Comercio, Industria y Turismo. (2013). *Decreto 1377 de 2013, por el cual se reglamenta parcialmente la Ley 1581 de 2012*. \[Referencia por validar: datos de publicación\]

National Institute of Standards and Technology. (2023). *Artificial Intelligence Risk Management Framework (AI RMF 1.0)* (NIST AI 100-1). U.S. Department of Commerce. https://doi.org/10.6028/NIST.AI.100-1

National Institute of Standards and Technology. (2024). *Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile* (NIST AI 600-1). U.S. Department of Commerce. https://doi.org/10.6028/NIST.AI.600-1

OWASP Foundation. (2021). *OWASP Top 10:2021*. https://owasp.org/Top10/

OWASP Foundation. (2024). *OWASP Top 10 for LLM Applications 2025*. OWASP GenAI Security Project. https://genai.owasp.org/ \[Enlace específico por validar\]

PCI Security Standards Council. (2024). *Payment Card Industry Data Security Standard (PCI DSS) v4.0.1*. https://www.pcisecuritystandards.org/ \[Aplicabilidad por validar con el proveedor de pagos\]

UNESCO. (2022). *Recommendation on the Ethics of Artificial Intelligence*. https://unesdoc.unesco.org/ark:/48223/pf0000381137

World Wide Web Consortium. (2023). *Web Content Accessibility Guidelines (WCAG) 2.2*. W3C Recommendation. https://www.w3.org/TR/WCAG22/

Las referencias se construyeron a partir de documentos institucionales y técnicos conocidos; antes de la entrega final se recomienda verificar cada enlace, la fecha de consulta y la versión vigente de cada documento.

## Nota de validación institucional

Este documento corresponde a un planteamiento inicial elaborado para el Módulo 1 del Diplomado en Inteligencia Artificial Generativa Local, Agentes Autónomos y Sistemas Multimodales. Sus requisitos, supuestos, valoraciones de riesgo y controles son preliminares y no constituyen asesoría jurídica, financiera ni contable. Antes de avanzar a las fases de diseño detallado y construcción, y en todo caso antes de utilizar datos reales o integrar pagos reales, el documento debe ser revisado y validado por:

- El propietario o administrador del establecimiento de parqueo.
- Operarios representativos.
- El responsable de tecnología o soporte.
- El responsable de protección de datos, cuando aplique.
- El responsable contable o financiero, cuando aplique.
- El asesor jurídico o de cumplimiento, cuando aplique.
- El proveedor de pagos, antes de una integración real.
- El docente o director del proyecto académico.

| Revisor | Nombre | Fecha | Observaciones |
| --- | --- | --- | --- |
| Propietario o administrador del establecimiento | \[campo editable\] | \[campo editable\] |  |
| Operario representativo | \[campo editable\] | \[campo editable\] |  |
| Responsable de tecnología o soporte | \[campo editable\] | \[campo editable\] |  |
| Responsable de protección de datos | \[campo editable\] | \[campo editable\] |  |
| Responsable contable o financiero | \[campo editable\] | \[campo editable\] |  |
| Asesor jurídico o de cumplimiento | \[campo editable\] | \[campo editable\] |  |
| Proveedor de pagos | \[campo editable\] | \[campo editable\] |  |
| Docente o director del proyecto | \[campo editable\] | \[campo editable\] |  |
