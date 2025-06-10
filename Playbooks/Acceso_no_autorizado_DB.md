# Playbook de Respuesta a Incidente: R-08 - Acceso no autorizado a base de datos institucional

## 🛑 Clasificación del Incidente
**Categoría ANCI**: Intrusión (Acceso no autorizado)  
**Nivel de Criticidad**: Alta  
**Tipo de Activo Afectado**: Base de datos institucional (académica, administrativa o financiera)

## 🧩 Descripción
Este incidente corresponde a un acceso no autorizado a una o más bases de datos institucionales, ya sea por explotación de vulnerabilidades, uso indebido de credenciales, o inyecciones maliciosas (por ejemplo, SQL). Se compromete la integridad y confidencialidad de la información almacenada, afectando datos personales, académicos y/o financieros.

## 👥 Roles y Responsabilidades
| Rol                       | Responsabilidad                                                                 |
|---------------------------|---------------------------------------------------------------------------------|
| CSIRT Universitario       | Lidera análisis forense y coordinación general                                 |
| DBA Institucional         | Identifica vectores, revisa logs y respalda estado actual                      |
| Dirección de Informática  | Supervisa acciones técnicas y escalamiento                                    |
| Seguridad de la Información | Evalúa impacto, establece nivel de exposición y plan de mitigación           |
| Área Jurídica y Comunicaciones | Apoya con comunicación interna y acciones legales                      |

## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

**NIST SP 800-53 Rev. 5:**
- `AC-3`: Aplicación de controles de acceso
- `AC-6`: Principio de privilegio mínimo
- `AU-12`: Generación de registros de auditoría
- `SI-4`: Monitoreo del sistema
- `SC-28`: Protección de la información en reposo
- `IA-2`: Identificación y autenticación

**Controles Críticos de Seguridad CIS:**
- `CIS Control 5`: Configuración segura de hardware/software
- `CIS Control 6`: Gestión de control de acceso
- `CIS Control 8`: Gestión de registros de auditoría
- `CIS Control 16`: Monitoreo y control de cuentas
- `CIS Control 18`: Seguridad en el software de aplicaciones

**Herramientas Recomendadas:**
- Monitoreo de actividad en bases de datos: IBM Guardium, Imperva Database Security, Oracle Database Vault
- Firewalls para bases de datos: GreenSQL, McAfee Database Security
- Soluciones SIEM: Splunk, QRadar, Elastic Security
- Escáneres de vulnerabilidades: Nessus, Qualys, SQLMap
- Herramientas de cifrado: Transparent Data Encryption (TDE), Always Encrypted (SQL Server)
- Gestión de accesos: CyberArk, Thycotic Secret Server
- Análisis de logs: ELK Stack, Graylog, Alerta
- Frameworks ORM: Hibernate, Entity Framework, Django ORM

## 🧭 Fases de Respuesta

### 1. Preparación
- Uso obligatorio de contraseñas robustas y autenticación multifactor en accesos administrativos
- Aplicación de políticas de privilegios mínimos en bases de datos
- Registro centralizado de logs y auditoría activa

### 2. Detección y Análisis
- Monitorear accesos inusuales o fuera de horario
- Analizar logs de eventos y sentencias SQL sospechosas
- Verificar si se han extraído, modificado o eliminado datos
- Activar plan de respuesta y clasificar criticidad

### 3. Contención
- Suspender accesos de usuarios comprometidos
- Aislar la base de datos si se detecta actividad continua
- Aplicar reglas de firewall o WAF si se detectan vectores como SQLi

### 4. Erradicación
- Corregir vulnerabilidades explotadas (por ejemplo, filtrado de entradas)
- Cambiar contraseñas de todos los accesos administrativos
- Reestablecer políticas de seguridad reforzada

### 5. Recuperación
- Restaurar datos desde backups si se comprometió integridad
- Verificar integridad de registros y permisos tras la recuperación
- Reanudar servicio tras validaciones con DBA y CSIRT

### 6. Lecciones Aprendidas
- Analizar causas raíz del acceso indebido
- Reforzar políticas de desarrollo seguro si fue ataque a través de app web
- Incorporar reglas preventivas en IDS/IPS y SIEM

## 📦 Evidencias a Recolectar
- Logs de acceso a la base de datos (últimos 72h)
- Trazas de consultas inusuales o maliciosas
- Hashes y dumps sospechosos (si aplica)
- Registro de accesos con privilegios

## 📌 Indicadores de Compromiso (IOC)
- Consultas inusuales desde IPs externas
- Exfiltración de tablas completas
- Uso de cuentas administrativas fuera de horario
- Cambios en estructuras o permisos no autorizados

## 📅 Tiempo Estimado de Contención y Recuperación
**Contención**: ≤ 2 horas  
**Recuperación**: 12–24 horas (según nivel de compromiso)

## ✅ Checklist de Validación Final
- [ ] Accesos maliciosos bloqueados
- [ ] Contraseñas y permisos revisados
- [ ] Auditoría final de actividad sospechosa
- [ ] Documentación completa del incidente generada