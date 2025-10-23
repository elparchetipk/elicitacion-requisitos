# 📋 HISTORIA DE USUARIO - Dashboard Principal Personalizado

## Información General

**ID:** HU-004  
**Título:** Visualizar dashboard personalizado con portafolio e impacto ambiental  
**Épica/Módulo:** RF-003: Dashboard y Experiencia de Usuario  
**Prioridad:** MUST (Crítico)  
**Puntos de Historia:** 8  
**Sprint/Iteración:** Sprint 2

---

## Historia de Usuario

**Como** usuario inversionista activo  
**Quiero** ver un dashboard personalizado con mi portafolio, rendimiento e impacto ambiental  
**Para** tomar decisiones informadas y sentirme motivado por el impacto positivo que genero

---

## Descripción Detallada

El dashboard es la vista principal de la aplicación y debe consolidar toda la información relevante para el usuario:

- Valor actual del portafolio con gráfico de tendencia
- Rendimiento acumulado (porcentaje y valor absoluto)
- Métricas de impacto ambiental personal (CO2 evitado, árboles plantados, familias beneficiadas)
- Oportunidades de inversión recomendadas según perfil
- Actividad reciente y notificaciones importantes

Debe ser altamente visual, actualizado en tiempo real, y optimizado para mobile y desktop. La información debe presentarse de forma que motive al usuario a seguir invirtiendo.

---

## Criterios de Aceptación

### Escenario 1: Acceder al dashboard con inversiones activas

```gherkin
Dado que soy un usuario con inversiones activas
Cuando accedo al dashboard principal
Entonces veo el valor total actual de mi portafolio destacado
Y veo un gráfico de tendencia del último mes
Y veo mi rendimiento acumulado en porcentaje y pesos
Y veo métricas de impacto: CO2 evitado, árboles plantados, familias beneficiadas
Y veo al menos 3 oportunidades recomendadas basadas en mi perfil
Y veo mi actividad reciente (últimas 5 transacciones)
```

### Escenario 2: Dashboard de usuario sin inversiones

```gherkin
Dado que soy un usuario nuevo sin inversiones
Cuando accedo al dashboard
Entonces veo un mensaje motivacional de bienvenida
Y veo fondos recomendados para comenzar a invertir
Y veo contenido educativo sobre inversión verde
Y veo un CTA claro: "Hacer mi primera inversión"
Y no veo gráficos de rendimiento vacíos
```

### Escenario 3: Actualización en tiempo real del portafolio

```gherkin
Dado que estoy viendo mi dashboard
Cuando el valor de mis inversiones cambia (actualización de mercado)
Entonces el valor total se actualiza automáticamente sin refrescar
Y el gráfico de tendencia se actualiza
Y veo un indicador visual del cambio (verde para ganancia, rojo para pérdida)
Y la actualización ocurre en menos de 5 segundos
```

### Escenario 4: Interacción con gráficos de rendimiento

```gherkin
Dado que estoy en el dashboard viendo el gráfico de tendencia
Cuando paso el mouse sobre un punto del gráfico
Entonces veo un tooltip con la fecha y valor exacto
Y puedo cambiar el período: 1 semana, 1 mes, 3 meses, 1 año, todo
Y el gráfico se actualiza mostrando el período seleccionado
```

### Escenario 5: Navegar desde dashboard a detalles de inversión

```gherkin
Dado que veo mi lista de inversiones en el dashboard
Cuando hago click en una inversión específica
Entonces soy redirigido a la página de detalles de esa inversión
Y puedo ver información completa y opciones de gestión
```

### Escenario 6: Notificaciones importantes en dashboard

```gherkin
Dado que tengo notificaciones pendientes
Cuando accedo al dashboard
Entonces veo un badge con el número de notificaciones sin leer
Y las notificaciones importantes aparecen destacadas
Y puedo ver: rendimientos mensuales, nuevas oportunidades, actualizaciones de proyectos
Y puedo marcar como leídas o acceder a detalles
```

### Escenario 7: Comparación con promedio de usuarios

```gherkin
Dado que estoy viendo mis métricas de impacto
Cuando veo el impacto ambiental generado
Entonces puedo comparar mi impacto con el promedio de usuarios similares
Y veo un indicador: "Tu impacto es X% mayor que el promedio"
Y esto me motiva a seguir invirtiendo
```

---

## Reglas de Negocio

- **RN-004.1:** Los valores del portafolio se actualizan cada 5 segundos máximo
- **RN-004.2:** El gráfico de tendencia muestra al menos 7 días de historia
- **RN-004.3:** Métricas de impacto se calculan en base a proyectos reales
- **RN-004.4:** Las recomendaciones se basan en: perfil de riesgo, historial, tendencias
- **RN-004.5:** Actividad reciente muestra últimas 5 transacciones
- **RN-004.6:** Dashboard debe cargar en menos de 2 segundos
- **RN-004.7:** Usuarios sin inversiones ven contenido motivacional, no vacío

---

## Definición de Terminado (DoD)

