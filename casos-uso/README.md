# 📘 CASOS DE USO - FINTECH VERDE COLOMBIA

## 📌 INFORMACIÓN DEL DOCUMENTO

**Proyecto:** Fintech Verde Colombia - Plataforma de Inversiones Sostenibles  
**Versión:** 1.0  
**Fecha:** 12 de noviembre de 2025  
**Estado:** Aprobado

---

## 🎯 PROPÓSITO

Este documento consolida todos los casos de uso identificados para el proyecto Fintech Verde Colombia, derivados del análisis de requisitos funcionales, entrevistas con stakeholders y historias de usuario. Los casos de uso describen las interacciones entre actores (usuarios, sistemas externos, administradores) y el sistema para lograr objetivos específicos.

---

## 📂 ESTRUCTURA DE LA DOCUMENTACIÓN

La documentación de casos de uso está organizada por módulos funcionales:

1. **CU-001 a CU-006:** Gestión de Usuarios y Onboarding
2. **CU-007 a CU-012:** Productos Financieros Verdes
3. **CU-013 a CU-016:** Dashboard y Experiencia de Usuario
4. **CU-017 a CU-020:** Funcionalidades Sociales y Comunidad
5. **CU-021 a CU-026:** Pagos y Transacciones Financieras
6. **CU-027 a CU-030:** Reportería y Cumplimiento
7. **CU-031 a CU-035:** Administración y Gestión
8. **CU-036 a CU-040:** Integraciones Externas

---

## 👥 ACTORES DEL SISTEMA

### Actores Principales

| Actor | Descripción | Casos de Uso |
|-------|-------------|--------------|
| **Usuario Nuevo** | Persona interesada en registrarse en la plataforma | CU-001, CU-002, CU-003 |
| **Usuario Inversionista** | Usuario registrado que realiza inversiones | CU-007, CU-008, CU-009, CU-013, CU-014 |
| **Usuario Solicitante** | Usuario que solicita microcréditos verdes | CU-010, CU-011 |
| **Administrador** | Personal interno que gestiona la plataforma | CU-031, CU-032, CU-033 |
| **Auditor** | Personal que revisa cumplimiento y auditoría | CU-027, CU-028, CU-029 |

### Actores Secundarios (Sistemas Externos)

| Actor Externo | Descripción | Casos de Uso |
|---------------|-------------|--------------|
| **Sistema Registraduría** | Valida identidad de ciudadanos colombianos | CU-001, CU-036 |
| **Pasarelas de Pago** | PSE, PayU, Mercado Pago, Nequi, Daviplata | CU-021, CU-022, CU-037 |
| **Central de Riesgo** | DataCrédito, TransUnion para scoring crediticio | CU-010, CU-038 |
| **Proveedores Datos Ambientales** | APIs de sensores IoT e imágenes satelitales | CU-014, CU-039 |
| **Sistema de Custodia** | Depositarios de valores regulados | CU-012, CU-040 |
| **Superintendencia Financiera** | Entidad reguladora que recibe reportes | CU-027, CU-028 |

---

## 📊 RESUMEN DE CASOS DE USO

**Total de Casos de Uso Identificados:** 40

### Por Prioridad

- **MUST (Críticos):** 25 casos de uso
- **SHOULD (Importantes):** 10 casos de uso
- **COULD (Deseables):** 5 casos de uso

### Por Complejidad

- **Alta:** 12 casos de uso
- **Media:** 18 casos de uso
- **Baja:** 10 casos de uso

---

## 🔗 DOCUMENTOS RELACIONADOS

- **Requisitos Funcionales:** `4a. functional_requirements.md`
- **Requisitos No Funcionales:** `4b. non_functional_requirements.md`
- **Restricciones del Proyecto:** `6. restricciones_proyecto.md`
- **Historias de Usuario:** Carpeta `historias_usuario/`
- **Entrevistas:** `1. entrevista-1.md`, `2. entrevista-2.md`

---

## 📖 ÍNDICE DE CASOS DE USO

### 🔐 Módulo 1: Gestión de Usuarios y Onboarding

- [CU-001: Registrar Usuario Nuevo](./CU-001_registrar_usuario.md)
- [CU-002: Validar Identidad con Registraduría](./CU-002_validar_identidad.md)
- [CU-003: Configurar Perfil de Riesgo e Intereses](./CU-003_perfil_riesgo_intereses.md)
- [CU-004: Iniciar Sesión](./CU-004_iniciar_sesion.md)
- [CU-005: Recuperar Contraseña](./CU-005_recuperar_contrasena.md)
- [CU-006: Actualizar Información Personal](./CU-006_actualizar_informacion.md)

### 💰 Módulo 2: Productos Financieros Verdes

- [CU-007: Explorar Fondos de Inversión Verde](./CU-007_explorar_fondos.md)
- [CU-008: Invertir en Fondo Verde](./CU-008_invertir_fondo.md)
- [CU-009: Participar en Crowdfunding de Proyecto](./CU-009_crowdfunding_proyecto.md)
- [CU-010: Solicitar Microcrédito Verde](./CU-010_solicitar_microcredito.md)
- [CU-011: Simular Microcrédito](./CU-011_simular_microcredito.md)
- [CU-012: Liquidar Inversión](./CU-012_liquidar_inversion.md)

