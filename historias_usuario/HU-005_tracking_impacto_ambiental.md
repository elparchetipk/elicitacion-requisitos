# 📋 HISTORIA DE USUARIO - Tracking de Impacto Ambiental

## Información General

**ID:** HU-005  
**Título:** Calcular y visualizar impacto ambiental de inversiones  
**Épica/Módulo:** RF-003: Dashboard y Experiencia de Usuario  
**Prioridad:** MUST (Crítico)  
**Puntos de Historia:** 8  
**Sprint/Iteración:** Sprint 3

---

## Historia de Usuario

**Como** usuario inversionista consciente del medio ambiente  
**Quiero** ver el impacto ambiental real que generan mis inversiones  
**Para** sentirme motivado y validar que mi dinero está generando cambio positivo tangible

---

## Descripción Detallada

Esta funcionalidad convierte inversiones abstractas en impacto ambiental concreto y medible. El sistema debe recopilar datos reales de los proyectos (energía generada, hectáreas reforestadas, emisiones evitadas), calcular la contribución proporcional de cada inversionista, y presentar las métricas en formato comprensible y motivador.

Las métricas clave son:

- **CO2 evitado:** Toneladas de emisiones reducidas
- **Árboles plantados:** Número de árboles sembrados y en crecimiento
- **Familias beneficiadas:** Hogares con acceso a energía limpia o beneficios económicos
- **Energía limpia generada:** kWh de energía renovable

Los usuarios deben poder descargar certificados de impacto y compartir sus logros en redes sociales.

---

## Criterios de Aceptación

### Escenario 1: Visualizar impacto ambiental personal

```gherkin
Dado que tengo inversiones activas en proyectos ambientales
Cuando accedo a la sección "Mi Impacto Ambiental"
Entonces veo mis métricas consolidadas: toneladas CO2 evitadas, árboles plantados, familias beneficiadas
Y veo gráficos visuales que representan el impacto (ej: iconos de árboles)
Y veo la evolución de mi impacto en el tiempo
Y cada métrica tiene una explicación clara de cómo se calcula
```

### Escenario 2: Desglose de impacto por proyecto

```gherkin
Dado que estoy viendo mi impacto ambiental total
Cuando selecciono "Ver desglose por proyecto"
Entonces veo una lista de mis inversiones
Y cada inversión muestra su contribución específica al impacto total
Y puedo ver qué proyectos generan mayor impacto
Y puedo navegar a detalles del proyecto
```

### Escenario 3: Comparación con benchmarks

```gherkin
Dado que estoy viendo mis métricas de impacto
Cuando veo cada métrica principal
Entonces veo una comparación: "Tu impacto es X% mayor que el promedio"
Y puedo comparar con: promedio de usuarios, promedio de mi perfil, mejores del mes
Y veo mi ranking de impacto (opcional, gamificación)
```

### Escenario 4: Descarga de certificado de impacto

```gherkin
Dado que he generado impacto ambiental medible
Cuando solicito descargar mi certificado de impacto
Entonces el sistema genera un PDF personalizado
Y el certificado incluye: mi nombre, período, métricas de impacto, proyectos participados
Y tiene diseño profesional con identidad visual de la plataforma
Y incluye un código QR de verificación única
```

### Escenario 5: Compartir impacto en redes sociales

```gherkin
Dado que estoy orgulloso de mi impacto ambiental
Cuando selecciono "Compartir mi impacto"
Entonces puedo elegir: Facebook, Twitter, Instagram, LinkedIn
Y se genera una imagen con diseño atractivo mostrando mis métricas destacadas
Y incluye un link a la plataforma para referidos
Y el sistema registra el compartido para analytics
```

### Escenario 6: Actualización mensual de métricas

```gherkin
Dado que es el primer día del mes
Cuando el sistema recalcula las métricas de impacto
Entonces mis métricas se actualizan con datos del mes anterior
Y recibo una notificación: "Tu impacto del mes: X toneladas CO2"
Y puedo ver el reporte mensual detallado
Y se me sugiere incrementar mi inversión si mi impacto disminuyó
```

### Escenario 7: Equivalencias comprensibles de impacto

```gherkin
Dado que estoy viendo mi impacto de CO2 evitado
Cuando veo "10 toneladas de CO2 evitadas"
Entonces el sistema muestra equivalencias: "Equivale a X autos fuera de circulación por un año"
Y las equivalencias ayudan a dimensionar el impacto
Y son calculadas con estándares reconocidos (EPA, ONU)
```

---

## Reglas de Negocio

- **RN-005.1:** Las métricas se actualizan mensualmente con datos de proyectos
- **RN-005.2:** El cálculo de impacto es proporcional a la inversión del usuario en cada proyecto
- **RN-005.3:** Solo se muestran métricas verificadas por los proyectos
- **RN-005.4:** Los certificados son únicos con código de verificación
- **RN-005.5:** Las comparaciones con promedio son anónimas
- **RN-005.6:** Equivalencias basadas en estándares internacionales (EPA, IPCC)
- **RN-005.7:** Usuarios pueden descargar máximo 5 certificados por mes (prevenir abuso)

---

## Definición de Terminado (DoD)

