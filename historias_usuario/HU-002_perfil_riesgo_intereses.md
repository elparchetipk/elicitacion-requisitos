# 📋 HISTORIA DE USUARIO - Perfil de Riesgo e Intereses Ambientales

## Información General

**ID:** HU-002  
**Título:** Configuración de perfil financiero y motivaciones ambientales  
**Épica/Módulo:** RF-001: Gestión de Usuarios y Onboarding  
**Prioridad:** MUST (Crítico)  
**Puntos de Historia:** 5  
**Sprint/Iteración:** Sprint 1

---

## Historia de Usuario

**Como** usuario registrado en la plataforma  
**Quiero** completar un cuestionario sobre mi perfil financiero y mis motivaciones ambientales  
**Para** recibir recomendaciones personalizadas de inversión alineadas con mis intereses de sostenibilidad y capacidad de riesgo

---

## Descripción Detallada

Esta historia implementa el onboarding financiero y ambiental del usuario. A través de un cuestionario interactivo (máximo 15 preguntas), el sistema recopila información sobre:

- Experiencia en inversiones
- Ingresos mensuales aproximados
- Tolerancia al riesgo financiero
- Motivaciones ambientales (cambio climático, conservación, energías renovables, justicia social)

El algoritmo de perfilamiento clasifica automáticamente al usuario y personaliza toda su experiencia en la plataforma (dashboard, recomendaciones, contenido educativo).

---

## Criterios de Aceptación

### Escenario 1: Completar cuestionario de perfil financiero y ambiental

```gherkin
Dado que soy un usuario que acaba de verificar mi cuenta
Cuando accedo al cuestionario de perfil
Y respondo las preguntas sobre mis ingresos, experiencia y tolerancia al riesgo
Y selecciono mis motivaciones ambientales principales
Entonces el sistema calcula y asigna mi perfil de riesgo (Conservador/Moderado/Agresivo)
Y personaliza mi dashboard con proyectos relevantes
Y guarda mis preferencias para futuras recomendaciones
```

### Escenario 2: Usuario con ingresos bajos recibe opciones apropiadas

```gherkin
Dado que soy un usuario con ingresos mensuales menores a 1 salario mínimo
Cuando completo el cuestionario de perfil
Entonces el sistema me clasifica considerando mi capacidad de inversión limitada
Y prioriza opciones de microinversión (desde $1,000 COP)
Y sugiere contenido educativo sobre construcción de patrimonio
```

### Escenario 3: Modificar perfil posteriormente

```gherkin
Dado que ya tengo un perfil configurado
Cuando accedo a la configuración de mi perfil
Y actualizo mis respuestas sobre tolerancia al riesgo o motivaciones
Entonces el sistema recalcula mi perfil
Y actualiza las recomendaciones inmediatamente
Y mantiene un historial de cambios de perfil
```

### Escenario 4: Usuario abandona cuestionario a mitad

```gherkin
Dado que estoy respondiendo el cuestionario de perfil
Cuando salgo de la página sin completarlo
Entonces el sistema guarda temporalmente mis respuestas parciales
Y al reingresar, me ofrece continuar desde donde lo dejé
Y las respuestas guardadas expiran después de 24 horas
```

### Escenario 5: Validación de respuestas inconsistentes

```gherkin
Dado que estoy completando el cuestionario
Cuando selecciono "sin experiencia en inversiones" pero luego "tolerancia alta al riesgo"
Entonces el sistema muestra una advertencia sobre la inconsistencia
Y ofrece información educativa sobre la relación experiencia-riesgo
Y permite confirmar o modificar la selección
```

---

## Reglas de Negocio

- **RN-002.1:** El cuestionario debe tener máximo 15 preguntas obligatorias
- **RN-002.2:** Clasificación de perfiles:
  - **Conservador:** Ingresos <2 SMMLV, sin experiencia, baja tolerancia al riesgo
  - **Moderado:** Ingresos 2-5 SMMLV, experiencia básica, tolerancia media
  - **Agresivo:** Ingresos >5 SMMLV, experiencia avanzada, alta tolerancia
- **RN-002.3:** Las motivaciones ambientales son multi-selección (hasta 5 opciones)
- **RN-002.4:** El usuario puede modificar su perfil en cualquier momento
- **RN-002.5:** Los cambios de perfil no afectan inversiones existentes, solo nuevas recomendaciones
- **RN-002.6:** El perfil debe completarse antes de realizar la primera inversión

---

