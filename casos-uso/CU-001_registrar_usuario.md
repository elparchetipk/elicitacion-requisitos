# CU-001: Registrar Usuario Nuevo

## Información General

- **ID:** CU-001
- **Nombre:** Registrar usuario nuevo en la plataforma
- **Módulo:** Gestión de Usuarios y Onboarding
- **Prioridad:** MUST (Crítico)
- **Complejidad:** Media
- **Estado:** Aprobado
- **Relacionado con:** RF-001.1, HU-001

---

## Descripción

Permite que una persona nueva se registre en la plataforma Fintech Verde Colombia proporcionando su información básica y validando su identidad a través de verificación dual (SMS + email) y validación con la Registraduría Nacional.

---

## Actores

- **Actor Principal:** Usuario Nuevo
- **Actores Secundarios:** 
  - Sistema Registraduría Nacional
  - Servicio de SMS (Twilio)
  - Servicio de Email (SendGrid)

---

## Precondiciones

- Usuario tiene acceso a internet
- Usuario posee documento de identidad colombiano válido (cédula de ciudadanía)
- Usuario tiene número de teléfono móvil activo
- Usuario tiene dirección de correo electrónico activa
- Sistema de validación con Registraduría está operativo

---

## Postcondiciones

### Éxito
- Cuenta de usuario creada en el sistema
- Usuario verificado con doble autenticación
- Usuario puede iniciar sesión
- Log de auditoría registrado con datos de creación
- Usuario redirigido a configuración de perfil de riesgo

### Fracaso
- No se crea cuenta de usuario
- Datos ingresados no se persisten
- Usuario recibe mensaje claro del motivo de falla

---

## Flujo Principal (Camino Feliz)

1. Usuario accede a la página de registro de la plataforma
2. Sistema muestra formulario de registro con campos:
   - Nombres completos
   - Número de cédula
   - Correo electrónico
   - Número de teléfono móvil
   - Contraseña
   - Confirmación de contraseña
   - Aceptación de términos y condiciones
   - Aceptación de política de privacidad
3. Usuario completa todos los campos del formulario
4. Usuario hace clic en "Crear cuenta"
5. Sistema valida formato de datos ingresados:
   - Email con formato válido
   - Teléfono con 10 dígitos
   - Contraseña cumple requisitos de seguridad
   - Cédula con formato numérico válido
6. Sistema verifica que email y teléfono no estén ya registrados
7. Sistema consulta Registraduría Nacional para validar cédula
8. Registraduría confirma que cédula es válida y pertenece al nombre ingresado
9. Sistema genera código de verificación de 6 dígitos
10. Sistema envía código por SMS al teléfono registrado
11. Sistema envía código por email al correo registrado
12. Sistema muestra pantalla de verificación con campos para ambos códigos
13. Usuario ingresa código recibido por SMS
14. Usuario ingresa código recibido por email
15. Sistema valida que ambos códigos sean correctos y no hayan expirado
16. Sistema crea cuenta de usuario en base de datos
17. Sistema registra evento en log de auditoría (SARLAFT)
18. Sistema envía email de bienvenida
19. Sistema autentica automáticamente al usuario
20. Sistema redirige a página de configuración de perfil de riesgo
21. Sistema muestra mensaje: "¡Bienvenido! Completa tu perfil para comenzar a invertir"

---

## Flujos Alternativos

### FA-1: Usuario ya tiene cuenta
**En el paso 6:**
- 6a. Sistema detecta que email o cédula ya están registrados
- 6b. Sistema muestra mensaje: "Ya existe una cuenta con estos datos"
- 6c. Sistema ofrece opciones: "Iniciar sesión" o "Recuperar contraseña"
- 6d. Caso de uso termina

### FA-2: Usuario ingresa solo código de SMS
**En el paso 13-14:**
- 13a. Usuario ingresa solo código SMS pero no el de email
- 13b. Sistema muestra advertencia: "También debes verificar tu email"
- 13c. Sistema ofrece reenviar código de email
- 13d. Usuario completa verificación dual
- 13e. Flujo continúa en paso 15

