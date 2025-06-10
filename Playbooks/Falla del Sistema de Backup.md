# Playbook de Respuesta a Incidente: R-05 - Falla del Sistema de Backup

## 🛑 Clasificación del Incidente
**Categoría ANCI**: Disponibilidad (Falla de servicio crítico)  
**Nivel de Criticidad**: Alta  
**Tipo de Activo Afectado**: Sistema de respaldo de datos (servidores de backup, software de respaldo)

## 🧩 Descripción
Este incidente se refiere a la imposibilidad de ejecutar, recuperar o verificar respaldos programados debido a fallos de hardware, software o configuración. Afecta directamente la capacidad de recuperación ante incidentes como ransomware, pérdidas de datos o interrupciones del sistema.

## 👥 Roles y Responsabilidades
| Rol                     | Responsabilidad                                                                 |
|-------------------------|---------------------------------------------------------------------------------|
| CSIRT Universitario     | Evalúa impacto, coordina con infraestructura y reporta estado                  |
| Encargado de Backup     | Ejecuta diagnóstico, recuperación o configuración del sistema de respaldo      |
| Dirección de Informática| Toma decisiones sobre continuidad de operaciones y escalamiento               |
| Encargado de Infraestructura | Verifica conectividad, almacenamiento y salud del hardware               |
| Área de Sistemas        | Verifica integración y accesos desde otros sistemas dependientes              |

## 🛠️ Herramientas y Recursos (NIST/CIS Controls)
**NIST SP 800-53 Rev. 5:**
- `CP-9`: Respaldo del sistema de información  
- `CP-10`: Recuperación y reconstrucción del sistema de información  
- `SI-7`: Integridad de software, firmware e información  
- `MA-6`: Mantenimiento oportuno  
- `AU-4`: Capacidad de almacenamiento de auditoría

**CIS Critical Security Controls:**
- `CIS Control 10`: Capacidad de recuperación de datos  
- `CIS Control 11`: Configuración segura para dispositivos de red  
- `CIS Control 12`: Defensa perimetral  
- `CIS Control 16`: Monitoreo y control de cuentas  
- `CIS Control 18`: Seguridad del software de aplicaciones

**Herramientas Recomendadas:**
- **Herramientas de Verificación de Backups**:  
    - *Veeam SureBackup* (Verificación automatizada de respaldos)  
    - *Commvault Auto Image Replication* (Replicación y validación automática de imágenes de respaldo)

- **Soluciones de Monitoreo**:  
    - *Nagios* (Monitoreo de infraestructura y servicios)  
    - *Zabbix* (Supervisión de sistemas y aplicaciones)  
    - *SolarWinds Backup Monitor* (Monitoreo específico de respaldos)

- **Gestión de Configuración**:  
    - *Ansible* (Automatización y gestión de configuraciones)  
    - *Puppet* (Administración centralizada de configuraciones)  
    - *Chef* (Automatización de infraestructura)

- **Gestión de Logs**:  
    - *ELK Stack* (Elasticsearch, Logstash, Kibana para análisis de logs)  
    - *Splunk* (Recolección y análisis de registros)  
    - *Graylog* (Gestión centralizada de logs)

- **Diagnóstico de Hardware**:  
    - *Dell OpenManage* (Supervisión y diagnóstico de hardware Dell)  
    - *HPE OneView* (Gestión y monitoreo de hardware HPE)  
    - *SMART Monitoring Tools* (Monitoreo del estado de discos duros)

- **Plataformas de Pruebas de Recuperación**:  
    - *Virtual Test Labs* (Laboratorios virtuales para pruebas de restauración)  
    - *Sandbox Environments* (Entornos aislados para pruebas de recuperación)

## 🧭 Fases de Respuesta

### 1. Preparación
- Documentar políticas de respaldo (frecuencia, retención, medios utilizados)
- Validar integridad de respaldos mediante pruebas periódicas
- Contar con respaldos offline o alternativos ante fallos del sistema principal

### 2. Detección y Análisis
- Identificar errores de respaldo (fallos en logs, alertas de verificación fallida)
- Analizar si la falla es total (todos los respaldos) o parcial (algunos nodos o fechas)
- Determinar última copia funcional disponible

### 3. Contención
- Suspender temporalmente nuevos respaldos para evitar corrupción adicional
- Aislar componente afectado (unidad de almacenamiento, servidor, aplicación)
- Registrar errores y mensajes del sistema para análisis

### 4. Erradicación
- Corregir errores de configuración o scripts automáticos si aplica
- Sustituir hardware o reinstalar software de respaldo si se detecta falla crítica
- Verificar permisos y accesos de usuarios/servicios que interactúan con el sistema

### 5. Recuperación
- Reanudar copias de respaldo programadas
- Verificar consistencia e integridad del nuevo respaldo
- Restaurar una muestra de archivos para comprobar funcionalidad

### 6. Lecciones Aprendidas
- Registrar causas raíz y debilidades encontradas
- Considerar implementación de backup redundante o multisitio
- Mejorar monitoreo y alertas automáticas del sistema
- Ajustar procedimientos de verificación post-respaldo

## 📦 Evidencias a Recolectar
- Logs del software de backup
- Alertas del sistema o software de monitoreo
- Capturas de errores o fallos
- Registro de tareas programadas fallidas

## 📌 Indicadores de Compromiso (IOC)
- Fallos recurrentes en la verificación de respaldos
- Tiempos inusualmente largos en ejecución de copias
- Archivos de respaldo corruptos o incompletos
- Cambios recientes en configuración o permisos del sistema

## 📅 Tiempo Estimado de Contención y Recuperación
**Contención**: ≤ 4 horas  
**Recuperación**: 24–48 horas (depende del nivel de fallo y tipo de backup)

## ✅ Checklist de Validación Final
- [ ] Diagnóstico técnico completado
- [ ] Respaldo funcional y verificado
- [ ] Prueba de restauración realizada
- [ ] Registro del incidente documentado
- [ ] Plan de mejora actualizado