### 📊 Módulo 3: Dashboard y Experiencia de Usuario

- [CU-013: Visualizar Dashboard Principal](./CU-013_visualizar_dashboard.md)
- [CU-014: Consultar Impacto Ambiental Personal](./CU-014_impacto_ambiental.md)
- [CU-015: Descargar Certificado de Impacto](./CU-015_certificado_impacto.md)
- [CU-016: Ver Historial de Transacciones](./CU-016_historial_transacciones.md)

### 👥 Módulo 4: Funcionalidades Sociales y Comunidad

- [CU-017: Comentar en Proyecto](./CU-017_comentar_proyecto.md)
- [CU-018: Acceder a Contenido Educativo](./CU-018_contenido_educativo.md)
- [CU-019: Participar en Webinar](./CU-019_participar_webinar.md)
- [CU-020: Compartir Impacto en Redes Sociales](./CU-020_compartir_redes.md)

### 💳 Módulo 5: Pagos y Transacciones Financieras

- [CU-021: Agregar Fondos a la Cuenta](./CU-021_agregar_fondos.md)
- [CU-022: Procesar Pago con PSE](./CU-022_pago_pse.md)
- [CU-023: Procesar Pago con Tarjeta](./CU-023_pago_tarjeta.md)
- [CU-024: Procesar Pago con Billetera Digital](./CU-024_pago_billetera.md)
- [CU-025: Retirar Fondos](./CU-025_retirar_fondos.md)
- [CU-026: Consultar Saldo Disponible](./CU-026_consultar_saldo.md)

### 📑 Módulo 6: Reportería y Cumplimiento

- [CU-027: Generar Reporte Regulatorio Automático](./CU-027_reporte_regulatorio.md)
- [CU-028: Generar Certificado Tributario Anual](./CU-028_certificado_tributario.md)
- [CU-029: Auditar Transacciones](./CU-029_auditar_transacciones.md)
- [CU-030: Exportar Historial de Inversiones](./CU-030_exportar_historial.md)

### ⚙️ Módulo 7: Administración y Gestión

- [CU-031: Gestionar Proyectos Verdes](./CU-031_gestionar_proyectos.md)
- [CU-032: Aprobar/Rechazar Solicitud de Crédito](./CU-032_aprobar_credito.md)
- [CU-033: Configurar Parámetros del Sistema](./CU-033_configurar_sistema.md)
- [CU-034: Monitorear Rendimiento del Sistema](./CU-034_monitorear_sistema.md)
- [CU-035: Gestionar Usuarios y Permisos](./CU-035_gestionar_usuarios.md)

### 🔌 Módulo 8: Integraciones Externas

- [CU-036: Validar Identidad con Registraduría](./CU-036_integracion_registraduria.md)
- [CU-037: Integrar con Pasarela de Pago](./CU-037_integracion_pasarela.md)
- [CU-038: Consultar Central de Riesgo](./CU-038_consultar_central_riesgo.md)
- [CU-039: Sincronizar Datos Ambientales](./CU-039_sincronizar_datos_ambientales.md)
- [CU-040: Integrar con Sistema de Custodia](./CU-040_integracion_custodia.md)

---

## ✅ PLANTILLA DE CASO DE USO

Cada caso de uso sigue la siguiente estructura estándar:

```markdown
# CU-XXX: Nombre del Caso de Uso

## Información General
- **ID:** CU-XXX
- **Nombre:** Descripción breve
- **Módulo:** Categoría funcional
- **Prioridad:** MUST / SHOULD / COULD
- **Complejidad:** Alta / Media / Baja
- **Estado:** Aprobado / En Revisión / Implementado

## Actores
- **Actor Principal:** Quién inicia el caso de uso
- **Actores Secundarios:** Otros participantes

## Precondiciones
- Condiciones que deben cumplirse antes de ejecutar el caso de uso

## Postcondiciones
- Estado del sistema después de ejecutar el caso de uso exitosamente

## Flujo Principal (Camino Feliz)
1. Paso a paso de la interacción exitosa

## Flujos Alternativos
- Variaciones del flujo principal

## Flujos de Excepción
- Manejo de errores y situaciones anómalas

## Reglas de Negocio
- RN-XXX: Reglas aplicables

## Requisitos No Funcionales
- RNF-XXX: Requisitos aplicables

## Interfaces de Usuario
- Pantallas o vistas involucradas

## Referencias
- Documentos relacionados
```

---

## 🔄 CONTROL DE VERSIONES

| Versión | Fecha | Autor | Descripción |
|---------|-------|-------|-------------|
| 1.0 | 12-Nov-2025 | Equipo de Análisis | Versión inicial - Índice completo |

---

**Documento generado para:** Fintech Verde Colombia  
**Clasificación:** Interno - Confidencial
