# 📋 HISTORIA DE USUARIO - Inversión en Fondos Verdes

## Información General

**ID:** HU-003  
**Título:** Invertir en fondos diversificados de proyectos ambientales  
**Épica/Módulo:** RF-002: Productos Financieros Verdes  
**Prioridad:** MUST (Crítico)  
**Puntos de Historia:** 13  
**Sprint/Iteración:** Sprint 2

---

## Historia de Usuario

**Como** usuario inversionista con perfil configurado  
**Quiero** explorar y invertir en fondos verdes diversificados  
**Para** obtener retornos financieros mientras genero impacto ambiental positivo con montos accesibles desde $1,000 COP

---

## Descripción Detallada

Esta historia implementa la funcionalidad core del producto: la inversión en fondos verdes. Los usuarios pueden explorar un catálogo de fondos diversificados, cada uno con información detallada sobre composición, rendimiento histórico, nivel de riesgo e impacto ambiental esperado.

La democratización financiera es clave: inversión mínima de $1,000 COP permite que cualquier persona participe. El proceso debe ser transparente, mostrando claramente comisiones, riesgos y proyecciones. Las órdenes de inversión se ejecutan inmediatamente y el portafolio se actualiza en tiempo real.

---

## Criterios de Aceptación

### Escenario 1: Explorar catálogo de fondos verdes

```gherkin
Dado que soy un usuario autenticado con perfil completo
Cuando accedo a la sección "Fondos de Inversión"
Entonces veo un catálogo con fondos disponibles
Y cada fondo muestra: nombre, rendimiento histórico, nivel de riesgo, impacto ambiental
Y puedo filtrar por: tipo de proyecto, nivel de riesgo, rendimiento esperado
Y los fondos recomendados para mi perfil aparecen destacados
```

### Escenario 2: Ver detalles completos de un fondo

```gherkin
Dado que estoy explorando el catálogo de fondos
Cuando selecciono un fondo específico
Entonces veo información detallada: composición de proyectos, distribución geográfica, historial de rendimiento
Y veo métricas de impacto: toneladas CO2 evitadas, árboles plantados, familias beneficiadas
Y veo la estructura de comisiones claramente especificada
Y veo reseñas y comentarios de otros inversionistas
```

### Escenario 3: Invertir monto mínimo exitosamente

```gherkin
Dado que estoy en la página de detalles de un fondo
Y tengo saldo disponible de al menos $1,000 COP
Cuando ingreso $1,000 como monto a invertir
Y confirmo la inversión con mi método de pago
Entonces el sistema procesa el pago inmediatamente
Y actualiza mi portafolio mostrando la nueva inversión
Y envía confirmación por email con comprobante
Y muestra el impacto ambiental proyectado de mi inversión
```

### Escenario 4: Intentar invertir con fondos insuficientes

```gherkin
Dado que quiero invertir en un fondo
Cuando ingreso un monto mayor a mi saldo disponible
Entonces el sistema muestra: "Saldo insuficiente. Tu saldo actual: $X"
Y ofrece opciones: "Agregar fondos" o "Ajustar monto"
Y no permite continuar con la transacción
```

### Escenario 5: Invertir monto menor al mínimo

```gherkin
Dado que estoy ingresando el monto de inversión
Cuando intento invertir menos de $1,000 COP
Entonces el sistema muestra: "El monto mínimo de inversión es $1,000 COP"
Y ajusta automáticamente el campo al mínimo permitido
Y explica la razón del mínimo (costos operativos)
```

### Escenario 6: Cálculo transparente de comisiones

```gherkin
Dado que estoy a punto de confirmar una inversión de $10,000 COP
Cuando reviso el resumen antes de confirmar
Entonces veo el desglose: Inversión: $10,000, Comisión: $X (X%), Total: $10,000 + $X
Y las comisiones están claramente explicadas
Y el monto final a pagar es el que se muestra
```

### Escenario 7: Actualización inmediata de portafolio

```gherkin
Dado que acabo de completar una inversión exitosa
Cuando accedo a mi dashboard o sección "Mi Portafolio"
Entonces veo la nueva inversión reflejada inmediatamente
Y el valor total de mi portafolio está actualizado
Y puedo ver el desglose de todas mis inversiones activas
```

---

## Reglas de Negocio

- **RN-003.1:** Inversión mínima: $1,000 COP por transacción
- **RN-003.2:** No hay inversión máxima por transacción (sujeto a límites regulatorios)
- **RN-003.3:** Comisión de administración: 0.5% - 2% anual según el fondo
- **RN-003.4:** Las inversiones son ejecutadas inmediatamente (no hay pendientes)
- **RN-003.5:** El usuario debe tener saldo suficiente antes de invertir
- **RN-003.6:** Cada inversión genera un comprobante único con ID de transacción
- **RN-003.7:** Solo usuarios con perfil completo pueden invertir
- **RN-003.8:** Cada fondo tiene capacidad máxima (cupos limitados)

---

## Definición de Terminado (DoD)

