# Playbook de Respuesta a Incidente: R-01 - Ransomware en Servidores

## 🛑 Clasificación del Incidente
- **Categoría ANCI**: Intrusión (Malware - Ransomware)
- **Nivel de Criticidad**: Alta
- **Tipo de Activo Afectado**: Servidor institucional (producción)

## 🧩 Descripción
El incidente consiste en la infección de uno o más servidores con ransomware, resultando en el cifrado de archivos críticos y posible extorsión por parte de los atacantes. La disponibilidad y confidencialidad de los servicios institucionales se ve comprometida.

## 👥 Roles y Responsabilidades
| Rol                            | Responsabilidad                                                                 |
|-------------------------------|----------------------------------------------------------------------------------|
| CSIRT Universitario           | Coordina la respuesta, análisis y contención                                    |
| Dirección de Informática      | Supervisa acciones y autoriza decisiones mayores                                |
| Encargado de Infraestructura  | Ejecuta contención técnica (aislamiento, backups)                              |
| Asesor Legal                  | Evalúa implicancias legales y contactos con terceros                           |
| Comunicaciones Institucionales| Administra la información oficial hacia la comunidad universitaria             |

## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

**NIST SP 800-61 Rev. 3:**
- `IR-4`: Manejo de Incidentes
- `IR-5`: Monitoreo de Incidentes
- `SI-4`: Herramientas de Monitoreo de Sistemas
- `CP-9`: Respaldo de Sistemas de Información
- `SC-7`: Protección de Fronteras

**Controles Críticos de Seguridad CIS:**
- `CIS Control 5`: Configuración Segura de Hardware/Software
- `CIS Control 8`: Defensas contra Malware (Protección de Endpoints)
- `CIS Control 10`: Capacidad de Recuperación de Datos (Verificación de Respaldos)
- `CIS Control 13`: Monitoreo y Defensa de Red (IDS/IPS)
- `CIS Control 16`: Monitoreo y Control de Cuentas

**Herramientas Recomendadas:**
- Herramientas de Segmentación de Red (VLANs, Firewalls)
- Soluciones de Detección y Respuesta en Endpoints (EDR)
- Utilidades de Verificación de Respaldos (Veeam, Commvault)
- Herramientas de Análisis Forense de Memoria (Volatility, Rekall)
- Plataformas de Escaneo de IOC (MISP, ThreatConnect)

## 🧭 Fases de Respuesta

### 1. Preparación
- Mantener respaldos verificados y segmentados (offline preferentemente)
- Tener una imagen base actualizada para restauración rápida de servidores
- Realizar simulacros de ransomware periódicamente
- Contar con herramientas forenses e informes previos de pruebas de restauración

### 2. Detección y Análisis
- Identificar señales de ransomware: extensiones inusuales, bloqueo del sistema, nota de rescate
- Correlacionar logs de acceso, cambios en archivos y picos de CPU o disco
- Confirmar el tipo de ransomware si es posible (mediante hash o firma)
- Activar plan de respuesta e informar al CSIRT

### 3. Contención
- Aislar el/los servidores afectados de la red inmediatamente
- Desactivar credenciales con privilegios usados recientemente
- Detener procesos sospechosos si es seguro hacerlo
- Registrar huellas del ataque (logs, RAM dump si aplica)

### 4. Erradicación
- Eliminar el malware mediante análisis forense
- Aplicar parches de seguridad si la vulnerabilidad es conocida
- Reinstalar sistema operativo si compromisos a nivel raíz son detectados

### 5. Recuperación
- Restaurar servicios a partir de respaldos no comprometidos
- Verificar la integridad de datos restaurados
- Monitorear durante al menos 72 horas la actividad del servidor

### 6. Lecciones Aprendidas
- Realizar una reunión post mortem con todos los involucrados
- Actualizar el Plan de Respuesta si se detectaron debilidades
- Documentar todo el flujo del incidente
- Generar un informe ejecutivo y técnico

## 📦 Evidencias a Recolectar
- Hash del ransomware (si disponible)
- Logs del servidor antes y después del ataque
- Copia de archivos cifrados (muestra, no completa)
- Captura de nota de rescate

## 📌 Indicadores de Compromiso (IOC)
- Extensiones de archivo inusuales
- Cambios en clave de registro (Windows)
- Cadenas comunes en notas de rescate (“Your files are encrypted…”)
- Comunicación con dominios C2 conocidos

## 📅 Tiempo Estimado de Contención y Recuperación
- Contención: ≤ 4 horas
- Recuperación: 24–48 horas (dependiendo del sistema)

## ✅ Checklist de Validación Final
- [ ] Aislamiento completado
- [ ] Respaldos utilizados verificados
- [ ] Comunicado institucional emitido
- [ ] Informe final generado y aprobado