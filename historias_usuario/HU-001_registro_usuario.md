# 📋 HISTORIA DE USUARIO - Registro de Usuario

## Información General

**ID:** HU-001  
**Título:** Registro rápido de usuario con verificación de identidad  
**Épica/Módulo:** RF-001: Gestión de Usuarios y Onboarding  
**Prioridad:** MUST (Crítico)  
**Puntos de Historia:** 8  
**Sprint/Iteración:** Sprint 1

---

## Historia de Usuario

**Como** usuario nuevo interesado en finanzas sostenibles  
**Quiero** registrarme en la plataforma de forma rápida y segura  
**Para** poder acceder a productos financieros verdes y empezar a invertir con impacto ambiental positivo

---

## Descripción Detallada

Esta historia cubre el proceso completo de registro de nuevos usuarios en la plataforma fintech verde. El proceso debe ser ágil (máximo 5 minutos) pero cumplir con requisitos regulatorios colombianos (SARLAFT, validación con Registraduría). La experiencia debe ser móvil-first considerando que muchos usuarios accederán desde smartphones.

El sistema debe validar la identidad del usuario en tiempo real con la Registraduría Nacional y aplicar verificación dual (SMS + email) para garantizar la seguridad de la cuenta.

---

## Criterios de Aceptación

### Escenario 1: Registro exitoso de usuario nuevo

```gherkin
Dado que soy un usuario nuevo que accede a la página de registro
Cuando ingreso mis datos personales (nombres completos, cédula, correo, teléfono)
Y todos los datos tienen el formato correcto
Y la cédula es válida según Registraduría
Entonces el sistema envía un código de verificación a mi teléfono y correo
Y puedo ingresar el código para confirmar mi identidad
Y el sistema crea mi cuenta en menos de 5 minutos
Y soy redirigido al formulario de perfil financiero
```

### Escenario 2: Documento de identidad inválido

```gherkin
Dado que estoy en el proceso de registro
Cuando ingreso un número de cédula que no existe en la Registraduría
Entonces el sistema muestra un mensaje: "Documento no válido. Verifica el número ingresado"
Y no permite continuar con el registro
Y sugiere contactar soporte si el problema persiste
```

### Escenario 3: Usuario ya registrado intenta crear cuenta duplicada

```gherkin
Dado que ya existe una cuenta con mi documento de identidad
Cuando intento registrarme nuevamente con el mismo documento
Entonces el sistema muestra: "Ya existe una cuenta con este documento"
Y ofrece opciones de "Iniciar sesión" o "Recuperar contraseña"
Y no crea una cuenta duplicada
```

### Escenario 4: Código de verificación incorrecto

```gherkin
Dado que he solicitado el código de verificación
Cuando ingreso un código incorrecto
Entonces el sistema muestra: "Código incorrecto. Intentos restantes: X"
Y permite reintentar hasta 3 veces
Y después de 3 intentos fallidos, solicita generar un nuevo código
```

### Escenario 5: Verificación dual exitosa

```gherkin
Dado que he ingresado correctamente el código de verificación SMS
Cuando también verifico el código enviado a mi correo electrónico
Entonces el sistema confirma ambas verificaciones
Y activa completamente mi cuenta
Y registra la verificación dual en el log de auditoría
```

---

## Reglas de Negocio

- **RN-001.1:** El documento de identidad debe ser cédula de ciudadanía colombiana válida
- **RN-001.2:** La validación con Registraduría debe completarse en tiempo real (timeout máximo 10 segundos)
- **RN-001.3:** El correo electrónico y número de teléfono deben ser únicos en el sistema
- **RN-001.4:** Los códigos de verificación expiran después de 10 minutos
- **RN-001.5:** El proceso completo de registro no debe exceder 5 minutos
- **RN-001.6:** Cumplimiento con SARLAFT: almacenar registro de validación de identidad
- **RN-001.7:** La contraseña debe tener mínimo 8 caracteres, incluir mayúsculas, minúsculas, números y caracteres especiales

---

## Definición de Terminado (DoD)

- [x] Código desarrollado y cumple con estándares
- [x] Pruebas unitarias implementadas (cobertura mínima 80%)
- [x] Pruebas de integración con Registraduría y servicios SMS/email
- [x] Revisión de código (code review) completada
- [x] Documentación técnica actualizada
- [x] Pruebas de aceptación pasadas por PO
- [x] Despliegue en ambiente de pruebas
- [x] Sin defectos críticos o bloqueantes abiertos
- [x] Cumplimiento validado con requisitos SARLAFT

