# Playbook de Respuesta a Incidente: R-06 - Acceso físico no autorizado a salas de servidores

### 🔍 Fuente de Información y Marco Normativo  
Este playbook se elabora conforme a:  
1. **Taxonomía de Incidentes de la Agencia Nacional de Ciberseguridad (ANCI)**:  
   - Clasificación por efectos observables (Resolución Exenta N°1.234/2024)  
2. **Ley Marco de Ciberseguridad (21.663)**:  
   - Art. 8° (Deberes específicos de los operadores de importancia vital.)  
   - Art. 9° (Plazos de reporte al CSIRT Nacional)  
3. **Protocolos Internos de la Universidad de Los Lagos**:  
   - Roles del CSIRT Universitario
   - Matriz de Clasificación de Activos Críticos  
4. **Estándares Internacionales**:  
   - NIST SP 800-61 (Respuesta a Incidentes)  
   - CIS Critical Security Controls v8.1.2
   - NIST SP 800-53 Rev. 5

## 🛑 Clasificación del Incidente
---
> [!Importante:]
> "Clasificar siempre por efectos observables, no por causas u orígenes. Registrar todo contexto verificable."
---
*Área de impacto*: Intrusión-Acceso no autorizado (Físico)  
*Impacto Operativo*: Alta  
*Tipo de Activo Afectado*: Infraestructura física (sala de servidores, racks, sistemas de control de acceso)

## 🧩 Descripción
El incidente se refiere a la entrada de personas no autorizadas a las salas donde se alojan servidores y equipos críticos, ya sea por falla de seguridad, error humano o intrusión intencional. Este acceso compromete la integridad, disponibilidad o confidencialidad de los activos informáticos institucionales.

---

### 👥 Roles y Responsabilidades  
| Rol                          | Responsabilidad                                                                       |
|------------------------------|---------------------------------------------------------------------------------------|
| Seguridad Física             | Verificar registros acceso, revisar dispositvos de videovigilancia, asegurar perímetro|
| CSIRT Universitario          | Evaluar impacto técnico, revisar logs de consolas                                     |
| Delegado Ciberseguridad      | Reportar al CSIRT Nacional (<3h Art. 9°)                                              |
| Encargado Infraestructura    | Inspeccionar equipos por manipulación física                                          |
| Asesor Legal                 | Gestionar denuncia policial si hay intrusión                                          |

---

## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

**NIST SP 800-53 Rev. 5:**
- `PE-2`: Autorizaciones de Acceso Físico
- `PE-3`: Control de acceso físico
- `PE-6`: Monitoreo del acceso físico
- `PE-8`: Registros de acceso de visitantes
- `PE-12`: Iluminación de emergencia
- `PE-14`: Controles ambientales

**Controles Críticos de Seguridad CIS:**
- `CIS Control 1`: El Control 1 es la base para saber qué activos (servidores) necesitan ser protegidos físicamente.  
- `CIS Control 3`: Seguridad física para oficinas, áreas de trabajo y áreas seguras
- `CIS Control 5`: Monitoreo y control de cuentas (para sistemas de control de acceso)
- `CIS Control 8`: Los "registros de control de acceso (por ejemplo, cerraduras electrónicas, sistema de alarma)" (access control logs (e.g., electronic locks, alarm system)). Esto significa que cualquier sistema de control de acceso físico implementado para proteger las salas de servidores (como cerraduras electrónicas) debe generar registros que deben ser recopilados, revisados y retenidos según lo especificado en este control.
- `CIS Control 14`: Conciencia de Seguridad y Capacitación de Habilidades 
- `CIS Control 18`: Pruebas de Penetración

**Herramientas Recomendadas:**
- Sistemas de Control de Acceso Físico (PACS): LenelS2, Honeywell WIN-PAK, Genetec
- Videovigilancia: cámaras Axis, Milestone XProtect, grabadores Hikvision NVR
- Sistemas de Detección de Intrusos: Bosch, DSC, Paradox
- Gestión de Registros de Acceso: CCURE 9000, Gallagher Command Centre
- Monitoreo Ambiental: APC NetBotz, Schneider EcoStruxure
- Sistemas Biométricos: Suprema BioStar, HID Signo
- Seguimiento de Activos: RF Code, Ekahau RTLS
- Sistemas de Gestión de Visitantes: Envoy, Proxyclick

---

## 🧭 Fases de Respuesta

### 1. Preparación
- Implementar políticas de control de acceso físico basadas en roles
- Contar con cámaras de vigilancia, registros biométricos o credenciales
- Realizar simulacros de respuesta ante incidentes físicos

### 2. Detección y Análisis
- Revisar logs de acceso físico (bitácoras, sensores, tarjetas)
- Verificar si se han alterado cables, puertos o equipos
- Identificar usuarios presentes en el momento del acceso

### 3. Contención
- Restringir acceso temporalmente al área comprometida
- Realizar inspección física y eléctrica de los equipos
- Cambiar credenciales de acceso físico si aplica

### 4. Erradicación
- Reparar cerraduras, tarjetas o mecanismos vulnerados
- Reforzar puntos débiles del perímetro de seguridad física
- Actualizar controles de ingreso en sistemas automatizados

### 5. Recuperación
- Restaurar condiciones normales de acceso con mayor control
- Validar que los sistemas y la infraestructura no presenten alteraciones
- Reanudar operaciones con registro de todos los accesos futuros

### 6. Lecciones Aprendidas
- Evaluar fallas humanas, tecnológicas o procedimentales
- Reentrenar al personal de seguridad si corresponde
- Establecer sanciones o acciones legales si hubo dolo

---

## 📦 Registros y Evidencias
- Registro de accesos físicos (bitácora, software de control)
- Imágenes de cámaras de seguridad
- Estado físico de la infraestructura (puertas, cerraduras, equipos)
- Declaraciones del personal presente o testigos

---

## 📌 Indicadores de Compromiso (IOC)
- Intentos de acceso fuera de horario laboral  
- Credenciales RFID clonadas (mismo ID en múltiples ubicaciones)  
- Eventos "Puerta forzada" en sistema de alarmas  
- Conexiones SSH/consola desde IPs no autorizadas post-acceso  
- Dispositivos USB desconocidos conectados a servidores  

---

## 📅 Tiempo Estimado de Contención y Recuperación
- Se necesita definir estimaciones para la universidad, podrian basarse en escenarios hipotéticos de respuesta rápida:
- Detección y contención: 30–60 min para acceso físico no autorizado.
- Recuperación completa: 4–24 h, según el nivel de revisión forense y restauración del ambiente.
**Contención**: ≤ 2 horas  
**Recuperación**: 12–24 horas (según el nivel de revisión requerido)

---

## ✅ Checklist de Validación Final
- [ ] Verificar integridad de sellos de seguridad en equipos  
- [ ] Revisar logs de acceso físico últimos 7 días  
- [ ] Analizar grabaciones CCTV período sospechoso  
- [ ] Rotar credenciales RFID/BIOMÉTRICAS  
- [ ] Escanear puertos consola (iDRAC/iLO) por accesos no autorizados  
- [ ] Validar estado de sensores de movimiento/intrusión  
- [ ] Actualizar políticas de acceso en sistema central 

## Reporte ANCI
Plataforma: [https://portal.anci.gob.cl]

**Campos requeridos:**
- [ ] Código categoría principal + subcategoría
- [ ] Hora detección primer efecto
- [ ] Sistemas/servicios afectados
- [ ] Evidencia técnica (logs, capturas)
- [ ] Nivel de criticidad (Alto/Medio/Bajo)