# Hallazgo de Seguridad: [Nombre]

| Campo | Valor |
| --- | --- |
| **Nombre** | [Título corto: tipo de vulnerabilidad + dónde. Ej.: IDOR en el detalle de ventas] |
| **Categoría** | [OWASP Top 10 + CWE. Ej.: A01:2021 Broken Access Control / CWE-639] |
| **Versión** | [Versión del software afectado, o N/A (No Aplica)] |
| **Vector CVSS** | [Score (Severidad) - `CVSS:3.1/AV:_/AC:_/PR:_/UI:_/S:_/C:_/I:_/A:_`] |
| **URL afectada(s)** | [Una URL por línea, con método y parámetro] |

## Descripción

> Resumen ejecutivo. Para alguien que no es técnico, en 3 o 4 oraciones.

[Qué problema tiene el sistema, qué puede hacer un atacante, a quién perjudica y qué tan urgente es corregirlo.]

## Detalles de la vulnerabilidad

> Detalle técnico. Para el desarrollador que lo tiene que arreglar.

[Qué hace la aplicación, qué control falta o falla y por qué eso es explotable.]

**Justificación del CVSS:**

| AV | AC | PR | UI | S | C | I | A |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [_] | [_] | [_] | [_] | [_] | [_] | [_] | [_] |

- [Una línea por cada métrica que no sea obvia, explicando por qué se eligió ese valor.]

## Cómo se detectó

> Prueba de Concepto. Cualquiera tiene que poder repetirla siguiendo los pasos.

**Requisitos:** [Herramientas, cuentas o datos que hacen falta.]

1. [Paso 1]
2. [Paso 2]
3. [Paso 3]

```http
[Petición enviada]
```

**Resultado esperado:** [Lo que la aplicación debería hacer.]
**Resultado obtenido:** [Lo que la aplicación hizo.]

## Recomendaciones

1. [Cambio que corrige la causa raíz.]
2. [Medidas complementarias.]

**Verificación:** [Qué repetir para confirmar que quedó corregido.]

## Evidencias

![Descripción de la captura](./evidencia_1.png)
