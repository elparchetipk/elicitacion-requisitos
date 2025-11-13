# CU-008: Invertir en Fondo Verde

## Información General

- **ID:** CU-008
- **Nombre:** Realizar inversión en fondo de inversión verde
- **Módulo:** Productos Financieros Verdes
- **Prioridad:** MUST (Crítico)
- **Complejidad:** Alta
- **Estado:** Aprobado
- **Relacionado con:** RF-002.1, HU-003

---

## Descripción

Permite que un usuario inversionista seleccione un fondo de inversión verde y realice una inversión especificando el monto deseado (mínimo $1,000 COP). El sistema valida disponibilidad de fondos, procesa el pago, actualiza el portafolio y calcula el impacto ambiental proyectado.

---

## Actores

- **Actor Principal:** Usuario Inversionista
- **Actores Secundarios:**
  - Sistema de Pagos
  - Pasarela de Pago Externa
  - Sistema de Custodia de Valores
  - Motor de Cálculo de Impacto Ambiental
  - Sistema de Notificaciones

---

## Precondiciones

- Usuario autenticado en el sistema
- Usuario tiene perfil de riesgo configurado
- Existen fondos de inversión verde disponibles
- Usuario tiene método de pago configurado o saldo disponible
- Sistema de pagos operativo
- Sistema de custodia integrado y operativo

---

## Postcondiciones

### Éxito
- Inversión registrada en el sistema
- Saldo del usuario actualizado
- Portafolio actualizado con nueva inversión
- Participación en fondo registrada en sistema de custodia
- Transacción registrada en log de auditoría
- Impacto ambiental proyectado calculado
- Notificaciones enviadas (email + in-app)
- Certificado de inversión generado

### Fracaso
- No se registra inversión
- Saldo del usuario no cambia
- No se cobra al usuario
- Usuario recibe notificación de falla con motivo

---

## Flujo Principal (Camino Feliz)

1. Usuario accede a sección "Fondos de Inversión" desde dashboard
2. Sistema muestra catálogo de fondos verdes disponibles con:
   - Nombre del fondo
   - Rendimiento histórico (últimos 12 meses)
   - Nivel de riesgo (Bajo/Medio/Alto)
   - Impacto ambiental acumulado
   - Inversión mínima
   - Fondos recomendados para el perfil del usuario destacados
3. Usuario explora opciones y selecciona un fondo específico
4. Sistema muestra página de detalles del fondo con:
   - Descripción completa
   - Composición de proyectos (gráfico circular)
   - Historial de rendimiento (gráfico de líneas)
   - Distribución geográfica
   - Métricas de impacto detalladas
   - Estructura de comisiones
   - Comentarios de otros inversionistas
5. Usuario revisa información y hace clic en "Invertir ahora"
6. Sistema muestra modal de inversión con campos:
   - Monto a invertir (pre-llenado con $1,000)
   - Método de pago (saldo disponible o agregar fondos)
   - Checkbox de aceptación de términos
7. Usuario ingresa monto deseado (ej: $50,000 COP)
8. Sistema valida que monto >= $1,000 COP
9. Sistema consulta saldo disponible del usuario
10. Sistema verifica que saldo >= monto a invertir
11. Sistema calcula y muestra resumen de inversión:
    - Monto a invertir: $50,000
    - Comisión de gestión (2%): $1,000
    - Total a cobrar: $51,000
    - Participaciones a adquirir: X unidades
    - Impacto ambiental proyectado (anual):
      - CO2 evitado: 0.5 toneladas
      - Árboles equivalentes: 25
12. Usuario revisa resumen y marca checkbox de términos
13. Usuario hace clic en "Confirmar inversión"
14. Sistema solicita autenticación adicional (PIN o biometría si monto > $500,000)
15. Usuario completa autenticación adicional
16. Sistema crea orden de inversión con estado "Procesando"
17. Sistema reserva fondos en cuenta del usuario
18. Sistema procesa transacción:
    - Debita saldo del usuario
    - Registra inversión en base de datos
    - Envía orden a sistema de custodia