- [x] Código desarrollado y cumple con estándares
- [x] Pruebas unitarias implementadas (cobertura mínima 80%)
- [x] Pruebas de integración con pasarela de pagos
- [x] Pruebas de concurrencia para inversiones simultáneas
- [x] Revisión de código (code review) completada
- [x] Documentación técnica actualizada
- [x] Pruebas de aceptación pasadas por PO
- [x] Despliegue en ambiente de pruebas
- [x] Sin defectos críticos o bloqueantes abiertos
- [x] Validación de cálculos de comisiones por área financiera

---

## Notas Técnicas

**Stack/Tecnología:**

- Backend: API REST para transacciones (con idempotencia)
- Base de datos: Transacciones ACID para inversiones
- Frontend: Carrito de inversión con preview en tiempo real
- Integración con pasarela de pagos (PSE, tarjetas)
- Sistema de cálculo de comisiones configurable

**Dependencias:**

- [HU-001] Registro de usuario
- [HU-002] Perfil completo
- [HU-008] Integración con pasarelas de pago
- Sistema de gestión de fondos (admin)
- Base de datos de proyectos ambientales

**Consideraciones de Seguridad:**

- Transacciones con idempotency key para evitar duplicados
- Validación de saldo en servidor (no confiar en cliente)
- Encriptación de datos financieros
- Logs de auditoría completos de todas las transacciones
- Rate limiting para prevenir ataques
- Autenticación reforzada para montos altos (2FA)

**Consideraciones de Performance:**

- Índices en tabla de fondos para búsquedas rápidas
- Caché de información de fondos (actualizado cada hora)
- Procesamiento asíncrono de confirmaciones de email
- Transacciones optimistas para actualización de portafolio
- Timeout de 30 segundos para procesamiento de pago

---

## Mockups/Wireframes

- Mockup: `/diseño/catalogo-fondos-verdes.png`
- Mockup: `/diseño/detalle-fondo.png`
- Mockup: `/diseño/confirmacion-inversion.png`
- Mockup: `/diseño/comprobante-inversion.png`

---

## Tareas Técnicas (Subtareas)

- [ ] Diseñar modelo de datos para fondos e inversiones
- [ ] Crear endpoint GET /api/v1/funds para listar fondos
- [ ] Crear endpoint GET /api/v1/funds/:id para detalle
- [ ] Crear endpoint POST /api/v1/investments para nueva inversión
- [ ] Implementar sistema de cálculo de comisiones
- [ ] Implementar validación de saldo disponible
- [ ] Implementar lógica de transacciones ACID
- [ ] Crear UI de catálogo de fondos con filtros
- [ ] Crear UI de detalle de fondo con gráficos
- [ ] Crear flujo de confirmación de inversión
- [ ] Integrar con pasarela de pagos
- [ ] Implementar sistema de idempotencia
- [ ] Crear generación de comprobantes PDF
- [ ] Implementar envío de emails de confirmación
- [ ] Actualizar portafolio en tiempo real
- [ ] Crear pruebas de concurrencia
- [ ] Documentar APIs de inversión

---

## Casos de Prueba Principales

1. **CP-003.1: Inversión mínima exitosa**

   - **Entrada:** Usuario con saldo, invierte $1,000 en fondo A
   - **Resultado esperado:** Inversión procesada, portafolio actualizado, email enviado

2. **CP-003.2: Inversión con comisiones calculadas correctamente**

   - **Entrada:** Inversión de $100,000, comisión 1%
   - **Resultado esperado:** Total cobrado $101,000, reflejado correctamente

3. **CP-003.3: Rechazo por fondos insuficientes**

   - **Entrada:** Saldo $500, intento de invertir $1,000
   - **Resultado esperado:** Error claro, transacción no procesada

4. **CP-003.4: Filtrado de fondos por riesgo**

   - **Entrada:** Filtro "Solo bajo riesgo"
   - **Resultado esperado:** Solo fondos conservadores mostrados

5. **CP-003.5: Recomendaciones personalizadas**

   - **Entrada:** Usuario con perfil conservador
   - **Resultado esperado:** Fondos de bajo riesgo destacados primero

6. **CP-003.6: Prevención de inversión duplicada (idempotencia)**

   - **Entrada:** Doble click en botón invertir
   - **Resultado esperado:** Solo una transacción procesada

7. **CP-003.7: Inversión en fondo sin cupos**
   - **Entrada:** Intento de invertir en fondo completo
   - **Resultado esperado:** Mensaje "Fondo completo", sugerencias de alternativas

---

## Validación INVEST

- [x] **I**ndependiente: Requiere HU-001, HU-002, HU-008 pero luego es independiente
- [x] **N**egociable: Estructura de comisiones y montos mínimos ajustables
- [x] **V**aliosa: Funcionalidad core del producto, genera ingresos
- [x] **E**stimable: 13 puntos por complejidad transaccional y integraciones
- [x] **S**mall (Pequeña): Completable en un sprint con equipo completo
- [x] **T**esteable: Criterios claros, casos de prueba bien definidos

---

## Historial de Cambios

| Fecha      | Versión | Autor              | Descripción                         |
| ---------- | ------- | ------------------ | ----------------------------------- |
| 22/10/2025 | 1.0     | Equipo de Análisis | Creación inicial basada en RF-002.1 |
