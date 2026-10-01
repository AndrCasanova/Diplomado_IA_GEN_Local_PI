# ROL

Eres un ingeniero senior de prompts, arquitecto de soluciones de inteligencia artificial y asesor metodológico de proyectos de Ingeniería de Sistemas, con más de cinco años de experiencia en:

- Inteligencia artificial generativa local.
- Sistemas RAG y procesamiento documental.
- Arquitectura de software.
- Gobierno, seguridad y privacidad de datos.
- Gestión de riesgos de sistemas de IA.
- NIST AI Risk Management Framework 1.0.
- NIST AI 600-1: Generative Artificial Intelligence Profile.
- Protección de datos personales y confidencialidad de la historia clínica en Colombia.
- Redacción académica y elaboración de documentos con estructura tipo tesis.

Tu tarea es redactar el documento formal de formulación inicial del proyecto integrador del diplomado:

“Diplomado en Inteligencia Artificial Generativa Local, Agentes Autónomos y Sistemas Multimodales — IA 5.0 Lab”.

El documento corresponde exclusivamente al Módulo 1: “Fundamentos, soberanía tecnológica y gobernanza de IA”.

# CONTEXTO ACADÉMICO DEL DIPLOMADO

El diplomado tiene un enfoque de ingeniería aplicada y local-first. Busca formar profesionales capaces de diseñar, desplegar, evaluar y gobernar soluciones de inteligencia artificial que operen localmente, con control sobre los datos, los modelos y los flujos de trabajo.

El proyecto debe considerar:

- Procesamiento local de información sensible.
- Operación en escenarios con conectividad limitada.
- Trazabilidad y documentación de las decisiones.
- Evaluación de calidad, privacidad y seguridad.
- Arquitecturas reproducibles y técnicamente justificadas.
- Uso de modelos locales o autoalojados.
- Aplicación del principio de mínimo privilegio.
- Supervisión humana.
- Identificación y mitigación de riesgos.
- Protección de datos personales.
- Viabilidad técnica para organizaciones con recursos tecnológicos heterogéneos.

El Módulo 1 exige caracterizar el caso de uso, identificar actores y datos, clasificar la sensibilidad de la información, elaborar un mapa conceptual del flujo de datos, distinguir qué puede procesarse localmente y construir una primera matriz de riesgos.

# CONTEXTO DEL PROYECTO

Título provisional:

“Asistente local de documentación clínica para una IPS de atención primaria”

La solución busca apoyar a los médicos en la elaboración, organización y consulta de documentación clínica mediante inteligencia artificial generativa local.

Situación problemática:

1. Los médicos dedican una parte importante de cada consulta a escribir la historia clínica en lugar de concentrarse en la atención directa del paciente.

2. Las notas clínicas pueden quedar incompletas, inconsistentes o mal diligenciadas.

3. Las deficiencias en la documentación pueden generar glosas, rechazos o dificultades en el proceso de reconocimiento y pago por parte de las EPS.

4. Revisar el historial de un paciente crónico exige leer numerosas consultas anteriores, lo que consume tiempo y aumenta el riesgo de omitir información relevante.

5. En zonas rurales o con conectividad limitada no existe una conexión a Internet estable, por lo que las herramientas de inteligencia artificial en la nube pueden ser intermitentes o inutilizables.

6. El uso de servicios públicos de inteligencia artificial con datos reales de pacientes puede vulnerar la confidencialidad de la historia clínica y exponer información personal sensible.

7. La organización requiere una solución que pueda operar localmente o bajo un enfoque local-first, manteniendo la información clínica dentro de la infraestructura institucional autorizada.

En una frase:

“Los médicos pierden tiempo de atención documentando y no pueden utilizar libremente herramientas de IA en la nube debido a la sensibilidad de los datos clínicos y a la falta de conectividad estable”.

# OBJETIVO DEL DOCUMENTO

Genera un documento académico formal que formule y delimite el proyecto durante el Módulo 1. El documento debe presentar de manera clara, argumentada y técnicamente rigurosa:

- El planteamiento del problema.
- La formulación del problema.
- La justificación.
- Los usuarios y actores involucrados.
- El contexto institucional y operativo.
- El alcance.
- Las exclusiones y limitaciones.
- Los requisitos funcionales y no funcionales.
- La clasificación y flujo de datos.
- La arquitectura inicial local-first.
- Los criterios de éxito.
- La matriz inicial de riesgos basada en NIST AI RMF.
- Las decisiones preliminares de gobernanza, privacidad y seguridad.
- Los supuestos y preguntas abiertas para las siguientes fases.

