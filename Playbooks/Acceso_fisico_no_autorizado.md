# Playbook de Respuesta a Incidente: R-06 - Acceso físico no autorizado a salas de servidores

## 🛑 Clasificación del Incidente
**Categoría ANCI**: Intrusión-Acceso no autorizado (Físico)  
**Nivel de Criticidad**: Alta  
**Tipo de Activo Afectado**: Infraestructura física (sala de servidores, racks, sistemas de control de acceso)

## 🧩 Descripción
El incidente se refiere a la entrada de personas no autorizadas a las salas donde se alojan servidores y equipos críticos, ya sea por falla de seguridad, error humano o intrusión intencional. Este acceso compromete la integridad, disponibilidad o confidencialidad de los activos informáticos institucionales.

## 👥 Roles y Responsabilidades
| Rol                     | Responsabilidad                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| CSIRT Universitario     | Coordina análisis de impacto e investigación técnica                           |
| Seguridad Física        | Investiga el acceso, revisa grabaciones, refuerza vigilancia                   |
| Dirección de Informática| Evalúa posible impacto en sistemas alojados en la sala                         |
| Encargado de Infraestructura | Verifica funcionamiento de servidores y otros equipos                   |
| Área Jurídica / Legal   | Asesora en acciones legales si corresponde                                     |

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