# 📋 HISTORIA DE USUARIO - Integración con Pasarelas de Pago

## Información General

**ID:** HU-008  
**Título:** Procesar pagos seguros con múltiples métodos colombianos  
**Épica/Módulo:** RF-005: Integraciones y Procesamiento de Pagos  
**Prioridad:** MUST (Crítico)  
**Puntos de Historia:** 13  
**Sprint/Iteración:** Sprint 1-2

---

## Historia de Usuario

**Como** usuario que desea invertir  
**Quiero** poder pagar de forma segura usando diferentes métodos de pago colombianos  
**Para** agregar fondos a mi cuenta y realizar inversiones sin fricciones ni preocupaciones de seguridad

---

## Descripción Detallada

Esta historia implementa la infraestructura crítica de procesamiento de pagos. Debe soportar los métodos de pago más populares en Colombia:

- **PSE (Pagos Seguros en Línea):** Transferencias bancarias directas
- **Tarjetas de crédito/débito:** Visa, Mastercard, American Express
- **Billeteras digitales:** Nequi, Daviplata, Movii
- **Corresponsales bancarios:** Efecty, Baloto (opcional)

La integración debe ser PCI-DSS compliant, con encriptación SSL/TLS, manejo robusto de errores, retry automático en fallos temporales, y reconciliación automática de transacciones. La experiencia debe ser fluida con redirección transparente a pasarelas y retorno automático a la plataforma.

---

## Criterios de Aceptación

### Escenario 1: Pago exitoso con PSE

```gherkin
Dado que quiero agregar $100,000 a mi cuenta
Cuando selecciono "PSE" como método de pago
Y elijo mi banco de la lista
Y soy redirigido a la plataforma de mi banco
Y completo la autenticación y confirmo el pago
Entonces el sistema recibe la confirmación del pago
Y actualiza mi saldo en menos de 1 minuto
Y recibo confirmación por email con comprobante
Y la transacción queda registrada en mi historial
```

### Escenario 2: Pago con tarjeta de crédito

```gherkin
Dado que quiero pagar con tarjeta de crédito
Cuando ingreso los datos de mi tarjeta en el formulario seguro
Y el sistema valida el formato de los datos
Y proceso el pago
Entonces la pasarela valida la tarjeta con el banco emisor
Y si es aprobada, el pago se confirma inmediatamente
Y mi saldo se actualiza en tiempo real
Y recibo notificación de pago exitoso
```

### Escenario 3: Pago con Nequi

```gherkin
Dado que quiero usar mi cuenta Nequi
Cuando selecciono "Nequi" como método de pago
Y ingreso mi número de celular registrado
Entonces recibo una notificación push en mi app Nequi
Y confirmo el pago con mi PIN de Nequi
Y el sistema recibe confirmación instantánea
Y mi saldo se actualiza inmediatamente
```

### Escenario 4: Manejo de pago rechazado

```gherkin
Dado que intento pagar con una tarjeta sin fondos
Cuando la pasarela intenta procesar el pago
Entonces recibo un mensaje claro: "Pago rechazado por fondos insuficientes"
Y se me sugiere: "Intenta con otro método de pago o verifica tu saldo"
Y no se cobra ninguna comisión
Y puedo reintentar con otro método inmediatamente
```

### Escenario 5: Timeout de pasarela de pago

```gherkin
Dado que estoy procesando un pago
Cuando la pasarela no responde en 30 segundos
Entonces el sistema muestra: "La transacción está tomando más tiempo de lo esperado"
Y reintentar automáticamente hasta 3 veces
Y si persiste el problema, mostrar: "Error temporal. Intenta nuevamente en unos minutos"
Y no duplicar el cargo al usuario
```

### Escenario 6: Reconciliación de pago pendiente

```gherkin
Dado que un pago quedó en estado pendiente (PSE en validación)
Cuando el sistema ejecuta la reconciliación automática cada hora
Y la pasarela confirma que el pago fue exitoso
Entonces el sistema actualiza el estado a "Completado"
Y actualiza el saldo del usuario
Y envía notificación de confirmación tardía
```

### Escenario 7: Seguridad - no almacenar datos sensibles