---

## Notas Técnicas

**Stack/Tecnología:**

- Backend: API REST (Node.js/Python)
- Validación de identidad: API Registraduría Nacional
- SMS: Twilio o proveedor local colombiano
- Email: SendGrid o Amazon SES
- Encriptación: bcrypt para contraseñas, SSL/TLS para transmisión

**Dependencias:**

- API de Registraduría Nacional del Estado Civil
- Servicio de envío de SMS (Twilio/InfoBip)
- Servicio de email transaccional
- Base de datos para almacenar usuarios

**Consideraciones de Seguridad:**

- Implementar rate limiting para prevenir ataques de fuerza bruta
- Encriptar datos sensibles en reposo y en tránsito
- Implementar CAPTCHA para prevenir registros automatizados
- Logs de auditoría para cumplimiento SARLAFT
- Validar y sanitizar todas las entradas del usuario

**Consideraciones de Performance:**

- Timeout de 10 segundos para validación con Registraduría
- Caché de resultados de validación (con TTL apropiado)
- Async processing para envío de códigos de verificación
- CDN para assets estáticos del formulario

---

## Mockups/Wireframes

- Mockup: `/diseño/registro-paso-1-datos-personales.png`
- Mockup: `/diseño/registro-paso-2-verificacion.png`
- Mockup: `/diseño/registro-paso-3-confirmacion.png`

---

## Tareas Técnicas (Subtareas)

- [ ] Diseñar y crear tabla de usuarios en base de datos
- [ ] Implementar endpoint POST /api/v1/auth/register
- [ ] Integrar API de Registraduría Nacional
- [ ] Implementar servicio de envío de SMS con códigos de verificación
- [ ] Implementar servicio de envío de emails transaccionales
- [ ] Crear formulario de registro frontend (responsive)
- [ ] Implementar validación de formulario en cliente y servidor
- [ ] Implementar generación y validación de códigos de verificación
- [ ] Configurar rate limiting y seguridad
- [ ] Crear logs de auditoría para SARLAFT
- [ ] Implementar manejo de errores y mensajes al usuario
- [ ] Crear pruebas unitarias y de integración
- [ ] Documentar API endpoints

---

## Casos de Prueba Principales

1. **CP-001.1: Registro completo exitoso**

   - **Entrada:** Datos válidos de usuario, documento válido
   - **Resultado esperado:** Cuenta creada, códigos enviados, verificación exitosa

2. **CP-001.2: Validación de formato de documento**

   - **Entrada:** Cédula con formato incorrecto (letras, menos de 6 dígitos)
   - **Resultado esperado:** Error de validación, mensaje descriptivo

3. **CP-001.3: Documento no encontrado en Registraduría**

   - **Entrada:** Número de documento inexistente
   - **Resultado esperado:** Error, sugerencia de verificar número

4. **CP-001.4: Email duplicado**

   - **Entrada:** Email ya registrado en sistema
   - **Resultado esperado:** Error, sugerencia de recuperar contraseña

5. **CP-001.5: Timeout de validación con Registraduría**

   - **Entrada:** Simulación de timeout de API externa
   - **Resultado esperado:** Mensaje de error amigable, opción de reintentar

6. **CP-001.6: Código de verificación expirado**
   - **Entrada:** Código después de 10 minutos de generado
   - **Resultado esperado:** Rechazo del código, opción de solicitar nuevo

---

## Validación INVEST

- [x] **I**ndependiente: Puede desarrollarse sin dependencias de otras HU
- [x] **N**egociable: Flexible en la implementación técnica del proveedor SMS/email
- [x] **V**aliosa: Esencial para que usuarios accedan a la plataforma
- [x] **E**stimable: 8 puntos de historia basado en complejidad de integraciones
- [x] **S**mall (Pequeña): Completable en un sprint de 2 semanas
- [x] **T**esteable: Criterios de aceptación claros y verificables

---

## Historial de Cambios

| Fecha      | Versión | Autor              | Descripción                         |
| ---------- | ------- | ------------------ | ----------------------------------- |
| 22/10/2025 | 1.0     | Equipo de Análisis | Creación inicial basada en RF-001.1 |
