# Ecosistema de Automatización IA para Atención al Cliente de un Gimnasio

Proyecto final de Coderhouse orientado a la construcción de un ecosistema autónomo de automatización con IA.

## Tecnologías utilizadas

- n8n
- Airtable
- OpenAI
- Gmail

## Caso de uso

El sistema recibe consultas de clientes de un gimnasio por Gmail, valida la información de entrada, clasifica la intención mediante IA, consulta una base de conocimiento en Airtable y genera una respuesta.

Las consultas simples se responden automáticamente.

Las consultas sensibles, como bajas, reclamos, quejas o cobros, requieren aprobación humana antes de enviar una respuesta al cliente.

El flujo incorpora además manejo de errores, registro de logs, trazabilidad y controles para evitar bucles automáticos.

## Arquitectura general

Gmail Trigger  
→ Validación de datos  
→ Registro de consulta en Airtable  
→ Clasificación con GPT  
→ Consulta de base de conocimiento  
→ Redacción con GPT  
→ Evaluación HITL  
→ Respuesta automática o aprobación humana  
→ Actualización de estado  
→ Registro en Log Ejecuciones  
→ Actualización automática de métricas

## Base de datos

### Consultas

https://airtable.com/appCbkilOBqeZTMza/shrzdiTotdICBItYH/tblQ9obBzD4jdPxXM

### Conocimiento

https://airtable.com/appCbkilOBqeZTMza/shrzdiTotdICBItYH/tblhli6TwYpYL4D0W/viwtmyrJ2OfynW4Ec

### Log Ejecuciones

https://airtable.com/appCbkilOBqeZTMza/shrzdiTotdICBItYH/tbligrUS8pEG09LpF/viwABZGXFGDK2TmM1

### Métricas

https://airtable.com/appCbkilOBqeZTMza/shrzdiTotdICBItYH/tblG8AMUUAZcMGZrr/viwEHpljwaiAaf6D1

La tabla Métricas consolida automáticamente los resultados registrados en Log Ejecuciones y permite visualizar indicadores como cantidad total de ejecuciones, ejecuciones exitosas, errores, revisiones manuales, casos HITL y tasas de desempeño.

## Dashboard de Control

El dashboard de control se basa en la tabla Métricas de Airtable, donde se concentran los principales KPIs del sistema y la tasa de errores.

https://airtable.com/appCbkilOBqeZTMza/shrzdiTotdICBItYH/tblG8AMUUAZcMGZrr/viwEHpljwaiAaf6D1

El dashboard permite monitorear KPIs del sistema, resultados de las ejecuciones, intervenciones humanas y tasa de errores.

## Documentación

- Diagrama de arquitectura
- Estructuras de datos y esquemas JSON
- Optimización de costos
- Seguridad y resiliencia

## Workflow

El archivo técnico exportado desde n8n se encuentra en:

`workflow/workflow_atencion_gimnasio.json`

## Evidencias

El repositorio incluye evidencias de:

- Respuesta automática
- HITL aprobado
- HITL rechazado
- Error de validación
- Error del modelo GPT
- Dashboard de control
- Tablas de Airtable
- Workflow completo

## Seguridad y resiliencia

El sistema implementa:

- Validación de datos de entrada
- Filtro anti-loop en Gmail
- Manejo de errores de OpenAI
- Registro persistente de errores
- Human-in-the-loop
- Prompts dinámicos
- Tipos de datos controlados
- Trazabilidad mediante Airtable
- Respuestas dentro del mismo hilo de Gmail