- [x] Código desarrollado y cumple con estándares
- [x] Pruebas unitarias implementadas (cobertura mínima 80%)
- [x] Pruebas de performance (tiempo de carga <2s)
- [x] Responsive design validado en mobile, tablet, desktop
- [x] Revisión de código (code review) completada
- [x] Documentación técnica actualizada
- [x] Pruebas de aceptación pasadas por PO
- [x] Despliegue en ambiente de pruebas
- [x] Sin defectos críticos o bloqueantes abiertos
- [x] Validación de cálculos de impacto por área ambiental

---

## Notas Técnicas

**Stack/Tecnología:**

- Frontend: React/Vue con componentes reutilizables
- Gráficos: Chart.js o D3.js para visualizaciones
- WebSockets o Server-Sent Events para actualizaciones en tiempo real
- API REST para cargar datos iniciales
- Caché del lado del cliente para optimización

**Dependencias:**

- [HU-001] Usuario autenticado
- [HU-003] Inversiones realizadas (o contenido para usuarios sin inversiones)
- Sistema de cálculo de impacto ambiental
- Sistema de recomendaciones
- Base de datos de transacciones y valoraciones

**Consideraciones de Seguridad:**

- Solo mostrar datos del usuario autenticado
- Validar permisos en cada endpoint de API
- No exponer datos sensibles de otros usuarios en comparaciones
- Rate limiting en actualizaciones en tiempo real

**Consideraciones de Performance:**

- Lazy loading de componentes no críticos
- Caché de datos del portafolio (invalidado en transacciones)
- Optimización de queries de base de datos con índices
- CDN para assets estáticos
- Compresión de respuestas API
- Paginación de actividad reciente si es necesaria

---

## Mockups/Wireframes

- Mockup: `/diseño/dashboard-principal-desktop.png`
- Mockup: `/diseño/dashboard-principal-mobile.png`
- Mockup: `/diseño/dashboard-sin-inversiones.png`
- Mockup: `/diseño/graficos-interactivos.png`

---

## Tareas Técnicas (Subtareas)

- [ ] Diseñar arquitectura de componentes del dashboard
- [ ] Crear endpoint GET /api/v1/dashboard/summary
- [ ] Crear endpoint GET /api/v1/portfolio/performance?period=
- [ ] Crear endpoint GET /api/v1/impact/metrics
- [ ] Implementar WebSocket/SSE para actualizaciones en tiempo real
- [ ] Desarrollar componente de resumen de portafolio
- [ ] Desarrollar componente de gráfico de tendencia interactivo
- [ ] Desarrollar componente de métricas de impacto ambiental
- [ ] Desarrollar componente de recomendaciones personalizadas
- [ ] Desarrollar componente de actividad reciente
- [ ] Desarrollar componente de notificaciones
- [ ] Implementar estado vacío motivacional para usuarios sin inversiones
- [ ] Optimizar performance de carga del dashboard
- [ ] Implementar animaciones y transiciones suaves
- [ ] Crear pruebas de integración del dashboard completo
- [ ] Documentar endpoints y estructura de datos

---

## Casos de Prueba Principales

1. **CP-004.1: Carga inicial del dashboard con datos**

   - **Entrada:** Usuario con 3 inversiones activas
   - **Resultado esperado:** Todos los componentes cargan en <2s, datos correctos

2. **CP-004.2: Dashboard vacío (usuario sin inversiones)**

   - **Entrada:** Usuario nuevo sin inversiones
   - **Resultado esperado:** Contenido motivacional, CTA visible, sin gráficos vacíos

3. **CP-004.3: Actualización en tiempo real**

   - **Entrada:** Cambio en valoración de fondo
   - **Resultado esperado:** Dashboard actualiza en <5s automáticamente

4. **CP-004.4: Gráfico interactivo cambia período**

   - **Entrada:** Usuario selecciona "3 meses"
   - **Resultado esperado:** Gráfico muestra datos de 3 meses correctamente

5. **CP-004.5: Cálculo correcto de impacto ambiental**

   - **Entrada:** Usuario con inversión de $100,000 en fondo solar
   - **Resultado esperado:** Métricas de CO2, árboles calculadas según proyecto

6. **CP-004.6: Recomendaciones personalizadas**

   - **Entrada:** Usuario con perfil conservador
   - **Resultado esperado:** Recomendaciones de fondos de bajo riesgo

7. **CP-004.7: Responsive en mobile**

   - **Entrada:** Acceso desde smartphone 375px ancho
   - **Resultado esperado:** Layout adaptado, touch-friendly, legible

8. **CP-004.8: Comparación con promedio**
   - **Entrada:** Usuario con impacto superior al promedio
   - **Resultado esperado:** Mensaje motivacional con porcentaje correcto

---

## Validación INVEST

- [x] **I**ndependiente: Depende de datos pero puede desarrollarse independientemente
- [x] **N**egociable: Layout y componentes específicos son flexibles
- [x] **V**aliosa: Vista principal de la app, experiencia clave del usuario
- [x] **E**stimable: 8 puntos por complejidad de visualizaciones y tiempo real
- [x] **S**mall (Pequeña): Completable en un sprint
- [x] **T**esteable: Criterios claros, métricas medibles

---

## Historial de Cambios

| Fecha      | Versión | Autor              | Descripción                         |
| ---------- | ------- | ------------------ | ----------------------------------- |
| 22/10/2025 | 1.0     | Equipo de Análisis | Creación inicial basada en RF-003.1 |