### FA-3: Usuario solicita reenvío de código
**En el paso 12:**
- 12a. Usuario no recibe código o código expira
- 12b. Usuario hace clic en "Reenviar código"
- 12c. Sistema genera nuevos códigos
- 12d. Sistema envía nuevos códigos por SMS y email
- 12e. Sistema invalida códigos anteriores
- 12f. Flujo continúa en paso 13

### FA-4: Nombres no coinciden con Registraduría
**En el paso 8:**
- 8a. Registraduría indica que nombre no coincide exactamente con cédula
- 8b. Sistema sugiere nombre correcto según Registraduría
- 8c. Sistema permite al usuario corregir o contactar soporte
- 8d. Usuario corrige nombre según sugerencia
- 8e. Flujo continúa en paso 9

---

## Flujos de Excepción

### FE-1: Cédula inválida
**En el paso 7-8:**
- 7a. Sistema consulta Registraduría
- 7b. Registraduría responde que cédula no existe o es inválida
- 7c. Sistema muestra: "Documento no válido. Verifica el número ingresado"
- 7d. Sistema mantiene datos ingresados para corrección
- 7e. Usuario puede corregir cédula y reintentar
- 7f. Si después de 3 intentos falla, sugiere contactar soporte
- 7g. Caso de uso termina

### FE-2: Servicio de Registraduría no disponible
**En el paso 7:**
- 7a. Sistema intenta conectar con Registraduría
- 7b. Servicio no responde después de 10 segundos (timeout)
- 7c. Sistema reintenta 2 veces más
- 7d. Si persiste falla, sistema muestra: "Servicio temporalmente no disponible. Intenta en unos minutos"
- 7e. Sistema guarda datos temporalmente (24 horas) para retomar registro
- 7f. Sistema envía alerta a equipo técnico
- 7g. Caso de uso termina

### FE-3: Código de verificación incorrecto
**En el paso 15:**
- 15a. Usuario ingresa código incorrecto (SMS o email)
- 15b. Sistema incrementa contador de intentos fallidos
- 15c. Sistema muestra: "Código incorrecto. Intentos restantes: X"
- 15d. Si intentos < 3, usuario puede reintentar (vuelve a paso 13)
- 15e. Si intentos = 3, sistema invalida códigos
- 15f. Sistema solicita generar nuevos códigos
- 15g. Usuario debe solicitar reenvío (ver FA-3)

### FE-4: Código expirado
**En el paso 15:**
- 15a. Usuario ingresa código después de 10 minutos de generado
- 15b. Sistema detecta que código expiró
- 15c. Sistema muestra: "Código expirado. Solicita uno nuevo"
- 15d. Sistema invalida códigos expirados
- 15e. Usuario debe solicitar reenvío (ver FA-3)

### FE-5: Contraseña débil
**En el paso 5:**
- 5a. Sistema valida fortaleza de contraseña
- 5b. Contraseña no cumple requisitos mínimos
- 5c. Sistema muestra mensaje específico: "La contraseña debe tener mínimo 8 caracteres, incluir mayúsculas, minúsculas, números y caracteres especiales"
- 5d. Sistema resalta campo de contraseña
- 5e. Usuario corrige contraseña
- 5f. Flujo continúa en paso 4

### FE-6: Error al enviar SMS o Email
**En el paso 10 u 11:**
- 10a. Sistema intenta enviar SMS/email
- 10b. Servicio de mensajería responde con error
- 10c. Sistema reintenta 3 veces
- 10d. Si persiste, sistema muestra: "Error al enviar código. Verifica tu número/email"
- 10e. Sistema permite corregir teléfono o email
- 10f. Usuario corrige dato
- 10g. Sistema reintenta envío
- 10h. Si falla definitivamente, sistema sugiere usar solo un canal
- 10i. Sistema registra incidencia para revisión

---

## Reglas de Negocio

