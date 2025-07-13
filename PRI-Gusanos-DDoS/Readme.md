# 🛡️ Playbook 02: Gusanos / DDoS
**Tipo de Incidente:** Disponibilidad-Afectación Servicios web, servidores institucionales y red perimetral
**Versión:** 1.0

---

## 1️⃣ Preparación

**Objetivo:** Establecer contactos, definir procedimientos y recolectar información para ahorrar tiempo durante un ataque.

### Acciones:

**Apoyo del proveedor de Servicio de Internet(ISP):** 
- Contactar al ISP para conocer servicios de mitigación y posibilidades de conexión redundante.
- Establecer contactos legales para cumplimiento.
**Inventario:** 
- Crear lista blanca de direcciones IPs críticas que se deben permitir si se prioriza el tráfico durante un ataque.
- Documentar los detalles de la infraestructura TI, incluyendo red y topología y un inventario de activos.
**Infraestructura de red:**
- Diseñar una correcta infraestructura de red resiliente, evitando puntos únicos de falla o cuellos de botella.
- Distribuir los servidores DNS y otros servicios críticos.

---

## 2️⃣ Detección

**Objetivo:** Detectar la infección y delimitar su alcance.

### Se debe recopilar y analizar la información proveniente de diferentes fuentes:
- Bitácoras de antivirus,
- Sistemas de Detección de Intrusión (IDS),
- Intentos sospechosos de conexión a servidores,
- Gran cantidad de cuentas bloqueadas,
- Tráfico de red sospechoso,
- Intentos sospechosos de conexión a los firewalls,
- Gran incremento en llamadas a Soporte,
- Cargas altas o sistemas "colgados",
- Grandes volúmenes de email enviados.

Si se observan uno o más de estos síntomas, deberán contactarse con los actores definidos en la etapa "Preparación" y si es necesario, crear una sala de crisis.

### Acciones:
**Identificar la infección**
- Analizar lo síntomas para identificar el gusano, sus vectores de propagación y contramedidas.
- Encontrar hallazgos
- Notificar a actores claves de la universidad, contactar al CSIR Nacional.
**Evaluar el perímetro de la infección**
- Definir la extensión de la infección (el incidente es global o limitado a una oficina, etc).
- Identificar el impacto de la infección las operaciones

---

## 3️⃣ Contención

**Objetivo:** Mitigar los efectos del ataque.

### Acciones:
1. Desconectar el área infectada de Internet
2. Aislar el área infectada. Desconéctela de cualquier red
3. Si no se puede desconectar el tráfico crítico, permitir después de asegurarse que no es un vector de infección o después de aplicar técnicas validadas de eliminación.
4. Neutralizar los vectores de propagación. Un vector de propagación puede ser cualquier cosa desde el tráfico de red hasta una falla en el software. Se aplicarán contramedidas relevantes (parches, bloqueo de tráfico, deshabilitar dispositivos, etc.). Por ejemplo, se pueden emplear las siguientes:
   - Herramientas de despliegue de parches (WSUS),
   - Windows GPO,
   - Reglas de firewall,
   - Procedimientos operacionales.
5. Repetir los pasos 2 al 4 en cada sub-área del área infectada hasta que el gusano deje de propagarse. Si es posible, monitoree la infección empleando herramientas de análisis (consola del antivirus, bitácoras de servidor, llamadas a Soporte)

*Debe de monitorearse la dispersión del gusano.*

**Dispositivos móviles**

- Asegurar que el gusano no pueda utilizar ninguna laptop, smartphone, PDA o dispositivo removible de almacenamiento como vector de propagación. De ser posible, bloquear las conexiones.
---

## 4️⃣ Erradicación

**Objetivo:** Eliminar la amenaza sin afectar servicios.

## Acciones 

**Identificar**
Identificar herramientas y métodos de remedio. Deben de considerarse los siguientes recursos:
- Arreglos (fixes) del proveedor (Microsoft, Oracle, etc.),
- Base de datos de firmas del antivirus,
- Contactos externos de Soporte,
- Sitios web de Seguridad.
- Definir un proceso de desinfección. El proceso debe de ser validado por la ANCI o REUNA.

**Probar**
- Probar el proceso de desinfección y asegurar que funciona adecuadamente sin dañar algún servicio.

**Desplegar**

- Desplegar las herramientas de desinfección. Se pueden usar varias opciones: Windows WSUS, GPO, despliegue de firmas de antivirus, desinfección manual.

*Advertencia:* Algunos gusanos podrían bloquear alguno de los métodos de despliegue de remedios. Si esto sucede, deberá de aplicarse algún artificio.

el progreso de erradicación debe ser monitoreado por el personal encargado.
---

## 5️⃣ Recuperación

**Objetivo:** Verificar restauración del funcionamiento.

## Acciones 
Verificar que todos los pasos previos se hayan realizado correctamente y obtener una aprobación de alta dirección antes de proceder con los siguientes pasos:

1. Reabrir el tráfico de red que fue utilizado como método de propagación por el gusano.
2. Reconectar las sub-áreas entre sí.
3. Reconectar las laptops y móviles al área.
4. Reconectar el área a la red local.
5. Reconectar el área a Internet.

Todos estos pasos deben de realizarse en una manera “paso a paso” y se debe realizar un monitoreo técnico puesto en vigor por el equipo de respuesta.

---

## 6️⃣ Lecciones aprendidas

**Objetivo:** Documentar el incidente y mejorar procesos.

### Informe:
Deberá de redactarse un informe de crisis que será distribuido entre todos los actores quienes gestionaron el incidente.

Deben de describirse los siguientes temas:
- Causa inicial de la infección,
- Acciones y líneas de tiempo de cada evento importante,
- Qué salió bien,
- Qué salió mal,
- Costo del incidente.

### Retrospectiva:
Deberán de definirse las acciones para mejorar los procesos de manejo de infecciones de gusanos para convertir esta experiencia en una oportunidad de mejora.

- Evaluar preparación
- Ajustar procesos
- Compartir lecciones aprendidas

---

## 📄 Referencia 

- **Fuente:** CERT SG 
- **Web:** [cert.societegenerale.com](http://cert.societegenerale.com)  
- **Email:** cert.sg@socgen.com  