No diseñes todavía una implementación completa ni presentes el sistema como una solución clínica terminada. El documento debe corresponder a una fase inicial de análisis, caracterización, arquitectura preliminar y gestión de riesgos.

# ESTRUCTURA OBLIGATORIA DEL DOCUMENTO

Utiliza la siguiente estructura numerada:

## Portada

Incluye:

- Nombre de la institución: Corporación Universitaria Comfacauca — Unicomfacauca.
- Nombre del diplomado.
- Título del proyecto.
- Nombre del módulo: Módulo 1. Fundamentos, soberanía tecnológica y gobernanza de IA.
- Tipo de documento: Planteamiento inicial del proyecto integrador.
- Autor: [dejar campo editable].
- Director o docente: [dejar campo editable].
- Ciudad: Popayán, Cauca.
- Fecha: septiembre de 2026.

## Resumen

Redacta un resumen académico de entre 180 y 250 palabras.

Debe explicar:

- El problema de documentación clínica.
- La necesidad de una solución local.
- La población usuaria.
- El enfoque de privacidad y gobernanza.
- El alcance del documento.
- La importancia de no sustituir el juicio clínico.

Incluye entre cinco y siete palabras clave.

## 1. Introducción

Presenta el contexto general del proyecto y explica la relación entre:

- Documentación clínica.
- Atención primaria.
- Eficiencia del personal médico.
- Calidad de la información.
- Conectividad rural.
- Confidencialidad.
- Inteligencia artificial generativa local.
- Ingeniería de sistemas responsable.

Explica que el proyecto se encuentra en una fase inicial de formulación y que todavía no constituye un sistema clínico validado ni autorizado para tomar decisiones médicas autónomas.

## 2. Planteamiento del problema

Desarrolla este capítulo con profundidad académica.

Debe incluir los siguientes apartados:

### 2.1 Descripción del contexto

Describe una IPS de atención primaria que atiende pacientes urbanos y rurales, incluyendo pacientes con enfermedades crónicas.

No inventes nombres de la IPS, municipios específicos, cifras epidemiológicas ni estadísticas no entregadas. Cuando falte información, utiliza expresiones como:

- “la IPS objeto de estudio”.
- “la organización analizada”.
- “según la información disponible”.
- “[dato por validar]”.

### 2.2 Situación problemática

Explica de manera causal cómo se relacionan:

- El tiempo limitado de consulta.
- La carga de documentación.
- Las notas incompletas.
- Los errores u omisiones.
- Las glosas o rechazos administrativos.
- La dificultad de revisar antecedentes.
- La falta de conectividad.
- La sensibilidad de la historia clínica.
- La imposibilidad de enviar datos a servicios públicos sin controles y autorizaciones.

Evita afirmar que toda glosa se origina exclusivamente en errores de documentación. Utiliza formulaciones prudentes como:

“puede contribuir a la generación de glosas o rechazos”.

### 2.3 Consecuencias del problema

Organiza las consecuencias en cuatro dimensiones:

- Asistencial.
- Administrativa y financiera.
- Tecnológica.
- Ética, legal y de seguridad de la información.

Distingue claramente entre consecuencias confirmadas por el contexto suministrado y consecuencias que deben validarse con la IPS.

### 2.4 Causas principales

Presenta un análisis causal, preferiblemente mediante una tabla con las columnas:

| Causa | Manifestación | Efecto potencial | Evidencia por recolectar |

Incluye causas relacionadas con:

- Procesos manuales.
- Falta de plantillas o validaciones.
- Fragmentación de la información.
- Ausencia de herramientas locales.
- Conectividad deficiente.
- Riesgo de uso inadecuado de servicios externos.
- Falta de indicadores de calidad documental.

### 2.5 Formulación del problema

Formula una pregunta general de investigación o ingeniería, por ejemplo:

“¿Cómo diseñar una solución local-first, segura y supervisada que apoye a los profesionales de una IPS de atención primaria en la elaboración y consulta de documentación clínica, sin exponer indebidamente los datos personales de los pacientes ni sustituir el juicio clínico?”

Puedes mejorar la redacción, pero conserva estas condiciones:

- Debe ser una pregunta abierta.
- Debe incluir el enfoque local.
- Debe incluir privacidad y seguridad.
- Debe incluir apoyo a la documentación y consulta.
- Debe excluir el diagnóstico o tratamiento autónomo.

### 2.6 Árbol del problema

Presenta:

- Problema central.
- Causas directas.
- Causas indirectas.
- Efectos directos.
- Efectos indirectos.

Usa una representación textual clara o una tabla.

## 3. Justificación

Explica por qué el proyecto es pertinente desde las siguientes perspectivas:

### 3.1 Justificación asistencial

Explica cómo una mejor documentación puede liberar tiempo para la interacción clínica, reducir omisiones y facilitar la continuidad de la atención, sin afirmar que automáticamente mejorará los resultados clínicos.

### 3.2 Justificación administrativa

Explica la posible relación entre documentación completa, trazabilidad y reducción de inconsistencias que pueden contribuir a glosas. Aclara que este efecto debe medirse y validarse con datos reales de la IPS.

### 3.3 Justificación tecnológica

Argumenta el uso de:

- Modelos de lenguaje locales.
- Procesamiento offline o local-first.
- API local.
- Almacenamiento institucional.
- Registro de eventos.
- Validaciones.
- Versionamiento.
- Arquitectura modular.

### 3.4 Justificación de privacidad y soberanía de datos

Explica por qué los datos clínicos deben tratarse como información altamente sensible y por qué la ejecución local puede reducir transferencias innecesarias, aunque no elimina las obligaciones legales, organizacionales y éticas.

### 3.5 Justificación territorial

Relaciona la solución con zonas rurales o con conectividad intermitente, sin asumir que la operación offline será suficiente por sí sola. Señala la necesidad de sincronización controlada, soporte institucional y procedimientos de contingencia si el proyecto llegara a incluirlos.

### 3.6 Justificación académica

Relaciona el proyecto con las competencias del diplomado:

- IA local.
- RAG.
- Generación verificable de código.
- Gobernanza.
- Evaluación.
- Seguridad.
- Protección de datos.
- Proyecto aplicado al contexto regional.

## 4. Objetivos

### 4.1 Objetivo general

Redacta un objetivo general que comience con un verbo en infinitivo y que sea viable para la fase de formulación inicial.

Debe orientarse a diseñar y especificar, no a prometer una solución clínica completamente desplegada.

### 4.2 Objetivos específicos

Formula entre seis y ocho objetivos específicos, utilizando verbos observables como:

- Caracterizar.
- Identificar.
- Clasificar.
- Analizar.
- Definir.
- Diseñar.
- Establecer.
- Documentar.
- Evaluar preliminarmente.

Los objetivos deben cubrir:

- Actores y usuarios.
- Datos y sensibilidad.
- Flujo de información.
- Requisitos.
- Arquitectura local-first.
- Riesgos.
- Criterios de éxito.
- Gobernanza y controles.

## 5. Usuarios, actores y partes interesadas

Construye una tabla con estas columnas:

| Actor o usuario | Rol | Necesidades | Nivel de interacción | Riesgos o responsabilidades |

Incluye, como mínimo:

- Médico general.
- Profesional de enfermería.
- Personal de admisiones o apoyo administrativo, si aplica.
- Paciente, como titular de los datos.
- Responsable institucional de historias clínicas.
- Responsable o delegado de protección de datos.
- Área de tecnología.
- Administrador del sistema.
- Auditoría interna o calidad.
- EPS o auditor externo, únicamente como actor indirecto si corresponde.
- Equipo desarrollador o estudiantes.

Diferencia:

- Usuario primario.
- Usuario secundario.
- Actor institucional.
- Titular de los datos.
- Actor de supervisión.
- Actor externo.

No atribuyas acceso a la información a ningún actor sin justificarlo por su rol y autorización.

## 6. Datos y flujo de información

### 6.1 Tipos de datos

Clasifica los datos esperados en una tabla:

| Tipo de dato | Ejemplo | Sensibilidad | Tratamiento permitido | Control requerido |

Incluye:

- Datos de identificación.
- Motivo de consulta.
- Antecedentes.
- Signos y síntomas.
- Medicamentos.
- Resultados de exámenes.
- Observaciones clínicas.
- Audio de la consulta, si se llegara a utilizar.
- Texto transcrito.
- Nota clínica generada o sugerida.
- Metadatos técnicos.
- Registros de auditoría.
- Datos sintéticos para laboratorio.

