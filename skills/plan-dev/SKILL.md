---
name: plan-dev
description: Plan de desarrollo detallado. Recolecta requisitos, analiza el contexto, diseña la arquitectura y produce un plan de implementación paso a paso. Usar cuando el usuario pide planear un feature, refactor, o desarrollo antes de escribir código. NUNCA crea ni edita archivos — solo investiga, razona y documenta el plan.
---

# Plan Dev — Planeación de Desarrollo

## Propósito

Este skill guía un proceso de planeación exhaustivo **sin tocar código**. Su único objetivo es recolectar información, analizar el contexto existente, diseñar la solución y producir un plan de implementación detallado que el usuario pueda revisar y aprobar antes de ejecutar.

**Regla de oro: NO crear, editar, ni modificar archivos. Solo leer, analizar y documentar el plan.**

---

## Fases del Proceso

Sigue estas fases en orden. No saltes ninguna sin confirmar con el usuario.

### Fase 1 — Descubrimiento

Recolecta toda la información necesaria para entender el problema:

1. **Clarificar el objetivo**: Si hay ambigüedad, haz preguntas. No asumas.
   - ¿Qué problema resuelve?
   - ¿Cuál es el resultado esperado?
   - ¿Qué criterios definen "terminado"?

2. **Identificar stakeholders y restricciones**:
   - ¿Hay deadlines, presupuesto, o dependencias externas?
   - ¿Qué tecnologías deben usarse (o evitarse)?
   - ¿Qué no debe cambiar (legacy, convenciones, APIs públicas)?

3. **Explorar el contexto existente**:
   - Lee archivos relevantes: configuración, dependencias, estructura del proyecto
   - Identifica patrones, convenciones y estilos usados en el código
   - Busca implementaciones similares que puedan servir de referencia
   - Revisa tests existentes para entender comportamiento esperado

4. **Documentar hallazgos**: Resume lo encontrado en bullets claros.

### Fase 2 — Diseño de la Solución

Con la información recolectada, diseña la solución:

1. **Arquitectura general**:
   - ¿Qué componentes/capas/funciones se necesitan?
   - ¿Cómo se relacionan entre sí?
   - ¿Qué flujos de datos hay (entrada → procesamiento → salida)?

2. **Decisiones técnicas**:
   - Justifica cada decisión relevante (¿por qué X y no Y?)
   - Identifica tradeoffs y riesgos
   - Si hay múltiples enfoques viables, preséntalos con pros/cons

3. **Diseño detallado por componente**:
   - Para cada pieza nueva o modificada: ubicación, interfaz, responsabilidad
   - Tipos de datos, firmas de funciones, estructura de archivos
   - Cómo se integra con el código existente

4. **Casos límite y errores**:
   - ¿Qué puede fallar?
   - ¿Cómo se manejan estados vacíos, nulos, timeouts, fallos de red?
   - ¿Hay consideraciones de seguridad o concurrencia?

### Fase 3 — Plan de Implementación

Traduce el diseño a una secuencia concreta de pasos:

1. **Divide en tareas atómicas**: Cada paso debe ser verificable independientemente.
2. **Ordena por dependencias**: ¿Qué debe existir primero?
3. **Para cada paso, especifica**:
   - Archivo(s) a crear o modificar
   - Qué cambio específico se hará (no "mejorar X", sino "agregar función Y en Z.ts")
   - Cómo verificar que el paso quedó bien (test manual, test automático, criterio de aceptación)
4. **Estima complejidad**: ¿Hay pasos particularmente riesgosos o inciertos?

---

## Entregable Final

Al terminar las tres fases, presenta al usuario un documento estructurado:

```markdown
# Plan de Implementación: [Título]

## 1. Resumen
[2-3 frases: qué se va a hacer y por qué]

## 2. Contexto y Hallazgos
- [Lo que se descubrió en Fase 1]

## 3. Diseño
- Arquitectura: [diagrama textual o descripción]
- Decisiones clave: [qué y por qué]
- Componentes: [detalle por pieza]

## 4. Plan Paso a Paso
1. [Paso 1] → Verificar: [criterio]
2. [Paso 2] → Verificar: [criterio]
...

## 5. Riesgos y Alternativas
- [Riesgo 1]: [mitigación]
- Alternativa considerada: [por qué se descartó]
```

El plan debe ser tan detallado que otro desarrollador pueda ejecutarlo sin ambigüedad.

---

## Anti-Patrones (NO hacer)

- ❌ Empezar a codear "para probar una idea"
- ❌ Asumir requisitos sin confirmar con el usuario
- ❌ Proponer refactors no relacionados con el objetivo
- ❌ Usar `edit` o `write` en archivos del proyecto
- ❌ Ejecutar comandos que modifiquen el código (git commit, npm install global, etc.)
- ❌ Dejar pasos vagos como "implementar la lógica" sin detallar

---

## Herramientas Permitidas

Durante la planeación puedes usar:
- `read` — leer archivos del proyecto
- `bash` — comandos de solo lectura: `ls`, `grep`, `find`, `git log`, `cat`, etc.
- `web_search` / `web_fetch` — investigar documentación externa

**Prohibido explícitamente**: `edit`, `write`, `bash` con comandos destructivos (rm, mv, redirección con >, etc.)