19. Sistema de custodia confirma registro de participación
20. Sistema actualiza estado de orden a "Completada"
21. Sistema actualiza portafolio del usuario en tiempo real
22. Sistema calcula y registra impacto ambiental proyectado
23. Sistema genera certificado de inversión (PDF)
24. Sistema envía email de confirmación con:
    - Detalles de la inversión
    - Comprobante de transacción
    - Certificado de inversión adjunto
    - Link a tracking de impacto
25. Sistema envía notificación push: "¡Inversión exitosa! Has invertido $50,000 en [Nombre Fondo]"
26. Sistema registra transacción en log de auditoría
27. Sistema muestra mensaje de éxito con animación celebratoria
28. Sistema ofrece opciones:
    - Ver mi portafolio
    - Explorar más fondos
    - Compartir en redes sociales
29. Usuario es redirigido a su portafolio actualizado

---

## Flujos Alternativos

### FA-1: Usuario invierte con saldo insuficiente
**En el paso 10:**
- 10a. Sistema detecta que saldo < monto a invertir
- 10b. Sistema calcula diferencia: Falta = Monto + Comisión - Saldo
- 10c. Sistema muestra mensaje: "Saldo insuficiente. Necesitas agregar $X más"
- 10d. Sistema ofrece opciones:
  - "Agregar fondos ahora" → Redirige a CU-021
  - "Ajustar monto" → Vuelve a paso 7
  - "Cancelar"
- 10e. Si usuario agrega fondos, flujo continúa en paso 9
- 10f. Si usuario ajusta monto, vuelve a paso 7

### FA-2: Usuario invierte monto menor al mínimo
**En el paso 8:**
- 8a. Sistema detecta que monto < $1,000
- 8b. Sistema muestra mensaje: "El monto mínimo de inversión es $1,000 COP"
- 8c. Sistema ajusta automáticamente el campo a $1,000
- 8d. Sistema explica razón: "Esto permite mantener costos operativos bajos y comisiones justas"
- 8e. Usuario puede aceptar mínimo o cancelar
- 8f. Flujo continúa en paso 9

### FA-3: Inversión requiere autenticación multifactor
**En el paso 14:**
- 14a. Sistema detecta que monto > $500,000 COP
- 14b. Sistema solicita autenticación adicional (MFA)
- 14c. Sistema presenta opciones:
  - Código SMS
  - App de autenticación (TOTP)
  - Biometría (si disponible)
- 14d. Usuario selecciona método y completa verificación
- 14e. Sistema valida autenticación
- 14f. Flujo continúa en paso 16

### FA-4: Fondo alcanza límite de inversión
**En el paso 16:**
- 16a. Sistema verifica capacidad disponible del fondo
- 16b. Fondo está cerca del límite (90% ocupado)
- 16c. Sistema muestra advertencia: "Este fondo está cerca de su capacidad máxima"
- 16d. Sistema sugiere fondos similares
- 16e. Usuario puede:
  - Proceder con inversión si hay espacio
  - Cambiar a fondo sugerido
  - Cancelar
- 16f. Si procede, flujo continúa en paso 17

### FA-5: Usuario cambia de opinión
**En el paso 12-13:**
- 12a. Usuario revisa resumen y no está conforme
- 12b. Usuario hace clic en "Editar monto" o "Cancelar"
- 12c. Si edita, vuelve a paso 7
- 12d. Si cancela, sistema muestra confirmación: "¿Seguro que deseas cancelar?"
- 12e. Si confirma cancelación, caso de uso termina
- 12f. Si no confirma, vuelve a paso 12

---

## Flujos de Excepción

### FE-1: Error en sistema de custodia
**En el paso 19:**
- 19a. Sistema envía orden a custodia
- 19b. Custodia responde con error o no responde (timeout 30s)
- 19c. Sistema intenta 3 reintentos con backoff exponencial
- 19d. Si persiste falla:
  - Sistema marca orden como "Pendiente Confirmación"
  - Sistema revierte débito temporal
  - Sistema guarda orden para procesamiento posterior
  - Sistema envía alerta a equipo técnico
  - Sistema notifica usuario: "Tu inversión está en proceso de confirmación. Te notificaremos cuando se complete"