- **RN-001.1:** Solo cédulas de ciudadanía colombiana son válidas para registro
- **RN-001.2:** Validación con Registraduría debe completarse en tiempo real (timeout 10 segundos)
- **RN-001.3:** Email y número de teléfono deben ser únicos en el sistema
- **RN-001.4:** Códigos de verificación expiran después de 10 minutos de generados
- **RN-001.5:** El proceso completo no debe exceder 5 minutos (restricción REST-REN-001)
- **RN-001.6:** Cumplimiento SARLAFT: registrar validación de identidad con timestamp
- **RN-001.7:** Contraseña debe cumplir:
  - Mínimo 8 caracteres
  - Al menos 1 mayúscula
  - Al menos 1 minúscula
  - Al menos 1 número
  - Al menos 1 carácter especial (@#$%^&+=!)
- **RN-001.8:** Máximo 3 intentos de verificación con el mismo código
- **RN-001.9:** Usuario menor de 18 años no puede registrarse
- **RN-001.10:** Términos y condiciones deben aceptarse explícitamente

---

## Requisitos No Funcionales

- **RNF-002.1:** Contraseñas almacenadas con hash SHA-256 y salt único
- **RNF-002.1:** Datos personales encriptados en reposo (AES-256)
- **RNF-002.2:** Comunicación con Registraduría sobre TLS 1.3
- **RNF-002.3:** Log de auditoría inmutable con firma digital
- **RNF-001.1:** Tiempo de respuesta total < 3 segundos (excluyendo validaciones externas)
- **REST-REN-001:** Proceso completo máximo 5 minutos

---

## Interfaces de Usuario

### Pantallas Involucradas

1. **Página de Registro:** Formulario con campos requeridos
2. **Modal de Términos y Condiciones:** Texto legal completo
3. **Página de Verificación:** Campos para códigos SMS y email
4. **Mensajes de Error/Éxito:** Toasts o modales informativos

### Elementos de UI

- Indicador de fortaleza de contraseña en tiempo real
- Botones "Mostrar/Ocultar contraseña"
- Validación inline de formato de campos
- Loading spinner durante validación con Registraduría
- Contador de tiempo para expiración de código
- Botón "Reenviar código" con cooldown de 60 segundos

---

## Criterios de Aceptación

✅ Usuario puede registrarse con datos válidos en menos de 5 minutos  
✅ Sistema valida cédula con Registraduría en tiempo real  
✅ Verificación dual (SMS + email) funciona correctamente  
✅ Sistema rechaza cédulas, emails o teléfonos duplicados  
✅ Códigos expiran después de 10 minutos  
✅ Máximo 3 intentos de verificación por código  
✅ Contraseñas cumplen requisitos de seguridad  
✅ Usuarios menores de 18 años no pueden registrarse  
✅ Log de auditoría registra evento de creación de cuenta  
✅ Manejo robusto de errores de servicios externos  

---

## Dependencias

### Servicios Externos
- **Registraduría Nacional:** Validación de identidad
- **Twilio:** Envío de SMS
- **SendGrid:** Envío de emails

### Módulos Internos
- Módulo de Autenticación
- Módulo de Gestión de Usuarios
- Módulo de Auditoría
- Módulo de Notificaciones

---

## Riesgos y Mitigaciones

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Registraduría no disponible | Media | Alto | Retry automático + guardado temporal + alertas |
| Códigos SMS no llegan | Media | Alto | Email como backup + reenvío + soporte |
| Ataques de registro masivo | Alta | Alto | CAPTCHA + rate limiting + verificación dual |
| Datos personales comprometidos | Baja | Crítico | Encriptación AES-256 + TLS + auditoría |

---

## Referencias

- **Requisito Funcional:** RF-001.1
- **Historia de Usuario:** HU-001
- **Entrevista:** CEO María José - "en máximo cinco minutos una persona pueda crear su cuenta"
- **Restricción:** REST-REN-001 (Tiempo onboarding máximo 5 minutos)
- **Regulación:** SARLAFT - Identificación y conocimiento del cliente

---

## Notas de Implementación

- Usar librería `bcrypt` para hashing de contraseñas
- Implementar rate limiting: máximo 5 intentos de registro por IP/hora
- Cachear resultados de Registraduría por 1 hora para evitar consultas duplicadas
- Implementar CAPTCHA invisible (Google reCAPTCHA v3)
- Monitorear tiempos de respuesta de Registraduría y alertar si > 5 segundos

---

**Estado:** Aprobado para implementación  
**Última revisión:** 12 de noviembre de 2025
