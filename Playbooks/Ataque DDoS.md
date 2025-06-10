# Playbook de Respuesta a Incidente: R-06 - Ataque DDoS

🛑 **Clasificación del Incidente**  
- **Categoría ANCI:** Disponibilidad-Afectación de Servicios (DDoS)  
- **Nivel de Criticidad:** Alta  
- **Tipo de Activo Afectado:** Servicios web, servidores institucionales y red perimetral

---

🧩 **Descripción**  
Un ataque de denegación de servicio distribuido (DDoS) busca saturar los recursos de red, servidores o aplicaciones, provocando la indisponibilidad de servicios institucionales como portales web, plataformas académicas o servicios internos. Puede ser ejecutado desde múltiples fuentes coordinadas y causar interrupciones operativas severas.

---

👥 **Roles y Responsabilidades**

| Rol                        | Responsabilidad                                                                 |
|----------------------------|-------------------------------------------------------------------------------|
| CSIRT Universitario        | Coordina la respuesta técnica y comunica con entidades externas (ISP)          |
| Encargado de Redes         | Monitorea tráfico, aplica reglas de filtrado y analiza vectores de ataque      |
| Proveedor de Servicios ISP | Coopera en la mitigación del tráfico en tránsito                               |
| Dirección de Informática   | Supervisa la estrategia de respuesta y coordina con autoridades                |
| Comunicaciones Institucionales | Informa a usuarios sobre afectación de servicios y estimaciones de normalización |

---

## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

**NIST SP 800-53 Rev. 5:**
- `SC-5`: Protección contra Denegación de Servicio
- `SI-4`: Monitoreo del Sistema
- `CP-2`: Planificación de Contingencias
- `SC-7`: Protección del Límite de Red
- `IR-4`: Manejo de Incidentes

**Controles Críticos de Seguridad CIS:**
- `CIS Control 12`: Defensa de Perímetro
- `CIS Control 13`: Protección de Datos (Resiliencia de Red)
- `CIS Control 16`: Monitoreo y Control de Cuentas
- `CIS Control 18`: Seguridad del Software de Aplicación
- `CIS Control 19`: Respuesta y Gestión de Incidentes

**Herramientas Recomendadas:**
- Servicios de Mitigación DDoS: Cloudflare, Akamai Prolexic, AWS Shield
- Monitoreo de Red: SolarWinds NPM, Zabbix, Nagios, PRTG Network Monitor
- Análisis de Flujos: NetFlow, sFlow, recolectores IPFIX (ElasticFlow, Plixer Scrutinizer)
- Soluciones de Firewall: FortiGate, Palo Alto Networks, Cisco Firepower
- Sistemas IDS/IPS: Suricata, Snort, Darktrace
- Herramientas de Análisis de Tráfico: Wireshark, tcpdump, ntopng
- Balanceadores de Carga: F5 BIG-IP, HAProxy, Nginx Plus
- Protección en la Nube: Azure DDoS Protection, GCP Cloud Armor

---

🧭 **Fases de Respuesta**

1. **Preparación**
   - Implementar mitigación básica (firewalls, listas de control de acceso, rate limiting)
   - Establecer acuerdos con ISP para activar mitigación avanzada
   - Tener planes de continuidad operativa ante fallos de servicios críticos
   - Monitoreo proactivo con herramientas como NetFlow, SNMP o IDS

2. **Detección y Análisis**
   - Identificar aumento abrupto de tráfico, uso de ancho de banda y caída de servicios
   - Correlacionar alertas de red, logs de servidores y análisis de tráfico
   - Confirmar que se trata de un DDoS mediante patrones (SYN flood, UDP flood, HTTP GET flood, etc.)

3. **Contención**
   - Activar reglas de bloqueo por origen IP, puertos o protocolos maliciosos
   - Notificar al proveedor de servicios para filtrar tráfico aguas arriba
   - Redirigir tráfico a servicios de mitigación en la nube si se dispone

4. **Erradicación**
   - Ajustar reglas y configuraciones para mitigar futuras recurrencias
   - Actualizar firmas y listas negras en firewalls e IDS
   - Revisar logs y posibles consecuencias colaterales (exfiltración encubierta)

5. **Recuperación**
   - Restablecer los servicios afectados tras disminución del ataque
   - Verificar disponibilidad completa y validación funcional
   - Reanudar comunicaciones oficiales y monitoreo extendido

6. **Lecciones Aprendidas**
   - Documentar vectores utilizados, duración y efectividad de la respuesta
   - Evaluar mejoras en infraestructura de mitigación (ej. balanceadores, servicios cloud)
   - Actualizar el plan de continuidad operativa y simulacros periódicos

---

📦 **Evidencias a Recolectar**
- Logs de tráfico (NetFlow, firewall, IDS)
- Reportes del proveedor de internet
- Gráficas de consumo de red (antes, durante y después del ataque)
- Registros de afectación en los servicios

---

📌 **Indicadores de Compromiso (IOC)**
- Picos de tráfico no justificados
- Conexiones entrantes desde cientos o miles de IPs únicas
- Paquetes anómalos (volumen y frecuencia elevada)
- Saturación de CPU o memoria en routers/firewalls

---

📅 **Tiempo Estimado de Contención y Recuperación**
- **Contención:** 1–2 horas (según el nivel de preparación)
- **Recuperación:** 2–6 horas (según gravedad y persistencia)

---

✅ **Checklist de Validación Final**
- [ ] Tráfico DDoS mitigado
- [ ] Servicios críticos restaurados
- [ ] Coordinación con ISP completada
- [ ] Registro y documentación del incidente almacenada