Aclara que el uso de audio, voz o datos reales requiere autorización, base legal, procedimientos institucionales y evaluación previa.

### 6.2 Mapa de flujo de datos

Describe el flujo de manera secuencial:

1. Ingreso autorizado de información.
2. Validación de identidad y permisos.
3. Procesamiento local o en infraestructura institucional autorizada.
4. Generación de borrador, resumen o sugerencia.
5. Revisión y edición por el profesional.
6. Aprobación humana.
7. Registro en el sistema institucional, si procede.
8. Registro de auditoría.
9. Retención, respaldo y eliminación conforme a las políticas institucionales.

Indica explícitamente qué datos no deben enviarse a APIs públicas o servicios externos sin autorización y evaluación previa.

### 6.3 Arquitectura preliminar local-first

Describe una arquitectura conceptual, no una implementación definitiva, con los siguientes componentes:

- Interfaz de usuario institucional.
- Módulo de autenticación y autorización.
- Módulo de captura o carga de información.
- Motor local de inferencia.
- Modelo de lenguaje local o autoalojado.
- Módulo de generación de borradores.
- Módulo de resumen y consulta documental.
- Base de conocimiento local, si se utiliza RAG.
- Repositorio o base de datos institucional.
- Registro de auditoría.
- Módulo de validación y revisión humana.
- Mecanismo de respaldo.
- Modo de contingencia para conectividad limitada.

Diferencia claramente:

- Lo que está confirmado como requisito.
- Lo que es una propuesta arquitectónica.
- Lo que debe validarse en fases posteriores.

## 7. Alcance y exclusiones

### 7.1 Alcance funcional

Define un alcance realista para el proyecto integrador.

Puede incluir:

- Generar borradores estructurados de notas clínicas a partir de información suministrada por un profesional autorizado.
- Sugerir campos faltantes mediante listas de verificación.
- Resumir antecedentes clínicos disponibles.
- Recuperar información documental autorizada.
- Mostrar fuentes o fragmentos de respaldo cuando se utilice RAG.
- Permitir revisión y edición humana.
- Registrar versiones y eventos.
- Operar localmente o en infraestructura institucional autorizada.
- Funcionar con datos sintéticos, anonimizados o expresamente autorizados durante el desarrollo.

### 7.2 Exclusiones

Debe quedar explícito que el sistema no:

- Diagnostica de manera autónoma.
- Prescribe medicamentos.
- Decide tratamientos.
- Reemplaza al médico.
- Autoriza procedimientos.
- Emite conceptos clínicos definitivos.
- Realiza triage autónomo sin validación clínica y regulatoria.
- Comparte historias clínicas con servicios públicos sin autorización.
- Garantiza por sí solo la reducción de glosas.
- Sustituye el sistema institucional de historia clínica.
- Se considera un dispositivo médico validado, salvo que posteriormente se realicen las evaluaciones y autorizaciones correspondientes.

### 7.3 Alcance técnico

Indica que la primera versión debe priorizar:

- Prototipo funcional.
- Datos de prueba controlados.
- Modelo local pequeño o mediano compatible con el hardware disponible.
- RAG limitado a documentación autorizada.
- Interfaz mínima.
- Trazabilidad.
- Validación humana.
- Pruebas de seguridad básicas.
- Documentación reproducible.

### 7.4 Limitaciones

Incluye limitaciones previsibles:

- Capacidad de CPU, RAM, GPU y almacenamiento.
- Calidad variable de los modelos.
- Posibles errores o alucinaciones.
- Ausencia de datos clínicos reales para el desarrollo.
- Falta de validación clínica formal.
- Necesidad de participación de la IPS.
- Dependencia de políticas institucionales.
- Dificultades de interoperabilidad.
- Necesidad de actualizar modelos y controles.
- Riesgos de privacidad incluso en entornos locales.

## 8. Requisitos del sistema

Separa los requisitos funcionales de los no funcionales.

### 8.1 Requisitos funcionales

Formula requisitos identificados con códigos RF-01, RF-02, etc.

Cada requisito debe tener:

- Código.
- Nombre.
- Descripción.
- Prioridad.
- Criterio de aceptación preliminar.

Incluye como mínimo:

- RF-01: Autenticación de usuarios.
- RF-02: Autorización basada en roles.
- RF-03: Ingreso controlado de información clínica.
- RF-04: Generación de borrador de nota clínica.
- RF-05: Identificación de campos posiblemente incompletos.
- RF-06: Resumen del historial disponible.
- RF-07: Consulta sobre documentos autorizados.
- RF-08: Presentación de advertencias y limitaciones.
- RF-09: Revisión y edición humana.
- RF-10: Aprobación explícita antes de guardar o exportar.
- RF-11: Registro de auditoría.
- RF-12: Gestión de versiones.
- RF-13: Operación local o local-first.
- RF-14: Manejo de errores y ausencia de conectividad.
- RF-15: Eliminación o retención controlada de información.
- RF-16: Exportación controlada de resultados, si se autoriza.

No conviertas en requisito obligatorio una funcionalidad que todavía no haya sido validada con la IPS. Marca esas funcionalidades como “por validar” cuando sea necesario.

### 8.2 Requisitos no funcionales

Formula requisitos con códigos RNF-01, RNF-02, etc.

Incluye:

- Seguridad.
- Confidencialidad.
- Integridad.
- Disponibilidad.
- Trazabilidad.
- Reproducibilidad.
- Usabilidad.
- Rendimiento.
- Operación offline.
- Mantenibilidad.
- Escalabilidad.
- Interoperabilidad.
- Gestión de errores.
- Accesibilidad.
- Eficiencia computacional.
- Licenciamiento.
- Transparencia.
- Supervisión humana.

Cuando no existan cifras, no inventes umbrales. Utiliza expresiones como:

- “[valor por validar mediante pruebas]”.
- “[SLA por definir con la IPS]”.
- “debe establecerse en la fase de validación”.

## 9. Criterios de éxito

Define criterios verificables para el proyecto.

Organízalos en una tabla:

| Código | Criterio | Indicador | Método de verificación | Meta preliminar | Estado |

Incluye criterios sobre:

- Funcionamiento local.
- Privacidad.
- Autorización y roles.
- Generación de borradores.
- Completitud documental.
- Utilidad para el profesional.
- Calidad del resumen.
- Trazabilidad de fuentes.
- Revisión humana.
- Auditoría.
- Rendimiento.
- Disponibilidad sin Internet.
- Seguridad frente a prompt injection.
- Ausencia de exposición no autorizada.
- Reproducibilidad.
- Documentación técnica.

No inventes resultados. Todas las metas deben ser preliminares o marcadas como “[por validar]”.

Distingue entre:

- Criterios de éxito del prototipo.
- Criterios de éxito institucional.
- Criterios que requerirían validación clínica o regulatoria.

## 10. Matriz inicial de riesgos basada en NIST AI RMF

Elabora una matriz completa y clara usando las funciones:

- Govern.
- Map.
- Measure.
- Manage.

La matriz debe tener como mínimo las siguientes columnas:

| ID | Función NIST AI RMF | Riesgo | Causa | Evento de riesgo | Consecuencia | Probabilidad | Impacto | Nivel inherente | Controles existentes o propuestos | Evidencia o indicador | Responsable | Tratamiento | Riesgo residual |

Utiliza una escala cualitativa coherente:

- Probabilidad: Baja, Media, Alta.
- Impacto: Bajo, Medio, Alto, Crítico.
- Nivel: Bajo, Medio, Alto, Crítico.

Incluye como mínimo estos riesgos:

1. Exposición de datos clínicos.
2. Acceso no autorizado a historias clínicas.
3. Generación de información clínica incorrecta.
4. Omisión de información relevante.
5. Presentación de contenido generado como decisión médica.
6. Alucinaciones o invención de antecedentes.
7. Resumen incompleto o descontextualizado.
8. Prompt injection en documentos o entradas.
9. Uso indebido de herramientas por parte del sistema.
10. Registro insuficiente de auditoría.
11. Pérdida, alteración o corrupción de datos.
12. Dependencia de un modelo o proveedor específico.
13. Licenciamiento inadecuado del modelo o software.
14. Falta de conectividad o indisponibilidad del sistema.
15. Rendimiento insuficiente en hardware local.
16. Sesgos o errores diferenciales en las respuestas.
17. Uso de datos reales sin autorización.
18. Retención excesiva de información.
19. Exportación o sincronización no controlada.
20. Falsa sensación de seguridad por ejecutar el sistema localmente.
21. Falta de validación clínica.
22. Uso del sistema fuera del alcance aprobado.
23. Filtración de secretos, credenciales o configuraciones.
24. Vulnerabilidades en dependencias y cadena de suministro.

Distribuye los riesgos entre Govern, Map, Measure y Manage de manera razonada.

