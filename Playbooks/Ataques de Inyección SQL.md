# Playbook de Respuesta a Incidente: R-27 - Ataques de Inyección SQL

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


## 🛑 Clasificación del Incidente según ANCI
---
   > [!Importante:]
   > "Clasificar siempre por efectos observables, no por causas u orígenes. Registrar todo contexto verificable."
   ---
   *Área de impacto*: Uso legítimo de recursos  
   *Impacto Operativo*: Alto (Exfiltración datos críticos)  
   *Tipo de Activo Afectado*: Bases de datos, aplicaciones web

---

## 🧩 Descripción
   Un ataque de inyección SQL se produce cuando un atacante inserta código malicioso en una consulta SQL a través de formularios web, URLs o cabeceras HTTP. Este tipo de ataque puede permitir la extracción, modificación o eliminación de datos, así como el acceso no autorizado a sistemas críticos.

---

## 👥 Roles y Responsabilidades

   | Rol                     | Responsabilidad                                                                                                                                |
   |-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
   | CSIRT Universitario     | Coordina el análisis, contención y comunica hallazgos técnicos; verifica la integridad de datos, revisa logs y aplica restauraciones si es necesario. |
   | Dirección de Informática| Supervisa acciones estratégicas; valida decisiones críticas relacionadas con la continuidad operativa.                                         |
   | Asesor Legal            | Evalúa implicancias legales y regulatorias; verifica cumplimiento de normativas sobre protección de datos personales.                          |


---

## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

   **NIST SP 800-53 Rev. 5**

   - `SI-3`: Protección contra Código Malicioso *(Malicious Code Protection)*
   - `SI-4`: Monitoreo del Sistema *(System Monitoring)*
   - `SI-11`: Manejo de Errores *(Error Handling)*
   - `AC-3`: Cumplimiento del Acceso *(Access Enforcement)*
   - `AC-6`: Mínimo Privilegio *(Least Privilege)*
   - `AU-2`: Registro de Eventos *(Event Logging)*
   - `SI-10`: Validación de Entradas de Información *(Information Input Validation)*
   - `SI-15`: Filtrado de Salida de Información *(Information Output Filtering)*

   **Controles Críticos de Seguridad CIS:**
   - `CIS Control 16`: Seguridad del software de aplicaciones

   **Herramientas Recomendadas:**
   - Cortafuegos de aplicaciones web (WAF): ModSecurity, Cloudflare, AWS WAF
   - Herramientas de análisis estático/dinámico (SAST/DAST): OWASP ZAP, Burp Suite, Checkmarx
   - Monitoreo de actividad de bases de datos: IBM Guardium, Imperva Database Security
   - Escáneres de vulnerabilidades: Nessus, Qualys, OpenVAS
   - Frameworks ORM: Hibernate (Java), Entity Framework (.NET), Django ORM (Python)
   - Análisis de logs: ELK Stack, Splunk, Graylog
   - Librerías de codificación segura: OWASP ESAPI, Microsoft AntiXSS

---

## 🧭 Fases de Respuesta

1. **Preparación**
   - Aplicar validación de entradas y uso de consultas preparadas (prepared statements)
   - Realizar revisiones periódicas de seguridad en código (SAST/DAST)
   - Implementar WAF con reglas anti-inyección
   - Capacitar a los desarrolladores sobre desarrollo seguro

      SAST/DAST: Dos metodologías de pruebas de seguridad de aplicaciones.
      SAST(Static Application Security Testing): Analiza el código fuente de una aplicación en busca de vulnerabilidades
      DAST(Dynamic Application Security Testing): valúa la aplicación en tiempo de ejecución, simulando ataques externos. 
      WAP: Es un dispositivo o servicio que protege las aplicaciones web filtrando y monitoreando el tráfico HTTP y HTTPS.

2. **Detección y Análisis**
   - Identificar errores inusuales en logs de aplicación o base de datos
   - Analizar solicitudes HTTP sospechosas con caracteres como ', --, OR 1=1
   - Verificar consultas SQL fallidas o ejecutadas fuera de patrón
   - Detectar comportamiento anómalo en la base de datos (accesos masivos, exportaciones)

