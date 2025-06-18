# Playbook de Respuesta a Incidente: R-08 - Acceso no autorizado a base de datos institucional

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

---

## 🛑 Clasificación del Incidente
---
> [!Importante:]
> "Clasificar siempre por efectos observables, no por causas u orígenes. Registrar todo contexto verificable."
---
*Área de Impacto*: Intrusión (Acceso no autorizado)  
*Impacto Operativo*: Alta  
*Tipo de Activo Afectado*: Base de datos institucional (académica, administrativa o financiera)

---

## 🧩 Descripción
Este incidente corresponde a un acceso no autorizado a una o más bases de datos institucionales, ya sea por explotación de vulnerabilidades, uso indebido de credenciales, o inyecciones maliciosas (por ejemplo, SQL). Se compromete la integridad y confidencialidad de la información almacenada, afectando datos personales, académicos y/o financieros.

---

## 👥 Roles y Responsabilidades
| Rol                       | Responsabilidad                                                                 |
|---------------------------|---------------------------------------------------------------------------------|
| CSIRT Universitario       | Lidera análisis forense y coordinación general                                 |
| DBA Institucional         | Identifica vectores, revisa logs y respalda estado actual                      |
| Dirección de Informática  | Supervisa acciones técnicas y escalamiento                                    |
| Seguridad de la Información | Evalúa impacto, establece nivel de exposición y plan de mitigación           |
| Área Jurídica y Comunicaciones | Apoya con comunicación interna y acciones legales    

---

## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

**NIST SP 800-53 Rev. 5:**
- `AC-2`: Gestión de Cuentas 
- `AC-3`: Cumplimiento de Acceso
- `AC-6`: Principio de Privilegio Mínimo
- `AC-16`: Atributos de Seguridad y Privacidad
- `AC-23`: Protección de Minería de Datos 
- `AU-12`: Generación de Registros de Auditoría
- `SI-4`: Monitoreo del Sistema
- `SC-28`: Protección de la Información en Reposo
- `IA-2`: Identificación y Autenticación

**Controles Críticos de Seguridad CIS:**
- `CIS Control 5`: Configuración Segura de Hardware/Software
- `CIS Control 6`: Gestión de Control de Acceso
- `CIS Control 8`: Gestión de Registros de Auditoría
- `CIS Control 16`: Monitoreo y Control de Cuentas
- `CIS Control 18`: Seguridad en el Software de Aplicaciones

**Herramientas Recomendadas:**
- Monitoreo de actividad en bases de datos: IBM Guardium, Imperva Database Security, Oracle Database Vault
- Firewalls para bases de datos: GreenSQL, McAfee Database Security
- Soluciones SIEM: Splunk, QRadar, Elastic Security
- Escáneres de vulnerabilidades: Nessus, Qualys, SQLMap
- Herramientas de cifrado: Transparent Data Encryption (TDE), Always Encrypted (SQL Server)
- Gestión de accesos: CyberArk, Thycotic Secret Server
- Análisis de logs: ELK Stack, Graylog, Alerta
- Frameworks ORM: Hibernate, Entity Framework, Django ORM

---

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

---

## 📦 Registros y Evidencias
- Logs de acceso a la base de datos (últimos 72h)
- Trazas de consultas inusuales o maliciosas
- Hashes y dumps sospechosos (si aplica)
- Registro de accesos con privilegios

Dumps: Copias o volcados de datos, ya sea de memoria, bases de datos o archivos, que pueden ser utilizados por atacantes para obtener información sensible

---

## 📌 Indicadores de Compromiso (IOC)
- Consultas inusuales desde IPs externas
- Exfiltración de tablas completas
- Uso de cuentas administrativas fuera de horario
- Cambios en estructuras o permisos no autorizados

---

## 📅 Tiempo Estimado de Contención y Recuperación
**Contención**: ≤ 2 horas  
**Recuperación**: 12–24 horas (según nivel de compromiso)

---

## ✅ Checklist de Validación Final
- [ ] Accesos maliciosos bloqueados
- [ ] Contraseñas y permisos revisados
- [ ] Auditoría final de actividad sospechosa
- [ ] Documentación completa del incidente generada

---

## Reporte ANCI
Plataforma: [https://portal.anci.gob.cl]

**Campos requeridos:**
- [ ] Código categoría principal + subcategoría
- [ ] Hora detección primer efecto
- [ ] Sistemas/servicios afectados
- [ ] Evidencia técnica (logs, capturas)
- [ ] Nivel de criticidad (Alto/Medio/Bajo)