# 🛡️ Playbook 03: Explotación de Vulnerabilidad Zero-Day

**Código:** PB-ULA-005  
**Última actualización:** 16/Ago/2025  
**Responsable de revisión:**  
**Tipo de Incidente:** Confidencialidad / Integridad – Explotación de una vulnerabilidad desconocida (Zero-Day)  
**Versión:** 1.0

---

## 1️⃣ Preparación
![Preparación](./Workflows/01-preparacion.png)

**Objetivo:** Fortalecer la capacidad institucional para detectar, contener y responder a ataques que aprovechan vulnerabilidades no conocidas públicamente.

### Acciones:

- Mantener actualizadas las plataformas de threat intelligence (ej: CISA KEV, MISP, NIST NVD, ZDI).
- Establecer acuerdos con proveedores de tecnología para recibir alertas tempranas de vulnerabilidades críticas.
- Documentar la infraestructura crítica y sistemas expuestos públicamente.
- Implementar políticas de hardening y control de cambios con priorización de sistemas críticos.
- Establecer canales seguros y rápidos de comunicación entre área de soporte, SOC y CSIRT Nacional.
- Realizar simulacros de ataques tipo zero-day con análisis de tiempos de respuesta.

---

## 2️⃣ Detección
![Detección y análisis](./Workflows/02-deteccion-analisis.png)

**Objetivo:** Identificar la explotación activa de una vulnerabilidad desconocida (zero-day) a través de síntomas indirectos, anomalías y fuentes externas.

### Acciones:

- Monitorear plataformas OSINT, CVE tempranas, y foros de investigadores de seguridad.
- Revisar eventos anómalos en EDR/XDR (ej: ejecución de procesos no firmados, DLLs inyectadas, técnicas Living off the Land).
- Analizar tráfico de red en busca de patrones anormales (DNS tunneling, conexiones persistentes a IPs desconocidas).
- Revisar logs del sistema operativo, autenticaciones inusuales y eventos de privilegios elevados.
- Correlacionar eventos con reglas YARA, Sigma, MITRE ATT&CK TTPs.
- Notificar inmediatamente a Dirección de informática y CSIRT institucional para evaluar el impacto.

---

## 3️⃣ Contención
![Contención](./Workflows/03-contencion.png)

**Objetivo:** Prevenir la expansión lateral del atacante y proteger sistemas aún no comprometidos.

### Acciones:

1. Aislar máquinas afectadas y desconectarlas de la red interna y externa.
2. Bloquear en firewall las IPs, dominios y rutas relacionados al exploit detectado.
3. Suspender sesiones activas sospechosas y revocar credenciales comprometidas.
4. Activar reglas de detección reforzada (EDR, SIEM) en toda la infraestructura.
5. Implementar segmentación adicional temporal (microsegmentación si es posible).
6. Aplicar reglas de detección compartidas por CERT, CISA u otros CSIRT confiables.

---

## 4️⃣ Erradicación
![Erradicación](./Workflows/04-erradicacion.png)

**Objetivo:** Eliminar cualquier rastro de la vulnerabilidad explotada y cerrar el acceso no autorizado.

### Acciones:

- **Identificar:** Determinar la variante del exploit utilizado. Validar con feeds de threat intelligence si existe patch o workaround oficial.
- **Probar:** Evaluar en entorno controlado la solución (hotfix, actualización, mitigación temporal como desactivar servicios).
- **Desplegar:** Aplicar workaround o actualización en todos los sistemas afectados y relacionados.
- Realizar escaneo forense completo en las máquinas comprometidas (procesos, persistencias, rootkits).

> *Nota:* Es común que el atacante o malware persista incluso después de mitigar la vulnerabilidad. Verificar presencia de backdoors, tareas programadas maliciosas o cuentas ocultas.

---

## 5️⃣ Recuperación
![Recuperación](./Workflows/05-recuperacion.png)

**Objetivo:** Restaurar el funcionamiento de los sistemas comprometidos sin reintroducir vectores de riesgo.

### Acciones:

1. Reinstalar o restaurar sistemas afectados desde respaldos verificados (anteriores a la explotación).
2. Reincorporar los sistemas a la red de forma controlada y por etapas.
3. Monitorear logs, tráfico y comportamiento por al menos 7 días.
4. Validar con pentest o escaneo externo que la vulnerabilidad está corregida o contenida.
5. Documentar la recuperación y obtener validación del CISO o responsable de seguridad.

---

## 6️⃣ Lecciones aprendidas
![Lecciones Aprendidas](./Workflows/06-lecciones-aprendidas.png)

**Objetivo:** Fortalecer la postura de seguridad mediante análisis post-incidente.

### Informe:

- Causa raíz: tipo de zero-day y vía de entrada (exploit remoto, local, correo, etc.).
- Línea de tiempo: descubrimiento, contención, erradicación, recuperación.
- Acciones implementadas y resultados.
- Efectividad de los controles activos.
- Recomendaciones para prevenir incidentes similares.

### Retrospectiva:

- Fortalecer colaboración con proveedores para recibir alertas tempranas.
- Evaluar necesidad de soluciones de sandboxing y análisis de comportamiento.
- Establecer thresholds más bajos de alerta ante anomalías.
- Mejorar visibilidad en activos no monitoreados (Shadow IT).
- Revisar cobertura y madurez del programa de gestión de vulnerabilidades.

---

## 📄 Referencia

- **Fuente:** MITRE ATT&CK, CISA, Mandiant 2025 Threat Landscape Report  
- **Web:** [https://www.cisa.gov/known-exploited-vulnerabilities-catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)  
- **Email:** csirt@ulagos.cl
