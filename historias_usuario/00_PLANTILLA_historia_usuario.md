# 📋 PLANTILLA DE HISTORIA DE USUARIO

> **💡 Propósito de esta plantilla:** Proporcionar una estructura estandarizada para documentar historias de usuario siguiendo las mejores prácticas ágiles (INVEST, Gherkin, BDD).

---

## 🎓 GUÍA DE USO DE ESTA PLANTILLA

### ¿Qué es una Historia de Usuario?

Una historia de usuario es una descripción breve y simple de una funcionalidad contada desde la perspectiva del usuario final. No es un documento técnico extenso, sino una **conversación** sobre lo que el usuario necesita y por qué.

### ¿Para qué sirve?

- ✅ **Enfocar** el desarrollo en el valor del usuario, no en la tecnología
- ✅ **Comunicar** requisitos de forma clara entre negocio, diseño y desarrollo
- ✅ **Priorizar** qué funcionalidades son más importantes
- ✅ **Estimar** el esfuerzo necesario para implementar
- ✅ **Validar** que lo construido cumple con las expectativas

### ¿Cómo usar esta plantilla?

1. **Copia** este archivo para crear una nueva historia (HU-XXX_nombre.md)
2. **Completa** cada sección según tu funcionalidad
3. **Revisa** que cumpla con los principios INVEST
4. **Refina** con el equipo en sesión de refinamiento
5. **Estima** los puntos de historia con Planning Poker
6. **Prioriza** usando método MoSCoW

### 📖 Cada sección incluye:

- 🎯 **Qué es:** Explicación del concepto
- 📌 **Para qué sirve:** Beneficio y propósito
- 💡 **Ejemplos:** Casos prácticos
- _Texto en cursiva:_ Explicaciones adicionales

---

## Información General

> **🎯 Qué es:** Metadatos que identifican y clasifican la historia dentro del proyecto.  
> **📌 Para qué sirve:** Facilitar la organización, priorización y seguimiento de las historias en el backlog.

**ID:** HU-XXX  
_Identificador único secuencial (ej: HU-001, HU-002)_

**Título:** [Título descriptivo de la historia]  
_Resumen breve y claro de la funcionalidad (máx. 10 palabras)_

**Épica/Módulo:** [RF-XXX: Nombre del módulo]  
_Agrupación funcional a la que pertenece (ej: RF-001: Gestión de Usuarios)_

