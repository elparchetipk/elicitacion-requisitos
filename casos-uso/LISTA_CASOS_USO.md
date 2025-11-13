# 📊 LISTA CONSOLIDADA DE CASOS DE USO

## Fintech Verde Colombia - 40 Casos de Uso Identificados

---

## 🔐 MÓDULO 1: GESTIÓN DE USUARIOS Y ONBOARDING (6 casos)

### CU-001: Registrar Usuario Nuevo ⭐ CRÍTICO
**Descripción:** Usuario nuevo se registra proporcionando datos básicos y verificando identidad  
**Actores:** Usuario Nuevo, Sistema Registraduría, Servicios SMS/Email  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-001.1, HU-001

### CU-002: Validar Identidad con Registraduría ⭐ CRÍTICO
**Descripción:** Sistema valida documento de identidad contra Registraduría Nacional  
**Actores:** Sistema, API Registraduría  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-001.1, REST-REG-001

### CU-003: Configurar Perfil de Riesgo e Intereses ⭐ CRÍTICO
**Descripción:** Usuario completa cuestionario de perfil financiero y motivaciones ambientales  
**Actores:** Usuario Registrado  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-001.2, HU-002

### CU-004: Iniciar Sesión ⭐ CRÍTICO
**Descripción:** Usuario accede a plataforma con credenciales  
**Actores:** Usuario Registrado  
**Prioridad:** MUST | **Complejidad:** Baja  
**Fuente:** RF-001 (implícito)

### CU-005: Recuperar Contraseña
**Descripción:** Usuario restablece contraseña olvidada mediante email  
**Actores:** Usuario, Servicio Email  
**Prioridad:** SHOULD | **Complejidad:** Baja  
**Fuente:** RF-001 (implícito)

### CU-006: Actualizar Información Personal
**Descripción:** Usuario modifica datos personales, perfil de riesgo o preferencias  
**Actores:** Usuario Autenticado  
**Prioridad:** SHOULD | **Complejidad:** Baja  
**Fuente:** RF-001 (implícito)

---

## 💰 MÓDULO 2: PRODUCTOS FINANCIEROS VERDES (6 casos)

### CU-007: Explorar Fondos de Inversión Verde ⭐ CRÍTICO
**Descripción:** Usuario explora catálogo de fondos verdes con filtros y búsqueda  
**Actores:** Usuario Inversionista  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-002.1, HU-003

### CU-008: Invertir en Fondo Verde ⭐ CRÍTICO
**Descripción:** Usuario realiza inversión en fondo seleccionado desde $1,000 COP  
**Actores:** Usuario Inversionista, Sistema Custodia, Pasarela Pago  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-002.1, HU-003

### CU-009: Participar en Crowdfunding de Proyecto ⭐ CRÍTICO
**Descripción:** Usuario invierte en proyecto específico de crowdfunding  
**Actores:** Usuario Inversionista, Gestor de Proyecto  
**Prioridad:** SHOULD | **Complejidad:** Alta  
**Fuente:** RF-002.2

### CU-010: Solicitar Microcrédito Verde
**Descripción:** Usuario solicita microcrédito para tecnología limpia  
**Actores:** Usuario Solicitante, Central de Riesgo, Analista Crédito  
**Prioridad:** COULD | **Complejidad:** Alta  
**Fuente:** RF-002.3

### CU-011: Simular Microcrédito
**Descripción:** Usuario simula condiciones de microcrédito antes de solicitar  
**Actores:** Usuario  
**Prioridad:** SHOULD | **Complejidad:** Baja  
**Fuente:** RF-002.3 (implícito)

### CU-012: Liquidar Inversión ⭐ CRÍTICO
**Descripción:** Usuario retira total o parcialmente inversión de un fondo  
**Actores:** Usuario Inversionista, Sistema Custodia  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-005.2

---

## 📊 MÓDULO 3: DASHBOARD Y EXPERIENCIA DE USUARIO (4 casos)

### CU-013: Visualizar Dashboard Principal ⭐ CRÍTICO
**Descripción:** Usuario accede a dashboard personalizado con portafolio e impacto  
**Actores:** Usuario Autenticado  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-003.1, HU-004

