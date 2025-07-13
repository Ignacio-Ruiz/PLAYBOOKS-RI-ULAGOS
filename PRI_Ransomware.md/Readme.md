# 📘 Playbook 04: Ransomware
**Tipo de Incidente:** Infección por Ransomware  
**Versión:** 1.0  


---

## 1️⃣ Preparación

**🎯 Objetivo:** Alistarse para manejar el incidente

- Tener buen conocimiento de políticas de seguridad y perfiles de usuario.
- Mantener actualizados productos de seguridad (correo, gateways, proxy, etc.).
- Aumentar la formación de usuarios finales y soporte TI sobre amenazas de ransomware.
- Asegurar copias de seguridad recientes, confiables y externas (local y red).

---

## 2️⃣ Detección

**🎯 Objetivo:** Detectar el incidente

### 🧩 Principales indicios de ransomware:
- Correos electrónicos con archivos adjuntos sospechosos.
- Presencia de “nota de secuestro” en el escritorio.
- Quejas de usuarios sobre archivos inaccesibles o cifrados.
- Archivos con extensiones inusuales (.abx, .xyz, .aaa).
- Cambios masivos en archivos en carpetas compartidas.

### 🔎 Identificación basada en el host:
- Ejecutables sospechosos en `%ALLUSERSPROFILE%`, `%APPDATA%`, `%SystemDrive%`.
- Notas de rescate.
- Imagen de memoria (si es posible).
- Procesos y adjuntos inusuales.
- Conexiones a Tor, I2P o sitios de pago en Bitcoin.

### 🌐 Identificación basada en la red:
- Patrones de conexión con Kits Exploit o C&C del ransomware.
- Navegación inusual (Tor2web, I2P).
- Archivos adjuntos maliciosos en correos.

---

## 3️⃣ Contención

**🎯 Objetivo:** Limitar el impacto del incidente

- Desconectar de la red los equipos comprometidos.
- Si no es posible, cancelar unidades compartidas (`NET USE X:`).
- Bloquear tráfico a servidores C&C.
- Enviar muestras de malware al proveedor de seguridad.
- Reportar URL o IP sospechosa.

---

## 4️⃣ Erradicación

**🎯 Objetivo:** Remover la amenaza

- Eliminar binarios y entradas del registro maliciosas.
- Rutas comunes: `%ALLUSERSPROFILE%`, `%APPDATA%`, `%SystemDrive%`.
- Si no es posible, reinstalar el equipo con una imagen limpia.

---

## 5️⃣ Recuperación

**🎯 Objetivo:** Restaurar operaciones normales

- Actualizar firmas antivirus.
- Asegurarse de que los binarios maliciosos hayan sido eliminados.
- Restaurar sistemas con respaldo verificado.
- Comunicar oficialmente el cierre del incidente.
- Reforzar copia de seguridad confiable.

---

## 6️⃣ Lecciones aprendidas

**🎯 Objetivo:** Evaluar lecciones aprendidas y mejorar procesos

### 📄 Informe post-mortem
Debe incluir:
- Detección inicial
- Acciones y plazos
- Lo que salió bien y mal
- Costo del incidente

### 🛠 Retrospectiva 
- Evaluar métodos de entrada de malware.
- Revisar y mejorar procedimientos.
- Considerar test externos de seguridad.
- Colaborar con CSIRTs y otras organizaciones.

---

## 📝 Información de Fuente

- **Autor IRM:** CERT SG / Jean-Philippe Teissier  
- **Versión:** 1.0  
- **Web:** [cert.societegenerale.com](http://cert.societegenerale.com)  
- **Email:** cert.sg@socgen.com  
- **Traducción:** Francisco Neira  