- [x] Código desarrollado y cumple con estándares
- [x] Pruebas unitarias implementadas (cobertura mínima 80%)
- [x] Algoritmo de cálculo validado por experto ambiental
- [x] Fórmulas de equivalencias verificadas con estándares internacionales
- [x] Revisión de código (code review) completada
- [x] Documentación técnica actualizada
- [x] Pruebas de aceptación pasadas por PO
- [x] Diseño de certificados aprobado por marketing
- [x] Despliegue en ambiente de pruebas
- [x] Sin defectos críticos o bloqueantes abiertos

---

## Notas Técnicas

**Stack/Tecnología:**

- Backend: Servicio de cálculo de impacto con scheduler mensual
- Generación de PDFs: Biblioteca puppeteer o similar
- Generación de imágenes para RRSS: Canvas o servicio de diseño dinámico
- API REST para obtener métricas
- Almacenamiento de certificados generados (S3 o similar)

**Dependencias:**

- [HU-003] Inversiones en proyectos
- [HU-004] Dashboard para mostrar métricas
- API de proyectos con datos de impacto real
- Sistema de reportes de proyectos
- Base de datos de métricas históricas

**Consideraciones de Seguridad:**

- Certificados con código único de verificación
- Prevenir generación masiva de certificados (rate limiting)
- Validar que el usuario tiene inversiones antes de generar certificado
- Logs de todas las descargas y compartidos

**Consideraciones de Performance:**

- Cálculo de métricas en batch mensual (no en tiempo real)
- Caché de métricas calculadas
- Generación asíncrona de PDFs (no bloquear UI)
- Pre-cálculo de equivalencias comunes
- Compresión de imágenes para compartir en RRSS

---

## Mockups/Wireframes

- Mockup: `/diseño/impacto-ambiental-dashboard.png`
- Mockup: `/diseño/desglose-impacto-proyectos.png`
- Mockup: `/diseño/certificado-impacto.pdf`
- Mockup: `/diseño/compartir-rrss.png`

---

## Tareas Técnicas (Subtareas)

- [ ] Diseñar modelo de datos para métricas de impacto
- [ ] Crear endpoint GET /api/v1/impact/metrics
- [ ] Crear endpoint GET /api/v1/impact/breakdown
- [ ] Implementar algoritmo de cálculo proporcional de impacto
- [ ] Implementar scheduler para actualización mensual
- [ ] Implementar cálculo de equivalencias (CO2 → autos, árboles → hectáreas)
- [ ] Diseñar plantilla de certificado de impacto en PDF
- [ ] Crear endpoint POST /api/v1/impact/certificate para generar PDF
- [ ] Implementar generación de imágenes para RRSS
- [ ] Crear componente de visualización de métricas con gráficos
- [ ] Crear componente de comparación con benchmarks
- [ ] Crear componente de compartir en RRSS
- [ ] Implementar sistema de verificación de certificados
- [ ] Crear página pública de verificación de certificados
- [ ] Implementar notificaciones mensuales de impacto
- [ ] Crear pruebas del algoritmo de cálculo
- [ ] Documentar fórmulas y fuentes de datos

---

## Casos de Prueba Principales

1. **CP-005.1: Cálculo correcto de impacto proporcional**

   - **Entrada:** Usuario invierte $10,000 en proyecto que evitó 100 ton CO2, inversión total del proyecto $1,000,000
   - **Resultado esperado:** Usuario tiene 1 tonelada CO2 evitada atribuida

2. **CP-005.2: Actualización mensual de métricas**

   - **Entrada:** Día 1 del mes, proyectos reportaron nuevos datos
   - **Resultado esperado:** Métricas recalculadas, notificaciones enviadas

3. **CP-005.3: Generación de certificado PDF**

   - **Entrada:** Usuario solicita certificado
   - **Resultado esperado:** PDF generado con datos correctos, código QR único

4. **CP-005.4: Verificación de certificado**

   - **Entrada:** Código de verificación de certificado
   - **Resultado esperado:** Página muestra autenticidad del certificado

5. **CP-005.5: Equivalencias comprensibles**

   - **Entrada:** 10 toneladas CO2 evitadas
   - **Resultado esperado:** "Equivale a 2.2 autos fuera de circulación por un año"

6. **CP-005.6: Comparación con promedio**

   - **Entrada:** Usuario con impacto 20% superior al promedio
   - **Resultado esperado:** Mensaje: "Tu impacto es 20% mayor que el promedio"

7. **CP-005.7: Desglose por proyecto**

   - **Entrada:** Usuario con 3 inversiones diferentes
   - **Resultado esperado:** Lista con contribución de cada proyecto al impacto total

8. **CP-005.8: Límite de certificados mensuales**
   - **Entrada:** Usuario intenta descargar 6to certificado en el mes
   - **Resultado esperado:** Error: "Límite mensual alcanzado"

---

## Validación INVEST

- [x] **I**ndependiente: Requiere inversiones pero es independiente en desarrollo
- [x] **N**egociable: Métricas específicas y equivalencias son ajustables
- [x] **V**aliosa: Diferenciador clave, motiva retención y engagement
- [x] **E**stimable: 8 puntos por algoritmos y generación de documentos
- [x] **S**mall (Pequeña): Completable en un sprint
- [x] **T**esteable: Cálculos verificables, certificados validables

---

## Historial de Cambios

| Fecha      | Versión | Autor              | Descripción                         |
| ---------- | ------- | ------------------ | ----------------------------------- |
| 22/10/2025 | 1.0     | Equipo de Análisis | Creación inicial basada en RF-003.2 |