- 19e. Sistema de reconciliación procesará orden cuando custodia esté disponible
- 19f. Usuario recibe notificación cuando se confirme

### FE-2: Fondo no disponible (agotado)
**En el paso 16:**
- 16a. Sistema verifica disponibilidad actual del fondo
- 16b. Fondo alcanzó 100% de capacidad justo antes de procesar
- 16c. Sistema muestra: "Este fondo alcanzó su capacidad máxima"
- 16d. Sistema sugiere:
  - Fondos similares con disponibilidad
  - Opción de lista de espera para próxima apertura
  - Suscripción a notificaciones de disponibilidad
- 16e. Caso de uso termina o usuario selecciona alternativa

### FE-3: Error de autenticación adicional
**En el paso 15:**
- 15a. Usuario falla autenticación MFA
- 15b. Sistema incrementa contador de intentos
- 15c. Sistema muestra: "Autenticación fallida. Intentos restantes: X"
- 15d. Si intentos < 3, usuario puede reintentar (vuelve a paso 14)
- 15e. Si intentos = 3:
  - Sistema bloquea transacción por 15 minutos
  - Sistema envía alerta de seguridad al usuario
  - Sistema sugiere verificar método de autenticación
- 15f. Usuario debe esperar o contactar soporte

### FE-4: Error de red durante transacción
**En el paso 18:**
- 18a. Sistema pierde conexión durante procesamiento
- 18b. Transacción queda en estado indeterminado
- 18c. Sistema verifica idempotencia usando ID único de transacción
- 18d. Sistema consulta estado real:
  - Si completada: continúa en paso 20
  - Si no completada: revierte cambios
  - Si desconocida: marca para reconciliación manual
- 18e. Sistema notifica usuario según estado determinado

### FE-5: Fondo suspendido por regulación
**En el paso 5:**
- 5a. Usuario intenta invertir en fondo
- 5b. Sistema detecta que fondo fue suspendido temporalmente
- 5c. Sistema muestra: "Este fondo está temporalmente suspendido por revisión regulatoria"
- 5d. Sistema oculta botón "Invertir ahora"
- 5e. Sistema ofrece suscribirse a notificaciones de reactivación
- 5f. Caso de uso termina

### FE-6: Cambio de precio durante transacción
**En el paso 18:**
- 18a. Valor de participación cambió desde paso 11
- 18b. Diferencia > 2%
- 18c. Sistema pausa transacción
- 18d. Sistema recalcula participaciones con nuevo precio
- 18e. Sistema muestra actualización al usuario:
  - Precio anterior: $X
  - Precio actual: $Y
  - Participaciones actualizadas: Z unidades
- 18f. Usuario puede:
  - Aceptar nuevo precio → continúa en paso 16
  - Cancelar transacción
- 18g. Si pasa más de 5 minutos, transacción expira

---

## Reglas de Negocio

- **RN-008.1:** Inversión mínima: $1,000 COP
- **RN-008.2:** Inversión máxima por transacción: $50,000,000 COP
- **RN-008.3:** Comisión de gestión estándar: 2% anual (prorrateada)
- **RN-008.4:** Autenticación multifactor obligatoria para inversiones > $500,000 COP
- **RN-008.5:** Transacciones idempotentes usando UUID único
- **RN-008.6:** Fondos deben tener mínimo 70% de proyectos verificados
- **RN-008.7:** Usuario debe aceptar términos y condiciones específicos del fondo
- **RN-008.8:** Horario de operación: 24/7, pero liquidación ocurre en horario hábil
- **RN-008.9:** Máximo 10 inversiones simultáneas por usuario en mismo fondo
- **RN-008.10:** Información del fondo debe estar actualizada con antigüedad máxima 24 horas

---

## Requisitos No Funcionales