### CU-014: Consultar Impacto Ambiental Personal ⭐ CRÍTICO
**Descripción:** Usuario visualiza métricas de impacto ambiental de sus inversiones  
**Actores:** Usuario Inversionista, Proveedores Datos Ambientales  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-003.2, HU-005

### CU-015: Descargar Certificado de Impacto
**Descripción:** Usuario descarga certificado PDF de su impacto ambiental  
**Actores:** Usuario Inversionista  
**Prioridad:** SHOULD | **Complejidad:** Media  
**Fuente:** RF-003.2, HU-005

### CU-016: Ver Historial de Transacciones ⭐ CRÍTICO
**Descripción:** Usuario consulta historial completo de transacciones financieras  
**Actores:** Usuario Autenticado  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-006.2

---

## 👥 MÓDULO 4: FUNCIONALIDADES SOCIALES Y COMUNIDAD (4 casos)

### CU-017: Comentar en Proyecto
**Descripción:** Usuario comenta, pregunta o discute sobre un proyecto  
**Actores:** Usuario Comunidad  
**Prioridad:** SHOULD | **Complejidad:** Media  
**Fuente:** RF-004.1

### CU-018: Acceder a Contenido Educativo ⭐ CRÍTICO
**Descripción:** Usuario consume videos, artículos y webinars sobre finanzas verdes  
**Actores:** Usuario  
**Prioridad:** SHOULD | **Complejidad:** Media  
**Fuente:** RF-004.2

### CU-019: Participar en Webinar
**Descripción:** Usuario se registra y asiste a webinar en vivo  
**Actores:** Usuario, Instructor  
**Prioridad:** COULD | **Complejidad:** Media  
**Fuente:** RF-004.2

### CU-020: Compartir Impacto en Redes Sociales
**Descripción:** Usuario comparte métricas de impacto en redes sociales  
**Actores:** Usuario, Redes Sociales  
**Prioridad:** SHOULD | **Complejidad:** Baja  
**Fuente:** HU-005

---

## 💳 MÓDULO 5: PAGOS Y TRANSACCIONES FINANCIERAS (6 casos)

### CU-021: Agregar Fondos a la Cuenta ⭐ CRÍTICO
**Descripción:** Usuario agrega dinero a su saldo mediante diferentes métodos  
**Actores:** Usuario, Pasarela de Pago  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-005.1, HU-008

### CU-022: Procesar Pago con PSE ⭐ CRÍTICO
**Descripción:** Usuario paga mediante transferencia bancaria PSE  
**Actores:** Usuario, PSE, Banco Usuario  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-005.1, HU-008

### CU-023: Procesar Pago con Tarjeta ⭐ CRÍTICO
**Descripción:** Usuario paga con tarjeta débito/crédito  
**Actores:** Usuario, Pasarela Pago, Banco Emisor  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-005.1, HU-008

### CU-024: Procesar Pago con Billetera Digital ⭐ CRÍTICO
**Descripción:** Usuario paga con Nequi, Daviplata u otra billetera  
**Actores:** Usuario, Proveedor Billetera  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-005.1, HU-008

### CU-025: Retirar Fondos ⭐ CRÍTICO
**Descripción:** Usuario retira dinero disponible a su cuenta bancaria  
**Actores:** Usuario, Sistema Bancario  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-005.2

### CU-026: Consultar Saldo Disponible
**Descripción:** Usuario consulta saldo disponible e invertido en tiempo real  
**Actores:** Usuario Autenticado  
**Prioridad:** MUST | **Complejidad:** Baja  
**Fuente:** RF-003 (implícito)

---

## 📑 MÓDULO 6: REPORTERÍA Y CUMPLIMIENTO (4 casos)

### CU-027: Generar Reporte Regulatorio Automático ⭐ CRÍTICO
**Descripción:** Sistema genera reportes para Superintendencia Financiera automáticamente  
**Actores:** Sistema, Superintendencia Financiera  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-006.1, REST-REG-001

