# Playbook de Respuesta a Incidente: R-03 - Phishing a usuarios ULagos

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
 *Área de impacto*: Uso legitimo de Recursos 
 *Impacto Operativo*: Media-Alta  
 *Tipo de Activo Afectado*: Cuentas de correo institucional y plataformas asociadas
---

## 🧩 Descripción
   Este incidente se refiere a la recepción de correos electrónicos fraudulentos por parte de usuarios institucionales, simulando ser una entidad confiable para obtener credenciales, ejecutar malware o redirigir a sitios falsos. Puede derivar en accesos no autorizados, filtración de información o infección de sistemas.

## 👥 Roles y Responsabilidades
   | Rol                            | Responsabilidad                                                                 |
   |--------------------------------|---------------------------------------------------------------------------------|
   | CSIRT Universitario            | Coordina acciones de análisis, contención y campañas de concientización         |
   | Encargado de Correo Institucional | Identifica correos maliciosos y bloquea remitentes / dominios involucrados    |
   | Dirección de Informática       | Toma decisiones estratégicas y autoriza bloqueos masivos                        |
   | Encargado de Seguridad         | Analiza patrones de ataques y actualiza sistemas de detección                   |
   | Comunicaciones Institucionales | Redacta alertas preventivas y mensajes oficiales a la comunidad universitaria   |

## 🛠️ Herramientas y Recursos (NIST/CIS Controls)
   **NIST SP 800-53 Rev. 5:**
   - `AT-2`: Capacitación en Concientización de Seguridad
   - `SI-4`: Monitoreo de Sistemas
   - `SC-7`: Protección de Fronteras (Pasarelas de Correo Electrónico)
   - `IR-4`: Manejo de Incidentes
   - `AC-17`: Protección de Acceso Remoto

   **Controles Críticos de Seguridad CIS:**
   - `Control CIS 9`: Protección de Correo Electrónico y Navegadores Web
   - `Control CIS 14`: Concientización sobre Seguridad y Capacitación en Habilidades
   - `Control CIS 5`: Gestión de Cuentas
   - `Control CIS 10`: Defensas contra Malware
   - `Control CIS 8`: Gestión de Registros de Auditoría
   - `Control CIS 13`: Monitoreo y Defensa de la Red

   **Herramientas Recomendadas:**
   - **Pasarelas de Seguridad de Correo** (Email Security Gateways): Proofpoint, Mimecast, Cisco ESA
   - **Plataformas de Simulación de Phishing** (Phishing Simulation Platforms): KnowBe4, Proofpoint Security Awareness
   - **Fuentes de Inteligencia de Amenazas** (Threat Intelligence Sources): AlienVault OTX, PhishTank
   - **Herramientas de Análisis de URLs** (URL Analysis Tools): VirusTotal, URLScan.io
   - **Detección y Respuesta en Endpoints (EDR)** (Endpoint Detection and Response): CrowdStrike, SentinelOne
   - **Soluciones SIEM** (Security Information and Event Management): Splunk, QRadar, Elastic Security

## 🧭 Fases de Respuesta

   ### 1. Preparación
   - Implementar políticas de seguridad para correos electrónicos (SPF, DKIM, DMARC)
   - Capacitar regularmente al personal sobre cómo identificar correos sospechosos
   - Contar con procedimientos de reporte rápido de phishing
   - Mantener filtros antispam y antiphishing actualizados

   ### 2. Detección y Análisis
   - Recepción de reportes de usuarios o detección por sistemas antispam
   - Analizar encabezados del correo y enlaces contenidos
   - Confirmar si se produjo ingreso de credenciales o descarga de malware
   - Identificar patrones comunes entre múltiples reportes

   ### 3. Contención
   - Bloquear direcciones IP, dominios o URLs maliciosas en el firewall y filtros de correo
   - Alertar inmediatamente a los usuarios sobre el intento de phishing
   - Monitorear accesos sospechosos derivados del incidente

   ### 4. Erradicación
   - Eliminar correos maliciosos entregados en bandejas de entrada (si es técnicamente viable)
   - Cambiar credenciales a cuentas posiblemente comprometidas
   - Eliminar reglas automáticas o redirecciones maliciosas en las cuentas afectadas

   ### 5. Recuperación
   - Restablecer acceso seguro a cuentas afectadas
   - Validar que no existan conexiones activas desde ubicaciones inusuales
   - Ejecutar análisis de malware en los equipos implicados

   ### 6. Lecciones Aprendidas
   - Revisión de la eficacia de los filtros de correo
   - Actualización de campañas de concientización en base al caso real
   - Registro y documentación del incidente y las medidas tomadas
   - Evaluación de mejoras técnicas en detección y prevención

---

## 📦 Evidencias a Recolectar
   - Copia del correo original en formato .eml (con encabezados)
   - URLs maliciosas utilizadas
   - Logs de accesos posteriores al clic en enlaces sospechosos
   - Reportes de usuarios afectados o alertas del sistema

---

## 📌 Indicadores de Compromiso (IOC)
   - Cadenas de texto comunes en correos (e.g., "Su cuenta ha sido bloqueada", "Acceda aquí")
   - Remitentes falsos o similares a cuentas institucionales
   - URLs acortadas o con dominios ajenos a ULagos
   - Reportes múltiples en un corto período

---

## 📅 Tiempo Estimado de Contención y Recuperación
   **Contención**: < 5 min con automatización avanzada.
   **Recuperación**: 2–4 horas como rango aceptable para recuperación tras phishing Un tiempo aceptado en SOC es de 2 a 4 horas para incidentes críticos, aunque puede variar según severidad (1 h crítica, 2 h alta, 4 h media, 8 h baja) según (https://www.prophetsecurity.ai/blog/soc-metrics-that-matter-mttr-mtti-false-negatives-and-more)

---

## ✅ Checklist de Validación Final
   - [ ] Correos fraudulentos bloqueados o eliminados
   - [ ] Cuentas comprometidas aseguradas
   - [ ] Usuarios informados y capacitados
   - [ ] Informe final documentado
   - [ ] IOC integrados al sistema de detección

---

## Reporte ANCI
   Plataforma: [https://portal.anci.gob.cl]

   **Campos requeridos:**
   - [ ] Código categoría principal + subcategoría
   - [ ] Hora detección primer efecto
   - [ ] Sistemas/servicios afectados
   - [ ] Evidencia técnica (logs, capturas)
   - [ ] Nivel de criticidad (Alto/Medio/Bajo)