```gherkin
Dado que un usuario paga con tarjeta de crédito
Cuando el pago se procesa exitosamente
Entonces el sistema NO almacena el número completo de la tarjeta
Y solo guarda los últimos 4 dígitos para referencia
Y los datos sensibles solo pasan por la pasarela certificada PCI-DSS
Y cumple con regulaciones de protección de datos
```

### Escenario 8: Comprobante de pago descargable

```gherkin
Dado que he completado un pago exitoso
Cuando accedo a mi historial de transacciones
Y selecciono una transacción específica
Entonces puedo descargar el comprobante en PDF
Y el comprobante incluye: fecha, monto, método, ID transacción, estado
Y puedo compartirlo o guardarlo para mis registros
```

---

## Reglas de Negocio

- **RN-008.1:** Métodos de pago soportados: PSE, tarjetas, Nequi, Daviplata
- **RN-008.2:** Monto mínimo de recarga: $1,000 COP
- **RN-008.3:** Monto máximo por transacción: $50,000,000 COP (regulatorio)
- **RN-008.4:** Comisiones transparentes mostradas antes de confirmar
- **RN-008.5:** Timeout de procesamiento: 30 segundos, con retry automático
- **RN-008.6:** Reconciliación automática cada hora para pagos pendientes
- **RN-008.7:** Cumplimiento PCI-DSS nivel 1 para datos de tarjetas
- **RN-008.8:** Transacciones con idempotency key para evitar duplicados
- **RN-008.9:** Logs de auditoría completos de todas las transacciones

---

## Definición de Terminado (DoD)

- [x] Código desarrollado y cumple con estándares
- [x] Pruebas unitarias implementadas (cobertura mínima 80%)
- [x] Pruebas de integración con pasarelas en sandbox
- [x] Pruebas de manejo de errores y reintentos
- [x] Certificación PCI-DSS validada (o uso de solución certificada)
- [x] Revisión de código (code review) completada
- [x] Documentación técnica actualizada
- [x] Pruebas de aceptación pasadas por PO
- [x] Pruebas en producción con montos reales pequeños
- [x] Proceso de reconciliación validado
- [x] Sin defectos críticos o bloqueantes abiertos

---

## Notas Técnicas

**Stack/Tecnología:**

- Pasarelas de pago: Wompi, PayU Colombia, MercadoPago
- Backend: API REST con webhooks para callbacks
- Encriptación: SSL/TLS, tokenización de datos sensibles
- Base de datos: Tabla de transacciones con estados
- Queue system: Para procesamiento asíncrono de confirmaciones

**Dependencias:**

- Cuentas activas con proveedores de pasarelas
- Certificados SSL válidos
- Cuenta bancaria empresarial para recibir fondos
- Validación de identidad empresarial ante pasarelas

**Consideraciones de Seguridad:**

- **PCI-DSS Compliance:** Usar iframes o tokenización
- No almacenar CVV en ningún formato
- Encriptar datos sensibles en tránsito y reposo
- Implementar rate limiting para prevenir fraude
- Logs de auditoría con información sensible ofuscada
- Validación de integridad de callbacks (HMAC signatures)
- Implementar 3D Secure para tarjetas internacionales

**Consideraciones de Performance:**

- Procesamiento asíncrono de webhooks
- Queue para manejar picos de transacciones
- Timeout configurables por método de pago
- Caché de configuración de pasarelas
- Monitoreo de SLA de pasarelas (uptime, latencia)

---

## Mockups/Wireframes

- Mockup: `/diseño/seleccion-metodo-pago.png`
- Mockup: `/diseño/formulario-tarjeta.png`
- Mockup: `/diseño/pago-pse.png`
- Mockup: `/diseño/confirmacion-pago.png`
- Mockup: `/diseño/error-pago.png`

---

## Tareas Técnicas (Subtareas)

