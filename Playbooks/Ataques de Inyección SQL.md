# Playbook de Respuesta a Incidente: R-27 - Ataques de Inyección SQL

🛑 **Clasificación del Incidente**  
- **Categoría ANCI:** Intrusión (Inyección de Código – SQL Injection)  
- **Nivel de Criticidad:** Alta  
- **Tipo de Activo Afectado:** Aplicaciones web, bases de datos y servidores backend

---

🧩 **Descripción**  
Un ataque de inyección SQL se produce cuando un atacante inserta código malicioso en una consulta SQL a través de formularios web, URLs o cabeceras HTTP. Este tipo de ataque puede permitir la extracción, modificación o eliminación de datos, así como el acceso no autorizado a sistemas críticos.

---

👥 **Roles y Responsabilidades**

| Rol                     | Responsabilidad                                                                 |
|-------------------------|--------------------------------------------------------------------------------|
| CSIRT Universitario     | Coordina el análisis, contención y comunica hallazgos técnicos                 |
| Encargado de Desarrollo Web | Identifica el punto vulnerable y corrige el código fuente                  |
| DBA (Administrador de BD)   | Verifica la integridad de datos, revisa logs y aplica restauraciones si necesario |
| Dirección de Informática    | Supervisa acciones estratégicas y valida decisiones mayores                |
| Asesor Legal                | Evalúa implicancias en protección de datos personales y cumplimiento normativo |

---

🧭 **Fases de Respuesta**

1. **Preparación**
   - Aplicar validación de entradas y uso de consultas preparadas (prepared statements).
   - Realizar revisiones periódicas de seguridad en código (SAST/DAST).
   - Implementar WAF con reglas anti-inyección.
   - Capacitar a los desarrolladores sobre desarrollo seguro (OWASP Top 10).

2. **Detección y Análisis**
   - Identificar errores inusuales en logs de aplicación o base de datos.
   - Analizar solicitudes HTTP sospechosas con caracteres como ', --, OR 1=1.
   - Verificar consultas SQL fallidas o ejecutadas fuera de patrón.
   - Detectar comportamiento anómalo en la base de datos (accesos masivos, exportaciones).

3. **Contención**
   - Bloquear inmediatamente el punto de entrada afectado (formulario o URL).
   - Aplicar reglas de emergencia en el WAF para filtrar patrones conocidos.
   - Deshabilitar temporalmente la aplicación si el ataque está activo y crítico.

4. **Erradicación**
   - Corregir el código vulnerable (usar ORM o consultas parametrizadas).
   - Revisar y limpiar accesos no autorizados o modificaciones realizadas.
   - Actualizar librerías y frameworks desactualizados.

5. **Recuperación**
   - Restaurar datos a partir de respaldos si hubo alteraciones.
   - Validar funcionamiento seguro de la aplicación.
   - Reintegrar a producción con monitoreo activo.

6. **Lecciones Aprendidas**
   - Documentar el vector de ataque y medidas correctivas aplicadas.
   - Evaluar la cobertura de pruebas de seguridad en el ciclo de desarrollo.
   - Agendar una auditoría de seguridad en toda la plataforma afectada.

---

📦 **Evidencias a Recolectar**
- Logs de acceso web y SQL (antes y después del incidente).
- Captura de payload utilizado (si es posible).
- Código fuente afectado y revisión de commit previo.
- Listado de tablas y registros modificados o consultados.

---

📌 **Indicadores de Compromiso (IOC)**
- Uso anómalo de caracteres como ', ", --, ;, OR, UNION SELECT.
- Consultas a tablas administrativas (users, admin, information_schema).
- Cambios en privilegios de usuarios de base de datos.
- Accesos desde IPs no usuales fuera de horario.

---

📅 **Tiempo Estimado de Contención y Recuperación**
- **Contención:** 1–2 horas
- **Recuperación:** 4–12 horas (dependiendo del daño a datos y código)

---

✅ **Checklist de Validación Final**
- [ ] Punto de entrada corregido y validado
- [ ] Logs respaldados y revisados
- [ ] Datos afectados restaurados (si aplica)
- [ ] Informe técnico y legal completado