### CU-028: Generar Certificado Tributario Anual ⭐ CRÍTICO
**Descripción:** Sistema genera certificado tributario para usuarios para declaración de renta  
**Actores:** Usuario Inversionista, Sistema  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-006.1

### CU-029: Auditar Transacciones ⭐ CRÍTICO
**Descripción:** Auditor consulta logs y traza transacciones para auditoría  
**Actores:** Auditor, Sistema Auditoría  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-006.2, REST-SEG-004

### CU-030: Exportar Historial de Inversiones
**Descripción:** Usuario exporta su historial completo en Excel/PDF  
**Actores:** Usuario Inversionista  
**Prioridad:** SHOULD | **Complejidad:** Baja  
**Fuente:** RF-006 (implícito)

---

## ⚙️ MÓDULO 7: ADMINISTRACIÓN Y GESTIÓN (5 casos)

### CU-031: Gestionar Proyectos Verdes ⭐ CRÍTICO
**Descripción:** Administrador crea, edita, aprueba o suspende proyectos de inversión  
**Actores:** Administrador, Gestor de Proyecto  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-002 (implícito)

### CU-032: Aprobar/Rechazar Solicitud de Crédito ⭐ CRÍTICO
**Descripción:** Analista revisa y decide sobre solicitudes de microcrédito  
**Actores:** Analista Crédito, Central de Riesgo  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-002.3

### CU-033: Configurar Parámetros del Sistema
**Descripción:** Administrador configura tasas, comisiones, límites del sistema  
**Actores:** Administrador  
**Prioridad:** SHOULD | **Complejidad:** Media  
**Fuente:** Requisitos administrativos

### CU-034: Monitorear Rendimiento del Sistema ⭐ CRÍTICO
**Descripción:** Administrador visualiza métricas técnicas y de negocio en tiempo real  
**Actores:** Administrador, CTO  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** Entrevista CTO

### CU-035: Gestionar Usuarios y Permisos
**Descripción:** Administrador gestiona roles, permisos y accesos de usuarios  
**Actores:** Administrador  
**Prioridad:** SHOULD | **Complejidad:** Media  
**Fuente:** Requisitos administrativos

---

## 🔌 MÓDULO 8: INTEGRACIONES EXTERNAS (5 casos)

### CU-036: Validar Identidad con Registraduría ⭐ CRÍTICO
**Descripción:** Sistema integra con API de Registraduría para validación de identidad  
**Actores:** Sistema, API Registraduría  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** REST-REG-001, CU-001

### CU-037: Integrar con Pasarela de Pago ⭐ CRÍTICO
**Descripción:** Sistema procesa pagos mediante pasarelas certificadas  
**Actores:** Sistema, Pasarelas (PSE, PayU, etc.)  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-005.1, REST-INT-001

### CU-038: Consultar Central de Riesgo ⭐ CRÍTICO
**Descripción:** Sistema consulta historial crediticio para evaluación de créditos  
**Actores:** Sistema, DataCrédito/TransUnion  
**Prioridad:** MUST | **Complejidad:** Media  
**Fuente:** RF-002.3, REST-INT-002

### CU-039: Sincronizar Datos Ambientales
**Descripción:** Sistema obtiene datos de sensores IoT e imágenes satelitales  
**Actores:** Sistema, Proveedores Datos Ambientales  
**Prioridad:** SHOULD | **Complejidad:** Alta  
**Fuente:** RF-003.2, REST-INT-003

### CU-040: Integrar con Sistema de Custodia ⭐ CRÍTICO
**Descripción:** Sistema registra y consulta participaciones en depósito de valores  
**Actores:** Sistema, Depositario de Valores  
**Prioridad:** MUST | **Complejidad:** Alta  
**Fuente:** RF-002.1, REST-INT-004

---

## 📈 ESTADÍSTICAS Y MÉTRICAS

### Por Prioridad
- **MUST (Críticos):** 25 casos de uso (62.5%)
- **SHOULD (Importantes):** 10 casos de uso (25%)
- **COULD (Deseables):** 5 casos de uso (12.5%)

### Por Complejidad
- **Alta:** 16 casos de uso (40%)
- **Media:** 16 casos de uso (40%)
- **Baja:** 8 casos de uso (20%)