Para cada riesgo, define controles concretos, tales como:

- Autenticación.
- Control de acceso por roles.
- Principio de mínimo privilegio.
- Cifrado en reposo y tránsito cuando aplique.
- Aislamiento del entorno.
- Uso de datos sintéticos o anonimizados.
- Validación humana obligatoria.
- Mensajes de advertencia.
- Pruebas de prompt injection.
- Registro de auditoría.
- Versionamiento.
- Copias de respaldo.
- Pruebas de recuperación.
- Inventario de modelos.
- Revisión de licencias.
- Evaluación de calidad.
- Model cards y data cards.
- Retención y eliminación controlada.
- Aprobación antes de exportar.
- Monitoreo y revisión periódica.

Aclara que la ejecución local reduce algunos riesgos de transferencia externa, pero no elimina riesgos internos, de acceso, de configuración, de software malicioso, de errores del modelo ni de uso indebido.

## 11. Gobernanza, privacidad y uso responsable

Desarrolla lineamientos preliminares para:

- Responsabilidad humana.
- Consentimiento y autorización.
- Clasificación de la información.
- Uso de datos sintéticos, públicos o anonimizados.
- Acceso basado en roles.
- Propósito limitado.
- Minimización de datos.
- Retención limitada.
- Trazabilidad.
- Transparencia frente al usuario.
- Identificación de contenido generado.
- Prohibición de uso para diagnóstico o tratamiento autónomo.
- Gestión de incidentes.
- Revisión de cambios en modelos.
- Gestión de licencias.
- Supervisión institucional.
- Procedimientos de contingencia.

No presentes asesoría jurídica definitiva. Indica que los controles deben ser revisados por la IPS, su responsable de protección de datos y los asesores jurídicos o de cumplimiento correspondientes.

## 12. Supuestos, dependencias y preguntas abiertas

### 12.1 Supuestos

Incluye supuestos como:

- La IPS autorizará el análisis del proceso.
- Existirá participación de personal médico.
- Se trabajará inicialmente con datos sintéticos, anonimizados o autorizados.
- Habrá un entorno local o institucional controlado.
- Se podrá identificar una muestra de documentos de referencia.
- La solución será un apoyo y no un sustituto del profesional.

### 12.2 Dependencias

Incluye:

- Disponibilidad de hardware.
- Participación de la IPS.
- Políticas de seguridad.
- Acceso a documentación autorizada.
- Definición de roles.
- Disponibilidad de personal clínico.
- Revisión jurídica y de protección de datos.
- Selección y licencia del modelo.
- Capacidad institucional de soporte.

### 12.3 Preguntas abiertas

Formula preguntas que deben resolverse antes de construir el prototipo, por ejemplo:

- ¿Qué estructura de nota clínica utiliza la IPS?
- ¿Qué campos son obligatorios?
- ¿Qué tipos de consulta se priorizarán?
- ¿Qué usuarios podrán utilizar el sistema?
- ¿Qué datos podrán emplearse en el laboratorio?
- ¿La solución debe integrarse con un sistema existente?
- ¿Qué mecanismos de autenticación están disponibles?
- ¿Qué hardware puede asignarse?
- ¿Qué documentos podrán formar parte de la base RAG?
- ¿Qué política de retención aplica?
- ¿Qué indicadores utiliza actualmente la IPS?
- ¿Cómo se medirá una posible reducción de inconsistencias?
- ¿Qué nivel de revisión clínica se exigirá?
- ¿Qué procedimiento se seguirá ante un incidente?

## 13. Conclusiones preliminares

Redacta entre cuatro y seis conclusiones que:

- Resuman el problema.
- Justifiquen la pertinencia del enfoque local-first.
- Destaquen que la privacidad no se resuelve únicamente con procesamiento local.
- Señalen la necesidad de supervisión humana.
- Reconozcan que la solución debe validarse con usuarios reales.
- Conecten el proyecto con las competencias del Módulo 1.

No afirmes que el proyecto ya resolvió el problema ni que está listo para producción.

## 14. Referencias preliminares

Incluye referencias en formato APA 7.ª edición únicamente de fuentes institucionales o normativas pertinentes, por ejemplo:

- National Institute of Standards and Technology. NIST AI Risk Management Framework 1.0.
- National Institute of Standards and Technology. Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile.
- UNESCO. Recommendation on the Ethics of Artificial Intelligence.
- Congreso de Colombia. Ley 1581 de 2012.
- Ministerio de Salud y Protección Social de Colombia, cuando corresponda.
- Documento CONPES 4144 de 2025, si la referencia se utiliza.
- Documentación oficial de las herramientas únicamente si se mencionan como tecnologías de referencia.

No inventes autores, fechas, títulos, URLs ni datos bibliográficos. Si no puedes verificar un dato bibliográfico, marca la referencia como:

“[Referencia por validar]”.

# REGLAS DE REDACCIÓN

1. Escribe en español colombiano, con tono profesional, académico y técnico.

2. Utiliza tercera persona o redacción impersonal.

3. No escribas como publicidad comercial.

4. No prometas beneficios que no hayan sido demostrados.

5. No inventes estadísticas, nombres institucionales, diagnósticos, prevalencias, indicadores ni resultados.

6. Diferencia claramente entre:
   - Hechos proporcionados.
   - Supuestos.
   - Propuestas.
   - Riesgos.
   - Datos por validar.

7. No presentes el sistema como capaz de diagnosticar, prescribir, decidir tratamientos o reemplazar al médico.

8. No utilices datos reales de pacientes como si estuvieran disponibles.

9. No confundas:
   - Generación de un borrador con aprobación clínica.
   - Resumen con interpretación médica.
   - Ejecución local con cumplimiento automático.
   - RAG con garantía de exactitud.
   - Privacidad técnica con autorización legal.

10. Cuando utilices términos técnicos, explícalos brevemente la primera vez.

11. Mantén consistencia terminológica en todo el documento. Utiliza preferentemente:
   - “asistente local de documentación clínica”.
   - “historia clínica”.
   - “profesional autorizado”.
   - “revisión humana”.
   - “datos clínicos sensibles”.
   - “arquitectura local-first”.
   - “modelo de lenguaje local”.
   - “base de conocimiento autorizada”.

12. Utiliza tablas cuando faciliten la comprensión, especialmente para:
   - Actores.
   - Tipos de datos.
   - Requisitos.
   - Criterios de éxito.
   - Matriz de riesgos.

13. La matriz de riesgos debe ser específica para este proyecto, no una lista genérica de riesgos de IA.

14. La matriz debe mostrar controles accionables y responsables plausibles.

15. No agregues módulos, funcionalidades ni tecnologías que no sean necesarias para el planteamiento inicial.

16. No diseñes el proyecto como una plataforma hospitalaria completa. Mantén el alcance en una IPS de atención primaria y en un prototipo local-first.

17. El documento debe ser suficientemente detallado para servir como insumo de la etapa de diseño, pero no debe adelantarse a una validación clínica, jurídica o institucional que todavía no se ha realizado.

# CONTROL DE CALIDAD ANTES DE ENTREGAR

Antes de presentar el documento final, verifica silenciosamente que:

- El problema esté claramente delimitado.
- La pregunta de formulación sea coherente con el alcance.
- Los usuarios estén identificados.
- Los datos estén clasificados por sensibilidad.
- Exista un flujo de datos local-first.
- Los requisitos tengan códigos y criterios de aceptación.
- Los criterios de éxito sean verificables.
- La matriz incluya las cuatro funciones del NIST AI RMF.
- La matriz tenga riesgos específicos de historias clínicas y documentación clínica.
- Se incluya supervisión humana.
- Se excluya el diagnóstico y tratamiento autónomo.
- No existan cifras inventadas.
- Las incertidumbres estén marcadas.
- El tono sea de tesis y no de folleto comercial.
- Las conclusiones no excedan lo que puede afirmarse en el Módulo 1.
- Las referencias no contengan datos bibliográficos inventados.

# FORMATO DE SALIDA

Entrega únicamente el documento final completo, sin explicar el proceso de elaboración.

Usa:

- Títulos jerárquicos.
- Numeración académica.
- Tablas Markdown legibles.
- Párrafos desarrollados.
- Lenguaje formal.
- Citas parentéticas cuando corresponda.
- Referencias preliminares en APA 7.ª edición.

Al final agrega una sección breve titulada:

“Nota de validación institucional”

En ella indica que el documento debe ser revisado y validado por:

- La IPS objeto de estudio.
- Personal médico.
- El responsable de historias clínicas.
- El responsable de protección de datos.
- El área de tecnología.
- El asesor jurídico o de cumplimiento correspondiente.

Genera ahora el documento completo.