- **RNF-001.1:** Tiempo de respuesta < 3 segundos (pasos UI)
- **RNF-001.2:** Latencia de APIs < 200ms
- **RNF-002.1:** Transacciones encriptadas AES-256
- **RNF-002.2:** Comunicación con custodia sobre TLS 1.3
- **RNF-002.3:** 100% de transacciones registradas en auditoría
- **RNF-003.1:** Disponibilidad 99.9% del sistema de inversiones
- **REST-SEG-004:** Log inmutable de todas las transacciones financieras

---

## Interfaces de Usuario

### Pantallas Involucradas

1. **Catálogo de Fondos:** Grid o lista de fondos disponibles
2. **Detalle de Fondo:** Información completa con gráficos
3. **Modal de Inversión:** Formulario de inversión
4. **Resumen de Inversión:** Confirmación antes de procesar
5. **Autenticación Adicional:** Modal MFA si aplica
6. **Confirmación de Éxito:** Pantalla celebratoria con opciones
7. **Portafolio Actualizado:** Dashboard con nueva inversión

### Componentes UI

- Slider o input numérico para monto
- Indicador de saldo disponible en tiempo real
- Calculadora de comisiones en vivo
- Progress bar durante procesamiento
- Animación celebratoria al completar
- Badge "Recomendado para ti" en fondos sugeridos
- Tooltips explicativos en términos técnicos

---

## Criterios de Aceptación

✅ Usuario puede invertir desde $1,000 COP en cualquier fondo  
✅ Sistema valida saldo disponible en tiempo real  
✅ Comisiones se muestran claramente antes de confirmar  
✅ Autenticación multifactor funciona para montos > $500,000  
✅ Portafolio se actualiza inmediatamente tras inversión exitosa  
✅ Certificado de inversión se genera y envía por email  
✅ Impacto ambiental proyectado se calcula y muestra  
✅ Transacciones son idempotentes (no se duplican)  
✅ Manejo robusto de errores de sistemas externos  
✅ Usuario recibe notificaciones en todos los canales  
✅ Integración con sistema de custodia funciona correctamente  

---

## Dependencias

### Servicios Externos
- **Sistema de Custodia de Valores:** Registro de participaciones
- **Pasarelas de Pago:** Si usuario agrega fondos
- **Motor de Impacto Ambiental:** Cálculo de métricas

### Módulos Internos
- Módulo de Gestión de Portafolio
- Módulo de Transacciones
- Módulo de Notificaciones
- Módulo de Auditoría
- Módulo de Reporting

---

## Riesgos y Mitigaciones

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Custodia no disponible | Media | Alto | Retry + cola de reconciliación + alertas |
| Doble inversión por error | Baja | Crítico | Idempotencia con UUID + validación estado |
| Cambio de precio durante transacción | Alta | Medio | Revalidación + confirmación usuario |
| Sobreventa de fondo | Baja | Alto | Lock optimista + verificación capacidad |
| Pérdida de datos transacción | Baja | Crítico | Transacciones ACID + logs inmutables |

---

## Pruebas Requeridas

### Pruebas Funcionales
- Inversión exitosa con saldo suficiente
- Rechazo por saldo insuficiente
- Validación de monto mínimo
- Autenticación MFA para montos altos
- Generación de certificado

### Pruebas de Integración
- Comunicación con sistema de custodia
- Actualización de portafolio en tiempo real
- Envío de notificaciones multi-canal
- Registro en log de auditoría

### Pruebas de Rendimiento
- 1000 inversiones concurrentes sin degradación
- Tiempo de respuesta < 3 segundos
- Latencia de APIs < 200ms

### Pruebas de Seguridad
- Encriptación end-to-end
- Validación de autenticación
- Prevención de inyección SQL
- Rate limiting (10 transacciones/minuto por usuario)

---

## Referencias

- **Requisito Funcional:** RF-002.1
- **Historia de Usuario:** HU-003
- **Entrevista:** CEO - "cualquier persona, con tan solo mil pesos, pueda invertir"
- **Restricción:** REST-NEG-001 (Inversión mínima $1,000)
- **Restricción:** REST-SEG-003 (MFA para operaciones > $500,000)

---

**Estado:** Aprobado para implementación  
**Última revisión:** 12 de noviembre de 2025