## Definición de Terminado (DoD)

- [x] Código desarrollado y cumple con estándares
- [x] Pruebas unitarias implementadas (cobertura mínima 80%)
- [x] Algoritmo de clasificación de perfil validado por área de negocio
- [x] Revisión de código (code review) completada
- [x] Documentación técnica actualizada
- [x] Pruebas de aceptación pasadas por PO
- [x] Despliegue en ambiente de pruebas
- [x] Sin defectos críticos o bloqueantes abiertos
- [x] UX validada con pruebas de usabilidad

---

## Notas Técnicas

**Stack/Tecnología:**

- Backend: API REST para guardar respuestas y calcular perfil
- Frontend: Formulario multi-paso con progress bar
- Base de datos: Tabla de perfiles con versionado
- Algoritmo de scoring para clasificación automática

**Dependencias:**

- [HU-001] Registro de usuario debe estar completo
- Sistema de recomendaciones para aplicar personalización
- Contenido de proyectos disponibles categorizados

**Consideraciones de Seguridad:**

- Información financiera sensible debe encriptarse
- Solo el usuario puede ver sus respuestas completas
- Logs de auditoría para cambios de perfil

**Consideraciones de Performance:**

- Cálculo de perfil debe ser instantáneo (<1 segundo)
- Caché de perfiles calculados
- Actualización async de recomendaciones si toma tiempo

---

## Mockups/Wireframes

- Mockup: `/diseño/perfil-paso-1-financiero.png`
- Mockup: `/diseño/perfil-paso-2-ambiental.png`
- Mockup: `/diseño/perfil-resultado-clasificacion.png`

---

## Tareas Técnicas (Subtareas)

- [ ] Diseñar tabla de perfiles y respuestas de cuestionario
- [ ] Crear endpoint POST /api/v1/users/profile
- [ ] Implementar algoritmo de clasificación de perfil
- [ ] Diseñar cuestionario multi-paso en frontend
- [ ] Implementar progress bar y navegación entre pasos
- [ ] Crear sistema de guardado temporal de respuestas parciales
- [ ] Implementar validación de consistencia de respuestas
- [ ] Crear endpoint PATCH /api/v1/users/profile para actualizaciones
- [ ] Integrar perfil con sistema de recomendaciones
- [ ] Crear visualización de resultado de perfil
- [ ] Implementar pruebas del algoritmo de clasificación
- [ ] Crear documentación de preguntas y lógica de scoring

---

## Casos de Prueba Principales

1. **CP-002.1: Clasificación perfil conservador**

   - **Entrada:** Ingresos bajos, sin experiencia, baja tolerancia riesgo
   - **Resultado esperado:** Perfil "Conservador" asignado

2. **CP-002.2: Clasificación perfil agresivo**

   - **Entrada:** Ingresos altos, experiencia avanzada, alta tolerancia
   - **Resultado esperado:** Perfil "Agresivo" asignado

3. **CP-002.3: Múltiples motivaciones ambientales**

   - **Entrada:** Selección de 5 motivaciones diferentes
   - **Resultado esperado:** Todas guardadas, recomendaciones diversificadas

4. **CP-002.4: Recuperación de cuestionario parcial**

   - **Entrada:** Usuario completa 50%, sale y vuelve
   - **Resultado esperado:** Progreso guardado, puede continuar

5. **CP-002.5: Modificación de perfil existente**

   - **Entrada:** Usuario cambia tolerancia de baja a alta
   - **Resultado esperado:** Perfil actualizado, nuevas recomendaciones

6. **CP-002.6: Validación de inconsistencias**
   - **Entrada:** Sin experiencia + alta tolerancia al riesgo
   - **Resultado esperado:** Advertencia mostrada, confirmación requerida

---

## Validación INVEST

- [x] **I**ndependiente: Depende de HU-001 pero luego es independiente
- [x] **N**egociable: Número y tipo de preguntas puede ajustarse
- [x] **V**aliosa: Clave para personalización y experiencia del usuario
- [x] **E**stimable: 5 puntos por complejidad del algoritmo y UX multi-paso
- [x] **S**mall (Pequeña): Completable en un sprint
- [x] **T**esteable: Algoritmo y flujo claramente verificables

---

## Historial de Cambios

| Fecha      | Versión | Autor              | Descripción                         |
| ---------- | ------- | ------------------ | ----------------------------------- |
| 22/10/2025 | 1.0     | Equipo de Análisis | Creación inicial basada en RF-001.2 |