3. **Contención**
   - Bloquear inmediatamente el punto de entrada afectado (formulario o URL)
   - Aplicar reglas de emergencia en el WAF para filtrar patrones conocidos
   - Deshabilitar temporalmente la aplicación si el ataque está activo y crítico

4. **Erradicación**
   - Corregir el código vulnerable (usar ORM o consultas parametrizadas)
   - Revisar y limpiar accesos no autorizados o modificaciones realizadas
   - Actualizar librerías y frameworks desactualizados

5. **Recuperación**
   - Restaurar datos a partir de respaldos si hubo alteraciones
   - Validar funcionamiento seguro de la aplicación
   - Reintegrar a producción con monitoreo activo

6. **Lecciones Aprendidas**
   - Documentar el vector de ataque y medidas correctivas aplicadas
   - Evaluar la cobertura de pruebas de seguridad en el ciclo de desarrollo
   - Agendar una auditoría de seguridad en toda la plataforma afectada

---

## 📦 Evidencias a Recolectar
   - Logs de acceso web y SQL (antes y después del incidente)
   - Captura de payload() utilizado (si es posible)
   - Código fuente afectado y revisión de commit previo
   - Listado de tablas y registros modificados o consultados

      Payload: parte de un paquete de datos o código malicioso que realiza la acción dañina en un sistema, como borrar archivos, robar información o tomar el control del sistema

---

## 📌 Indicadores de Compromiso (IOC)
   - Uso anómalo de caracteres como ', ", --, ;, OR, UNION SELECT
   - Consultas a tablas administrativas (users, admin, information_schema)
   - Cambios en privilegios de usuarios de base de datos
   - Accesos desde IPs no usuales fuera de horario

---

## 📅 Tiempo Estimado de Contención y Recuperación

   Según informes como el publicado por *Framework IT* ("Response & Resolution Times from a Managed Services Provider"), los proveedores de servicios gestionados (MSP) suelen establecer:

   - **Tiempo de respuesta inicial**: ≤ 1 hora
   - **Tiempo de resolución**: entre **8 y 24 horas**, dependiendo de la complejidad del incidente

   Según *ANCI* (Articulo 9 de la ley Marco de Cibersgurida) los tiempos para Notificar son:
   - **Reporte inicial**: ≤ 3 horas
   - **Informe Detallado**: ≤ 72 horas  

   Estos parámetros, aunque diseñados para problemas generales de TI, pueden ser aplicables a incidentes de seguridad **si la detección es temprana y se cuenta con los mecanismos adecuados de monitoreo y respuesta**.

   > *Nota:* Estos tiempos deben ser adaptados según el nivel de criticidad del incidente, la madurez del equipo de respuesta y los SLA(Service Level Agreement o Acuerdo de Nivel de Servicio) internos de la Universidad.

---

## ✅ Checklist técnico
   - [ ] Notificar a Delegado de Ciberseguridad (≤1h)
   - [ ] Iniciar reporte en portal.anci.gob.cl
   - [ ] Verificar integridad de backups
   - [ ] Validar parches en entornos DEV/TEST
   - [ ] Validar existencia de WAF con reglas actualizadas
   - [ ] Revisar logs de aplicaciones web
   - [ ] Escanear con SQLMap para confirmar vulnerabilidad
   - [ ] Rotar credenciales de base de datos
   - [ ] Verificar integridad de backups
   - [ ] Actualizar librerías de acceso a BD

---

## Reporte ANCI
   Plataforma: [https://portal.anci.gob.cl]

   **Campos requeridos:**
   - [ ] Código categoría principal + subcategoría
   - [ ] Hora detección primer efecto
   - [ ] Sistemas/servicios afectados
   - [ ] Evidencia técnica (logs, capturas)
   - [ ] Nivel de criticidad (Alto/Medio/Bajo)