### Por Módulo
| Módulo | Cantidad | Críticos |
|--------|----------|----------|
| Gestión Usuarios | 6 | 4 |
| Productos Financieros | 6 | 3 |
| Dashboard y UX | 4 | 4 |
| Comunidad | 4 | 1 |
| Pagos | 6 | 5 |
| Reportería | 4 | 3 |
| Administración | 5 | 3 |
| Integraciones | 5 | 4 |
| **TOTAL** | **40** | **27** |

---

## 🎯 CASOS DE USO CRÍTICOS PARA MVP

Los siguientes casos de uso son absolutamente esenciales para el Producto Mínimo Viable:

1. **CU-001:** Registrar Usuario Nuevo
2. **CU-003:** Configurar Perfil de Riesgo
3. **CU-004:** Iniciar Sesión
4. **CU-007:** Explorar Fondos de Inversión
5. **CU-008:** Invertir en Fondo Verde
6. **CU-013:** Visualizar Dashboard Principal
7. **CU-014:** Consultar Impacto Ambiental
8. **CU-016:** Ver Historial de Transacciones
9. **CU-021:** Agregar Fondos a la Cuenta
10. **CU-022/023/024:** Procesar Pagos (al menos PSE)
11. **CU-025:** Retirar Fondos
12. **CU-027:** Generar Reportes Regulatorios
13. **CU-036:** Validar Identidad con Registraduría
14. **CU-037:** Integrar con Pasarela de Pago
15. **CU-040:** Integrar con Sistema de Custodia

**Total MVP:** 15 casos de uso críticos

---

## 📋 MATRIZ DE DEPENDENCIAS

### Dependencias Críticas

```
CU-001 (Registro) → CU-002 (Validación Registraduría) → CU-003 (Perfil)
                                                              ↓
CU-004 (Login) → CU-013 (Dashboard) → CU-007 (Explorar Fondos)
                                                              ↓
CU-021 (Agregar Fondos) → CU-022/023/024 (Procesar Pago) → CU-008 (Invertir)
                                                              ↓
CU-040 (Custodia) ← CU-008 (Invertir) → CU-014 (Impacto Ambiental)
                                                              ↓
CU-016 (Historial) ← CU-008 (Invertir) → CU-027 (Reportes)
```

---

## 🔄 PRIORIZACIÓN DE IMPLEMENTACIÓN

### Sprint 1 (Fundacional)
- CU-001, CU-002, CU-003, CU-004, CU-005, CU-006
- CU-036, CU-037

### Sprint 2 (Core de Negocio)
- CU-007, CU-008
- CU-021, CU-022, CU-023, CU-024
- CU-040

### Sprint 3 (Experiencia de Usuario)
- CU-013, CU-014, CU-016
- CU-026, CU-025
- CU-015

### Sprint 4 (Expansión de Productos)
- CU-009 (Crowdfunding)
- CU-011, CU-010 (Microcréditos)
- CU-038

### Sprint 5 (Comunidad y Educación)
- CU-017, CU-018, CU-019, CU-020

### Sprint 6 (Reportería y Cumplimiento)
- CU-027, CU-028, CU-029, CU-030

### Sprint 7 (Administración)
- CU-031, CU-032, CU-033, CU-034, CU-035
- CU-039

---

## 📚 REFERENCIAS

- **Requisitos Funcionales:** `4a. functional_requirements.md`
- **Requisitos No Funcionales:** `4b. non_functional_requirements.md`
- **Restricciones:** `6. restricciones_proyecto.md`
- **Historias de Usuario:** Carpeta `historias_usuario/`
- **Entrevistas:** `1. entrevista-1.md`, `2. entrevista-2.md`

---

## ✅ CONTROL DE VERSIONES

| Versión | Fecha | Cambios |
|---------|-------|---------|
| 1.0 | 12-Nov-2025 | Lista completa de 40 casos de uso identificados |

---

**Documento generado para:** Fintech Verde Colombia  
**Estado:** Aprobado  
**Próxima revisión:** Al finalizar Sprint 1
