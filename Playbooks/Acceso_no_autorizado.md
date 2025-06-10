# Playbook de Respuesta a Incidente: R-02 - Acceso no autorizado a plataformas universitarias

## 🛑 Clasificación del Incidente
**Categoría ANCI**: Intrusión (Acceso no autorizado)  
**Nivel de Criticidad**: Alta  
**Tipo de Activo Afectado**: Plataformas institucionales (Intranet, Sistemas Académicos, Correo Electrónico, etc.)

## 🧩 Descripción
Este incidente ocurre cuando un tercero no autorizado accede a plataformas institucionales mediante credenciales robadas, suplantación de identidad o explotación de vulnerabilidades. Puede afectar la integridad, confidencialidad y disponibilidad de la información contenida en los sistemas.

## 👥 Roles y Responsabilidades
| Rol                        | Responsabilidad                                                                 |
|----------------------------|---------------------------------------------------------------------------------|
| CSIRT Universitario        | Coordinación general de la respuesta y análisis forense                         |
| Encargado de Seguridad     | Detección, monitoreo de actividad anómala y contención                          |
| Dirección de Informática   | Toma de decisiones estratégicas y coordinación con otras áreas                 |
| Encargado de Plataforma    | Revisión de logs, verificación de integridad del sistema                       |
| Asesor Legal               | Evaluación de consecuencias legales, reportes externos si corresponde          |
| Comunicaciones Institucionales | Comunicación oficial hacia usuarios afectados y comunidad universitaria     |

## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

**NIST SP 800-53 Rev. 5:**
- `AC-2`: Gestión de cuentas
- `AC-3`: Aplicación de controles de acceso
- `AC-6`: Mínimo privilegio
- `IA-2`: Identificación y autenticación
- `SI-4`: Monitoreo del sistema
- `AU-6`: Revisión, análisis y reporte de registros de auditoría

**Controles Críticos de Seguridad CIS:**
- `CIS Control 4`: Configuración segura de activos empresariales y software
- `CIS Control 5`: Gestión de cuentas
- `CIS Control 6`: Gestión de control de acceso
- `CIS Control 8`: Gestión de registros de auditoría
- `CIS Control 16`: Monitoreo y control de cuentas

**Herramientas Recomendadas:**
- Gestión de Identidad y Accesos (IAM): Okta, Azure AD, Ping Identity
- Autenticación Multifactor (MFA): Duo Security, Google Authenticator, YubiKey
- Gestión de Información y Eventos de Seguridad (SIEM): Splunk, QRadar, Elastic Security
- Detección y Respuesta en Endpoints (EDR): CrowdStrike, SentinelOne, Microsoft Defender
- Escáneres de Vulnerabilidades: Nessus, Qualys, OpenVAS
- Gestión de Registros: Graylog, LogRhythm, syslog-ng
- Gestión de Accesos Privilegiados (PAM): CyberArk, BeyondTrust, Thycotic

## 🧭 Fases de Respuesta

### 1. Preparación
- Implementar autenticación multifactor (MFA) en accesos críticos
- Mantener políticas de contraseñas robustas y vigentes
- Definir perfiles de acceso y aplicar el principio de mínimo privilegio
- Realizar campañas internas sobre buenas prácticas de seguridad

### 2. Detección y Análisis
- Monitorear inicios de sesión desde ubicaciones inusuales o múltiples intentos fallidos
- Revisar logs del sistema y de la aplicación para identificar accesos no autorizados
- Confirmar si hubo modificación, exfiltración o eliminación de información
- Activar protocolo de respuesta y notificar al CSIRT

### 3. Contención
- Forzar cierre de sesión en todas las cuentas afectadas
- Bloquear temporalmente las cuentas comprometidas o sospechosas
- Cambiar contraseñas de administradores y usuarios de alto privilegio
- Restringir acceso a los sistemas afectados

### 4. Erradicación
- Identificar y corregir la vulnerabilidad explotada (e.g. reconfiguración, parcheo)
- Verificar integridad de los sistemas afectados mediante auditoría técnica
- Eliminar cuentas maliciosas o accesos persistentes

### 5. Recuperación
- Restaurar servicios afectados asegurando su integridad
- Notificar a los usuarios sobre el restablecimiento y las medidas tomadas
- Monitorear accesos y actividad posterior durante al menos 72 horas

### 6. Lecciones Aprendidas
- Reunión con equipos involucrados para análisis retrospectivo
- Documentar el incidente, medidas adoptadas y lecciones
- Actualizar protocolos y capacitar a los equipos
- Evaluar incorporación de nuevas medidas tecnológicas o normativas

## 📦 Evidencias a Recolectar
- Logs de acceso antes y después del incidente
- Registro de direcciones IP y dispositivos conectados
- Capturas de accesos sospechosos o anómalos
- Reportes del SIEM o herramientas de monitoreo

## 📌 Indicadores de Compromiso (IOC)
- Inicios de sesión desde países no habituales
- Cambios en privilegios de cuentas sin autorización previa
- Picos inusuales en transferencia de datos
- Nuevas reglas de firewall o configuraciones no autorizadas

## 📅 Tiempo Estimado de Contención y Recuperación
**Contención**: ≤ 3 horas  
**Recuperación**: 12–24 horas (dependiendo del alcance y daño)

## ✅ Checklist de Validación Final
- [ ] Cuentas comprometidas bloqueadas y credenciales actualizadas
- [ ] Logs revisados y almacenados para análisis forense
- [ ] Servicios restaurados y verificados
- [ ] Informe de incidente generado y entregado
- [ ] Comunicación oficial enviada a usuarios involucrados