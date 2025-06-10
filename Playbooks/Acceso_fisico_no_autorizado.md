# Playbook de Respuesta a Incidente: R-06 - Acceso físico no autorizado a salas de servidores

## 🛑 Clasificación del Incidente
**Categoría ANCI**: Intrusión-Acceso no autorizado (Físico)  
**Nivel de Criticidad**: Alta  
**Tipo de Activo Afectado**: Infraestructura física (sala de servidores, racks, sistemas de control de acceso)

## 🧩 Descripción
Este incidente se refiere a la entrada de personas no autorizadas a las salas donde se alojan servidores y equipos críticos, ya sea por falla de seguridad, error humano o intrusión intencional. Este acceso compromete la integridad, disponibilidad o confidencialidad de los activos informáticos institucionales.

## 👥 Roles y Responsabilidades
| Rol                     | Responsabilidad                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| CSIRT Universitario     | Coordina análisis de impacto e investigación técnica                           |
| Seguridad Física        | Investiga el acceso, revisa grabaciones, refuerza vigilancia                   |
| Dirección de Informática| Evalúa posible impacto en sistemas alojados en la sala                         |
| Encargado de Infraestructura | Verifica funcionamiento de servidores y otros equipos                   |
| Área Jurídica / Legal   | Asesora en acciones legales si corresponde                                     |

---

## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

### **Herramientas para la Detección**
- **Sistemas de Control de Acceso (NIST 800-53: AC-2, AC-3)**
    - Utilización de tarjetas de acceso, biometría o reconocimiento facial para autenticar a usuarios antes de ingresar a salas de servidores.
    - **CIS Control 4**: Uso de acceso controlado y monitoreo continuo de entradas/salidas.
  
- **Cámaras de Seguridad y Sensores de Movimiento (NIST 800-53: PE-3, PE-6)**
    - Monitoreo en tiempo real y registro de eventos de acceso físico no autorizado mediante cámaras de seguridad.
    - **CIS Control 8**: Aseguramiento de que todas las instalaciones físicas críticas estén bajo vigilancia.

- **Software de Monitoreo de Infraestructura Física**
    - Herramientas que permitan revisar el acceso físico a los servidores y gestionar las bitácoras de acceso. 
    - **CIS Control 12**: Integración de controles para monitoreo de seguridad física y de los dispositivos.
  
### **Recursos Técnicos para Respuesta**
- **Equipos de Seguridad Física**:
    - **Control de Cerraduras de Alta Seguridad**: Implementación de cerraduras electrónicas que ofrezcan un mayor control de los accesos.
    - **Sistemas de Alarmas**: Utilización de sistemas de alarma para detectar accesos no autorizados.
  
- **Herramientas de Comunicación de Emergencia (NIST 800-61r3)**:
    - Establecimiento de un sistema de comunicación de emergencia para todo el equipo de respuesta ante incidentes.
    - Herramientas de mensajería instantánea o aplicaciones de comunicación interna como **Slack** o **Microsoft Teams** para coordinar las acciones de contención y mitigación de daños.

-   **Herramientas de Autenticación de Acceso (NIST 800-63)**:
    - Sistemas que utilicen autenticación multifactor (MFA) para reforzar el control sobre los accesos físicos y reducir el riesgo de accesos no autorizados.


### **Recomendaciones para Implementar las Herramientas**
- Realizar una **evaluación continua de las herramientas de seguridad física**, incluyendo cámaras y sistemas de control de acceso, para verificar su eficacia en la prevención de accesos no autorizados.
  
- **Automatizar las alertas** en los sistemas de monitoreo para que se actúe de forma inmediata en caso de detección de accesos no autorizados.

- **Realizar simulacros** periódicos para asegurarse de que todos los roles y responsabilidades, definidos en el playbook, estén bien coordinados y ejecutados en caso de un incidente real.
 

### **Recursos Adicionales**
- **CIS Control 4**: Implementación de controles de acceso físico que prevengan el ingreso no autorizado a instalaciones.
  
- **NIST 800-53**: Incorporación de controles físicos en el entorno de TI para proteger las instalaciones, el equipo y la información.

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

## 📦 Evidencias a Recolectar
- Registro de accesos físicos (bitácora, software de control)
- Imágenes de cámaras de seguridad
- Estado físico de la infraestructura (puertas, cerraduras, equipos)
- Declaraciones del personal presente o testigos

## 📌 Indicadores de Compromiso (IOC)
- Accesos fuera de horario o por usuarios no autorizados
- Manipulación de cables, conectores o sensores
- Corte de energía no programado
- Fallas simultáneas en varios equipos del rack

## 📅 Tiempo Estimado de Contención y Recuperación
**Contención**: ≤ 2 horas  
**Recuperación**: 12–24 horas (según el nivel de revisión requerido)

## ✅ Checklist de Validación Final
- [ ] Acceso restringido temporalmente
- [ ] Verificación de integridad de los equipos
- [ ] Registro del incidente físico generado
- [ ] Medidas correctivas aplicadas
- [ ] Reporte final validado por TI y Seguridad