**Prioridad:** [MUST / SHOULD / COULD / WON'T]  
_Clasificación MoSCoW que indica la criticidad para el negocio_

**Puntos de Historia:** [1, 2, 3, 5, 8, 13, 21]  
_Estimación relativa de esfuerzo usando secuencia Fibonacci_

**Sprint/Iteración:** [Por definir]  
_Sprint en el que se planifica implementar la historia_

---

## Historia de Usuario

> **🎯 Qué es:** Descripción de la funcionalidad desde la perspectiva del usuario final.  
> **📌 Para qué sirve:** Mantener el enfoque en el valor de negocio y las necesidades reales del usuario, no en la implementación técnica.

**Como** [tipo de usuario/rol]  
_¿Quién? - El actor que interactúa con el sistema (ej: usuario inversionista, administrador)_

**Quiero** [objetivo/acción que desea realizar]  
_¿Qué? - La acción o funcionalidad específica que necesita_

**Para** [beneficio o valor que obtiene]  
_¿Por qué? - El valor de negocio o beneficio que motiva esta necesidad_

**💡 Ejemplo:**

> **Como** usuario inversionista  
> **Quiero** ver el impacto ambiental de mis inversiones  
> **Para** sentirme motivado por el cambio positivo que genero

---

## Descripción Detallada

> **🎯 Qué es:** Contexto amplio y detalles adicionales sobre la historia.  
> **📌 Para qué sirve:** Proporcionar al equipo de desarrollo el contexto completo para tomar decisiones informadas durante la implementación.

[Contexto adicional sobre la historia, por qué es importante y cómo encaja en el sistema general]

**Incluir:**

- Contexto de negocio y motivación
- Importancia estratégica
- Consideraciones de experiencia de usuario
- Referencias a documentos o investigaciones relevantes

---

## Criterios de Aceptación

> **🎯 Qué es:** Condiciones específicas que deben cumplirse para considerar la historia como completada.  
> **📌 Para qué sirve:** Eliminar ambigüedad sobre qué debe funcionar y cómo, facilitando el testing y la validación. Formato Gherkin permite automatización con herramientas BDD (Behavior Driven Development).

### Escenario 1: [Nombre del escenario - Flujo principal]

> **💭 Tipo de escenario:** Happy Path - El flujo ideal cuando todo funciona correctamente.

```gherkin
Dado que [contexto inicial/precondiciones]
Cuando [acción del usuario]
Entonces [resultado esperado]
Y [resultado adicional si aplica]
```

### Escenario 2: [Nombre del escenario - Flujo alternativo]

> **💭 Tipo de escenario:** Camino alternativo válido - Otra forma legítima de usar la funcionalidad.

```gherkin
Dado que [contexto inicial]
Cuando [acción del usuario]
Entonces [resultado esperado]
```

### Escenario 3: [Nombre del escenario - Manejo de errores]

> **💭 Tipo de escenario:** Caso de error - Cómo el sistema maneja situaciones excepcionales.

```gherkin
Dado que [contexto inicial]
Cuando [acción que genera error]
Entonces [manejo del error y mensaje al usuario]
```

**📝 Nota sobre Gherkin:**

- **Dado que (Given):** Establece el contexto inicial o precondiciones
- **Cuando (When):** Describe la acción del usuario
- **Entonces (Then):** Define el resultado esperado
- **Y (And):** Añade condiciones o resultados adicionales

---

## Reglas de Negocio

> **🎯 Qué es:** Restricciones, políticas y lógica específica del dominio que gobiernan la funcionalidad.  
> **📌 Para qué sirve:** Documentar las reglas del negocio que el sistema debe cumplir, independientemente de la implementación técnica. Evita malentendidos sobre lógica de negocio crítica.

- **RN-XXX.1:** [Descripción de regla de negocio]  
  _Ejemplo: "El monto mínimo de inversión es $1,000 COP"_

- **RN-XXX.2:** [Descripción de regla de negocio]  
  _Ejemplo: "Los usuarios menores de 18 años no pueden crear cuenta"_

- **RN-XXX.3:** [Descripción de regla de negocio]  
  _Ejemplo: "Las comisiones se calculan como porcentaje del monto invertido"_

---

## Definición de Terminado (DoD)

> **🎯 Qué es:** Checklist de condiciones que deben cumplirse para considerar la historia 100% completa.  
> **📌 Para qué sirve:** Garantizar calidad consistente, prevenir "trabajo casi terminado", y asegurar que todos los aspectos (código, pruebas, documentación) están completos antes de marcar como Done.

- [ ] Código desarrollado y cumple con estándares  
      _Convenciones de código, clean code, revisado_

- [ ] Pruebas unitarias implementadas (cobertura mínima 80%)  
      _Tests automáticos que verifican unidades de código_

- [ ] Pruebas de integración implementadas  
      _Tests que verifican la interacción entre componentes_

- [ ] Revisión de código (code review) completada  
      _Otro desarrollador revisó y aprobó los cambios_

- [ ] Documentación técnica actualizada  
      _README, wikis, comentarios en código_

- [ ] Pruebas de aceptación pasadas por PO/usuario  
      _Product Owner valida que cumple criterios de aceptación_

- [ ] Despliegue en ambiente de pruebas  
      _Código desplegado en entorno de staging/QA_

- [ ] Sin defectos críticos o bloqueantes abiertos  
      _No hay bugs que impidan usar la funcionalidad_

---

## Notas Técnicas

> **🎯 Qué es:** Información técnica relevante para la implementación.  
> **📌 Para qué sirve:** Guiar decisiones técnicas del equipo de desarrollo sobre tecnologías, arquitectura, seguridad y performance.

**Stack/Tecnología:**  
_Tecnologías, frameworks y herramientas específicas a utilizar_

- [Tecnologías específicas a utilizar]

**Dependencias:**  
_Otras historias, servicios o APIs necesarias_

- [HU-XXX] Descripción de dependencia
- [Servicio/API externa] Descripción

**Consideraciones de Seguridad:**  
_Aspectos de seguridad, encriptación, autenticación, autorización_

- [Aspectos de seguridad relevantes]

**Consideraciones de Performance:**  
_Requisitos de rendimiento, tiempos de respuesta, optimizaciones_

- [Requisitos de rendimiento]

---

## Mockups/Wireframes

> **🎯 Qué es:** Referencias a diseños visuales de la interfaz de usuario.  
> **📌 Para qué sirve:** Alinear expectativas visuales entre diseño, desarrollo y negocio antes de implementar.

---

## Notas Técnicas

**Stack/Tecnología:**

- [Tecnologías específicas a utilizar]

**Dependencias:**

- [HU-XXX] Descripción de dependencia
- [Servicio/API externa] Descripción

**Consideraciones de Seguridad:**  
_Aspectos de seguridad, encriptación, autenticación, autorización_

- [Aspectos de seguridad relevantes]

**Consideraciones de Performance:**  
_Requisitos de rendimiento, tiempos de respuesta, optimizaciones_

- [Requisitos de rendimiento]

---

## Mockups/Wireframes

> **🎯 Qué es:** Referencias a diseños visuales de la interfaz de usuario.  
> **📌 Para qué sirve:** Alinear expectativas visuales entre diseño, desarrollo y negocio antes de implementar.

[Enlaces o referencias a diseños de UI/UX]

**Ejemplos:**

- `/diseño/pantalla-login.png`
- `https://figma.com/file/abc123`

---

## Tareas Técnicas (Subtareas)

> **🎯 Qué es:** Desglose de la historia en tareas técnicas más pequeñas y concretas.  
> **📌 Para qué sirve:** Facilitar la planificación del trabajo diario, permitir trabajo en paralelo entre desarrolladores, y hacer seguimiento granular del progreso.

- [ ] [Tarea 1: Descripción]  
      _Ej: "Crear tabla de usuarios en base de datos"_

- [ ] [Tarea 2: Descripción]  
      _Ej: "Implementar endpoint POST /api/auth/register"_

- [ ] [Tarea 3: Descripción]  
      _Ej: "Crear formulario de registro en frontend"_

- [ ] [Tarea 4: Descripción]  
      _Ej: "Implementar validaciones de campos"_

---

## Casos de Prueba Principales

> **🎯 Qué es:** Escenarios específicos de testing con datos de entrada y resultados esperados.  
> **📌 Para qué sirve:** Guiar al equipo de QA en las pruebas, asegurar cobertura de casos importantes, y facilitar testing manual o automatizado.

1. **CP-XXX.1:** [Descripción del caso de prueba]

   - **Entrada:** [Datos de entrada]  
     _Ej: "Usuario ingresa email válido y contraseña correcta"_
   - **Resultado esperado:** [Salida esperada]  
     _Ej: "Sistema autentica usuario y redirige al dashboard"_

2. **CP-XXX.2:** [Descripción del caso de prueba]
   - **Entrada:** [Datos de entrada]  
     _Ej: "Usuario ingresa email inválido"_
   - **Resultado esperado:** [Salida esperada]  
     _Ej: "Sistema muestra error: 'Email inválido'"_

---

## Validación INVEST

> **🎯 Qué es:** Validación contra los principios INVEST para asegurar que la historia está bien definida.  
> **📌 Para qué sirve:** Garantizar que las historias sean de alta calidad, estimables y entreguen valor. Previene historias mal definidas que causan problemas durante el desarrollo.

**Principios INVEST:**

- [x] **I**ndependiente: ¿Puede desarrollarse de forma autónoma?  
      _La historia no depende fuertemente de otras para poder desarrollarse_

- [x] **N**egociable: ¿Es flexible en su implementación?  
      _Los detalles técnicos son discutibles, no está sobre-especificada_

- [x] **V**aliosa: ¿Aporta valor al usuario/negocio?  
      _Tiene un beneficio claro y medible para el usuario o el negocio_

- [x] **E**stimable: ¿Se puede estimar el esfuerzo?  
      _El equipo tiene suficiente información para estimar puntos de historia_

- [x] **S**mall (Pequeña): ¿Se completa en un sprint?  
      _El tamaño permite completarla en una iteración (típicamente 1-2 semanas)_

- [x] **T**esteable: ¿Se pueden verificar los criterios de aceptación?  
      _Los criterios son claros y verificables mediante pruebas_

---

## Historial de Cambios

> **🎯 Qué es:** Registro cronológico de modificaciones al documento de la historia.  
> **📌 Para qué sirve:** Mantener trazabilidad de cambios, entender la evolución de los requisitos, y auditar modificaciones.

| Fecha      | Versión | Autor    | Descripción              |
| ---------- | ------- | -------- | ------------------------ |
| DD/MM/YYYY | 1.0     | [Nombre] | Creación inicial         |
| DD/MM/YYYY | 1.1     | [Nombre] | [Descripción del cambio] |

---

## 📚 GLOSARIO DE TÉRMINOS

> **Referencia rápida para entender los conceptos clave:**

- **User Story (Historia de Usuario):** Descripción simple de una funcionalidad desde la perspectiva del usuario
- **Gherkin:** Lenguaje de especificación de comportamiento (Given-When-Then)
- **BDD (Behavior Driven Development):** Desarrollo guiado por comportamiento
- **INVEST:** Principios de calidad para historias (Independent, Negotiable, Valuable, Estimable, Small, Testable)
- **MoSCoW:** Método de priorización (Must, Should, Could, Won't)
- **DoD (Definition of Done):** Definición de Terminado
- **Sprint:** Iteración de tiempo fijo en Scrum (típicamente 1-2 semanas)
- **Puntos de Historia:** Medida relativa de esfuerzo/complejidad
- **Épica:** Agrupación de historias relacionadas
- **Criterios de Aceptación:** Condiciones que deben cumplirse para dar por terminada la historia
- **Reglas de Negocio:** Políticas y restricciones del dominio del negocio
- **Happy Path:** Flujo ideal cuando todo funciona correctamente

---

**💡 Última actualización de la plantilla:** 23 de octubre de 2025  
**📌 Versión:** 2.0 (con explicaciones pedagógicas)
