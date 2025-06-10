# Playbook de Respuesta a Incidente: R-07 - Robo o pérdida de equipos con información sensible

## 🛑 Clasificación del Incidente
**Categoría ANCI**: Pérdida o Robo de Equipamiento  
**Nivel de Criticidad**: Alta  
**Tipo de Activo Afectado**: Equipos de usuarios finales o institucionales con información sensible (laptops, discos duros, USB)

## 🧩 Descripción
Este incidente implica la pérdida o sustracción de equipos que almacenan información sensible o confidencial, ya sea por robo, extravío o hurto. Esto representa un riesgo grave de filtración, suplantación de identidad, o pérdida de información crítica para la Universidad.

## 👥 Roles y Responsabilidades
| Rol                               | Responsabilidad                                                                 |
|-----------------------------------|---------------------------------------------------------------------------------|
| CSIRT Universitario               | Coordina la evaluación del impacto y medidas de contención                      |
| Encargado de Seguridad de la Información | Evalúa el nivel de exposición de datos y posibles consecuencias            |
| Dirección de Informática          | Apoya en verificación de respaldos y revocación de accesos                     |
| Usuario Afectado                  | Reporta el incidente, proporciona información del equipo                      |
| Seguridad / Legal                 | Realiza denuncia si aplica, gestiona seguimiento legal                         |

## 🛠️ Herramientas y Recursos (NIST/CIS Controls)

**NIST SP 800-53 Rev. 5:**
- `AC-3`: Aplicación de controles de acceso
- `AC-6`: Privilegio mínimo
- `MP-5`: Transporte de medios
- `SC-28`: Protección de la información en reposo
- `IR-4`: Manejo de incidentes

**Controles Críticos de Seguridad CIS:**
- `CIS Control 3`: Protección de datos (Cifrado)
- `CIS Control 8`: Defensas contra malware (Seguridad de endpoints)
- `CIS Control 10`: Capacidad de recuperación de datos
- `CIS Control 13`: Protección de datos en dispositivos móviles
- `CIS Control 16`: Monitoreo y control de cuentas

**Herramientas Recomendadas:**
- Gestión de Dispositivos Móviles (MDM): Jamf, Intune, Google Admin
- Cifrado de disco completo: BitLocker, FileVault, LUKS
- Soluciones de borrado remoto: Prey, Absolute, Apple Business Manager
- Gestión de identidad y acceso: Okta, Azure AD Conditional Access
- Herramientas de verificación de respaldos: Veeam, Acronis, Backup Exec

## 🧭 Fases de Respuesta

### 1. Preparación
- Establecer políticas de cifrado en equipos móviles e institucionales
- Habilitar servicios de borrado remoto y geolocalización
- Crear cultura de respaldo periódico de datos

### 2. Detección y Análisis
- Confirmar fecha, hora y contexto de la pérdida o robo
- Determinar tipo de información almacenada en el equipo
- Identificar si contenía accesos privilegiados o información crítica

### 3. Contención
- Revocar credenciales y accesos desde el equipo comprometido
- Bloquear cuentas de usuario vinculadas si es necesario
- Habilitar funciones de borrado remoto (MDM, Google Admin, etc.)

### 4. Erradicación
- Realizar denuncias ante la autoridad competente si aplica
- Revisar logs de actividad reciente del equipo si hay sincronización en la nube
- Validar que no existan brechas activas en otros sistemas relacionadas

### 5. Recuperación
- Reemplazar dispositivo si es necesario
- Restaurar datos desde respaldo verificado
- Realizar seguimiento del caso con el área jurídica

### 6. Lecciones Aprendidas
- Identificar fallas en la cadena de custodia de los equipos
- Evaluar si se aplicaron correctamente las políticas de cifrado
- Reforzar procedimientos de resguardo físico y uso de dispositivos personales

## 📦 Evidencias a Recolectar
- Información del equipo perdido (modelo, serie, usuario)
- Detalles del incidente (lugar, fecha, testigos)
- Logs de acceso y sincronización a servicios institucionales
- Copias de denuncias realizadas (si corresponde)

## 📌 Indicadores de Compromiso (IOC)
- Accesos sospechosos desde nuevas IPs después del incidente
- Cambios de contraseñas sin autorización
- Intentos de recuperación de cuentas desde dispositivos desconocidos
- Acceso a servicios institucionales fuera del país

## 📅 Tiempo Estimado de Contención y Recuperación
**Contención**: 1–2 horas  
**Recuperación**: 24–48 horas (según disponibilidad de respaldo)

## ✅ Checklist de Validación Final
- [ ] Credenciales revocadas
- [ ] Equipo reportado como extraviado ante dirección y legal
- [ ] Datos sensibles evaluados y mitigados
- [ ] Informe generado y comunicado a áreas pertinentes