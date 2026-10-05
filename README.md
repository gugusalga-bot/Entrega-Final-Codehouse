# Entrega-Final-Codehouse
# Ecosistema de Triage de Tickets de Soporte con IA
### Proyecto Final — Coderhouse

## Descripción

Sistema de automatización que recibe consultas de soporte por correo, las clasifica con IA (categoría, prioridad, sentimiento), genera una respuesta sugerida y la envía al cliente solo después de que una persona del equipo la revisa y aprueba. Ningún mensaje llega a un cliente real sin intervención humana.

Construido sobre los 4 componentes obligatorios del proyecto:

| Categoría | Herramienta |
|---|---|
| Orquestador | n8n |
| Base de datos | Airtable |
| Procesamiento IA | Google Gemini |
| Canal de salida | Slack + Gmail |

## Arquitectura: dos workflows

El sistema está dividido en dos workflows en vez de uno solo, para evitar depender de un túnel público (como ngrok) hacia una instancia de n8n corriendo en una computadora local. El detalle de esta decisión está documentado en `Documentacion_de_seguridad_y_resiliencia.docx`.

- **WF1 — Intake, Triage y Notificación**: recibe el correo, lo clasifica con IA, crea el ticket en Airtable y avisa por Slack al área correspondiente.
- **WF2 — Aprobación y Entrega**: detecta por polling cuándo un ticket fue aprobado en Airtable y recién ahí envía la respuesta al cliente por Gmail (o notifica que la respuesta debe redactarse a mano, si fue rechazada).

## Entregables

| # | Entregable | Archivo(s) |
|---|---|---|
| 1 | Diagrama de arquitectura | `Workflow 1.pdf`, `Workflow 2.pdf`, `Workflow 1 - JSON.docx`, `Workflow 2 - JSON.docx` |
| 2 | Manual operativo de datos | Parte A — Esquema de Airtable: `Tabla_de_tickets.pdf`, `Tabla_de_errores.pdf`, `Tabla_area_de_soporte.pdf` · Parte B — Esquemas JSON de integración: `Esquemas_JSON_de_transferencia_de_las_integraciones.docx` |
| 3 | Matriz de costos y optimización | `Matriz_de_costos_y_optimizacion.docx` |
| 4 | Documentación de seguridad y resiliencia | `Documentacion_de_seguridad_y_resiliencia.docx` |
| 5 | Dashboard de control | `[link a la interfaz de Airtable o archivo exportado]` |

## Autor

Guadalupe Salgado — Proyecto Final, Coderhouse
