# Playbook de Respuesta a Incidente: R-33 - Ataque de Man-in-the-Middle (MitM)

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
   *Áre de impacto:* Intrusión (Intercepción de datos - Man-in-the-Middle)  
   *Impacto Operativo*: Alta  
   *Tipo de Activo Afectado:* Comunicaciones de red (transacciones de datos), dispositivos de usuario y servidores de autenticación

---

## 🧩 Descripción  
   Un ataque Man-in-the-Middle (MitM) ocurre cuando un atacante intercepta y, posiblemente, altera la comunicación entre dos partes (por ejemplo, un usuario y un servidor). Estos ataques pueden implicar la intercepción de datos sensibles, como contraseñas, información personal y comunicaciones privadas.  
   Los ataques MitM pueden ser llevados a cabo utilizando métodos como la suplantación de DNS, ARP Spoofing o el compromiso de certificados SSL/TLS.

---

## 👥 Roles y Responsabilidades

   | Rol                      | Responsabilidad                                                                 |
   |--------------------------|--------------------------------------------------------------------------------|
   | CSIRT Universitario      | Coordina la respuesta, análisis y contención del incidente                      |
   | Dirección de Informática | Supervisión general y validación de la comunicación de las acciones de respuesta|
   | Encargado de Redes       | Aísla segmentos de red afectados y valida las configuraciones de enrutamiento   |
   | Equipo de Soporte Técnico| Analiza logs de red, identifica anomalías y realiza actualizaciones de seguridad|
   | Asesor Legal             | Evalúa las implicancias legales relacionadas con la interceptación de datos     |

---
## 🛠️ Herramientas y Recursos (Controles NIST/CIS)

   **NIST SP 800-53 Rev. 5:**
   - `SC-8`: Confidencialidad e integridad de la transmisión
   - `SC-23`: Autenticidad de la sesión
   - `IA-2`: Identificación y Autenticación(Usuarios Organizacionales)
   - `IA-3`: Identificación y Autenticación de Dispositivos
   - `SC-7`: Protección de Límites
   - `SC-11`: Ruta Confiable
   - `SC-12`: Establecimiento y Gestión de Claves Criptográficas
   - `SC-17`: Certificados de infraestructura de clave pública
   - `SI-4`: Monitoreo del sistema
   - `CA-9`: Conexiones internas del sistema

   **Controles Críticos de Seguridad CIS:**
   - `CIS Control 3`: Protección de Datos 
   - `CIS Control 4`: Configuración Segura de Activos Empresariales y Software
   - `CIS Control 6`: Gestión de Control de Acceso
   - `CIS Control 9`: Protecciones de Correo Electrónico y Navegador Web 
   - `CIS Control 12`: Gestión de la Infraestructura de Red
   - `CIS Control 14`: Concientización sobre Seguridad y Capacitación de Habilidades
   - `CIS Control 16`: Seguridad del Software de Aplicación
   - `CIS Control 8`: Gestión de Registros de Auditoría 
   - `CIS Control 13`: Monitorización y Defensa de Red


   **Herramientas recomendadas:**
   - Monitoreo de red(Sniffers): Wireshark, tcpdump, Zeek (Bro)
   - Detección/prevención de intrusiones: Snort, Suricata, Zeek IDS
   - Gestión de certificados: Let's Encrypt, HashiCorp Vault, OpenSSL
   - Soluciones VPN: OpenVPN, WireGuard, Cisco AnyConnect
   - Herramientas de cifrado: Librerías TLS/SSL (OpenSSL), IPsec
   - Plataformas SIEM: Splunk, ELK Stack, QRadar
   - Escáneres de seguridad de red: Nmap, Nessus, OpenVAS
   - Protección ARP: Arpwatch, XArp

---

## 🧭 Fases de Respuesta

1. **Preparación**
   - Implementar cifrado en las comunicaciones (HTTPS, VPNs, TLS)
   - Mantener actualizado el software de seguridad de red y las herramientas de monitoreo
   - Establecer procedimientos para la validación de certificados y la autenticación mutua
   - Capacitar a los usuarios en la identificación de certificados inválidos o sospechosos