- [ ] Investigar y seleccionar proveedor(es) de pasarela
- [ ] Crear cuentas de prueba (sandbox) con pasarelas
- [ ] Diseñar modelo de datos para transacciones
- [ ] Crear endpoint POST /api/v1/payments/initiate
- [ ] Implementar integración con PSE
- [ ] Implementar integración con procesador de tarjetas
- [ ] Implementar integración con Nequi API
- [ ] Implementar integración con Daviplata
- [ ] Crear endpoint webhook POST /api/v1/payments/callback
- [ ] Implementar validación de firmas de webhooks
- [ ] Implementar sistema de reintentos automáticos
- [ ] Crear job de reconciliación horaria
- [ ] Implementar UI de selección de método de pago
- [ ] Implementar formulario de tarjeta con validación
- [ ] Crear flujo de redirección a PSE
- [ ] Implementar actualización de saldo en tiempo real
- [ ] Crear generación de comprobantes PDF
- [ ] Implementar sistema de idempotencia
- [ ] Configurar alertas para transacciones fallidas
- [ ] Crear dashboard de monitoreo de transacciones
- [ ] Realizar pruebas de carga y stress testing
- [ ] Documentar APIs y flujos de integración
- [ ] Validar cumplimiento PCI-DSS

---

## Casos de Prueba Principales

1. **CP-008.1: Pago exitoso con PSE**

   - **Entrada:** Usuario selecciona banco, completa autenticación
   - **Resultado esperado:** Pago confirmado, saldo actualizado

2. **CP-008.2: Pago exitoso con tarjeta válida**

   - **Entrada:** Tarjeta con fondos suficientes
   - **Resultado esperado:** Cargo exitoso, saldo actualizado inmediatamente

3. **CP-008.3: Rechazo por tarjeta sin fondos**

   - **Entrada:** Tarjeta sin saldo suficiente
   - **Resultado esperado:** Mensaje claro de rechazo, sin cargo

4. **CP-008.4: Timeout y retry automático**

   - **Entrada:** Simulación de timeout de pasarela
   - **Resultado esperado:** 3 reintentos automáticos, mensaje al usuario

5. **CP-008.5: Prevención de duplicados (idempotencia)**

   - **Entrada:** Dos requests idénticos con mismo idempotency key
   - **Resultado esperado:** Solo un cargo procesado

6. **CP-008.6: Reconciliación de pago pendiente**

   - **Entrada:** Pago PSE en validación, confirmado por banco después
   - **Resultado esperado:** Job de reconciliación actualiza estado correctamente

7. **CP-008.7: Validación de integridad de webhook**

   - **Entrada:** Webhook con firma HMAC inválida
   - **Resultado esperado:** Webhook rechazado, transacción no actualizada

8. **CP-008.8: Pago con Nequi exitoso**

   - **Entrada:** Usuario confirma pago en app Nequi
   - **Resultado esperado:** Confirmación instantánea, saldo actualizado

9. **CP-008.9: Monto por debajo del mínimo**

   - **Entrada:** Intento de pagar $500 (mínimo $1,000)
   - **Resultado esperado:** Error de validación, no permite procesar

10. **CP-008.10: Comprobante PDF generado**
    - **Entrada:** Transacción exitosa
    - **Resultado esperado:** PDF descargable con todos los datos

---

## Validación INVEST

- [x] **I**ndependiente: Infraestructura base, otras HUs dependen de esta
- [x] **N**egociable: Proveedores de pasarela son intercambiables
- [x] **V**aliosa: Crítica, sin pagos no hay producto
- [x] **E**stimable: 13 puntos por complejidad de integraciones múltiples
- [x] **S**mall (Pequeña): Puede dividirse pero se completa en 1-2 sprints
- [x] **T**esteable: Escenarios claros, transacciones verificables

---

## Riesgos y Mitigaciones

| Riesgo                            | Probabilidad | Impacto | Mitigación                                             |
| --------------------------------- | ------------ | ------- | ------------------------------------------------------ |
| Pasarela caída en producción      | Media        | Alto    | Tener 2+ proveedores, failover automático              |
| Cambios en API de pasarelas       | Baja         | Medio   | Abstracción con patrón adapter, monitorear changelogs  |
| Fraude / transacciones maliciosas | Media        | Alto    | Rate limiting, scoring de riesgo, validación 3D Secure |
| Reconciliación incorrecta         | Baja         | Alto    | Doble verificación, alertas de discrepancias           |

---

## Historial de Cambios

| Fecha      | Versión | Autor              | Descripción                         |
| ---------- | ------- | ------------------ | ----------------------------------- |
| 22/10/2025 | 1.0     | Equipo de Análisis | Creación inicial basada en RF-005.1 |
