# Objetivo 3: Armado de Plantilla Base de Reporte

## Descripción

El reporte es lo que el cliente se lleva de un pentest. Si una vulnerabilidad está bien encontrada pero mal explicada, es muy probable que nadie la corrija. Por eso armé una plantilla para usar con cada hallazgo de acá en adelante.

La plantilla está en [plantilla_reporte.md](plantilla_reporte.md). La basé en el formulario de alta de tickets que usamos en el curso, con los mismos campos, para poder pasarla directo al formulario. Cada hallazgo va en un ticket propio, así se puede asignar a alguien, seguir su estado y cerrarlo cuando se corrige.

## Desarrollo

### Estructura

Cada campo del formulario cubre una de las secciones que tiene que tener el reporte:

| Campo | Sección del reporte | Quién lo lee |
| --- | --- | --- |
| Nombre, Categoría, Versión y URL afectada(s) | Encabezado | Todos |
| Descripción | Resumen ejecutivo | Directivos |
| Detalles de la vulnerabilidad | Detalles técnicos | Desarrolladores |
| Vector CVSS | Métricas CVSS | Equipo de seguridad |
| Cómo se detectó + Evidencias | Prueba de concepto | Desarrolladores y QA |
| Recomendaciones | Remediación | Desarrolladores |

El encabezado tiene lo mínimo para entender el hallazgo de un vistazo: qué es, de qué tipo, dónde está y qué tan grave es. En Categoría pongo la categoría del OWASP Top 10 y el CWE, que es el idioma común que vi en el [Objetivo 1](../Objetivo_1_Estandarizacion_de_Vulnerabilidades/objetivo_1_estandarizacion_de_vulnerabilidades.md).

La Descripción está pensada para alguien que no es técnico. En tres o cuatro oraciones cuenta qué problema hay, qué podría pasar y qué tan urgente es arreglarlo.

En Detalles de la vulnerabilidad va la explicación técnica, junto con una tabla chica que justifica cada métrica del CVSS. Así no queda solo el número, que siempre se puede discutir, y cualquiera puede revisar el cálculo. Las métricas de impacto salen del análisis de la triada del [Objetivo 2](../Objetivo_2_Analisis_Triada_CIA/objetivo_2_analisis_triada_cia.md).

Cómo se detectó es la prueba de concepto: qué hace falta, los pasos numerados, la petición que se envió y qué debería haber pasado frente a lo que pasó. Las capturas van en Evidencias.

Por último, Recomendaciones explica cómo corregirlo y cómo comprobar que quedó resuelto.

### ¿Qué le aporta al que lee el ticket?

Cada persona encuentra rápido lo que necesita y puede dejar de leer ahí. Un directivo con la descripción y el score ya entiende el riesgo y decide si hay que priorizarlo. El desarrollador tiene la URL, el parámetro, la causa y la solución, sin tener que volver a preguntarle nada al pentester. Y QA puede reproducir la falla con los pasos, y después repetirlos para confirmar que se arregló.

Al usar estándares como CWE y CVSS, el ticket además se entiende igual dentro y fuera de la empresa.

## Conclusiones

Hice la plantilla corta a propósito, para que cada campo responda una sola pregunta. Va de lo general a lo particular: qué es, por qué importa, cómo funciona, cómo se reproduce y cómo se arregla.

Como está en Markdown, la puedo versionar en Git y copiar para cada hallazgo. En el [Objetivo 4](../Objetivo_4_Primer_Reporte_Tecnico/objetivo_4_primer_reporte_tecnico.md) la uso por primera vez con lo que encontré en el laboratorio Ventas.