2. **Detección y Análisis**
   - Verificar si las conexiones están usando cifrado adecuado (TLS/SSL)
   - Revisar logs de red y comunicaciones en busca de tráfico inusual o conexiones no autorizadas
   - Detectar alteraciones en la validación de certificados o interceptación de tráfico
   - Activar herramientas de detección de intrusos y monitorización de tráfico (IDS/IPS)
   - Confirmar la naturaleza del ataque: ¿es interceptación de tráfico o manipulación de datos?

3. **Contención**
   - Aislar las redes y segmentos comprometidos para detener la propagación del ataque
   - Forzar el cierre de todas las sesiones activas comprometidas
   - Desactivar protocolos de red vulnerables o no cifrados (HTTP, FTP, etc.)
   - Deshabilitar cualquier ruta o conexión sospechosa entre los puntos de origen y destino

4. **Erradicación**
   - Cambiar las credenciales comprometidas, especialmente aquellas relacionadas con comunicaciones y servicios críticos
   - Reemplazar certificados SSL/TLS comprometidos con nuevos certificados emitidos
   - Aplicar parches de seguridad en todos los puntos vulnerables y verificar que no haya puertas traseras
   - Realizar un escaneo completo para asegurarse de que el sistema esté libre de software malicioso

5. **Recuperación**
   - Restaurar las conexiones seguras para los servicios y aplicaciones afectadas
   - Validar la integridad de los sistemas restaurados
   - Reconfigurar los dispositivos de red afectados y restablecer las rutas seguras
   - Monitorear de cerca el tráfico de red durante al menos 72 horas para detectar intentos de re-explotación

6. **Lecciones Aprendidas**
   - Revisión exhaustiva de los logs de red para entender cómo el atacante accedió a la comunicación
   - Análisis del tiempo de respuesta y eficacia de las medidas de contención y erradicación
   - Actualización de las políticas de cifrado y autenticación para evitar futuros incidentes de MitM
   - Capacitación adicional a los usuarios en cuanto a seguridad de las comunicaciones, incluyendo la validación de certificados y el uso de VPNs

---

## 📦 Registros y Evidencias
   - Capturas de tráfico de red antes, durante y después del ataque
   - Logs de acceso de los dispositivos afectados y las comunicaciones comprometidas
   - Copias de certificados SSL/TLS comprometidos
   - Registros de actividad del IDS/IPS y herramientas de análisis de tráfico de red

---

## 📌 Indicadores de Compromiso (IOC)
   - Certificados TLS con firmas no válidas o falsificadas
   - Tráfico de red que muestra señales de manipulación, como cambios en los paquetes o interrupciones en la validación de los datos
   - IPs sospechosas o no reconocidas interceptando la comunicación entre los sistemas

---

## 📅 Tiempo Estimado de Contención y Recuperación
   El tiempo estimado de contención y recuperación de un ataque Man-in-the-Middle (MitM) depende de factores como la complejidad del ataque, los sistemas afectados, la detección temprana y los controles implementados. Basado en estándares de respuesta a incidentes (NIST, SANS) y casos reales, se estiman los siguientes rangos:

   - *Contención*: De 15 minutos a 6 horas(Dependiendo si es un escenerio Simple o Complejo)
   - *Recuperación*: De 2 horas a 3 días (Si hay que revertir configuraciones)

---

## ✅ Checklist de Validación Final
   - [ ] Aislamiento de redes y dispositivos afectadas completado
   - [ ] Nueva infraestructura de red validada
   - [ ] Los certificados han sido reemplazados y validados
   - [ ] Los usuarios han sido informados y las sesiones de comunicación seguras han sido restauradas
   - [ ] Informe final generado y aprobado

---

## Reporte ANCI
   Plataforma: [https://portal.anci.gob.cl]

   **Campos requeridos:**
   - [ ] Código categoría principal + subcategoría
   - [ ] Hora detección primer efecto
   - [ ] Sistemas/servicios afectados
   - [ ] Evidencia técnica (logs, capturas)
   - [ ] Nivel de criticidad (Alto/Medio/Bajo)