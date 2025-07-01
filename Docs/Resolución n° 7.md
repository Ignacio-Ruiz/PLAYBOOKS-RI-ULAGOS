# Resumen Resolución Núm. 7 Exenta – Taxonomía de Incidentes de Ciberseguridad

La resolución a la que se hace referencia es la **Resolución Núm. 7 exenta**, emitida en Santiago el 28 de febrero de 2025, por la Agencia Nacional de Ciberseguridad. Fue publicada en el Diario Oficial el sábado 1 de marzo de 2025, bajo el número 44.088 y CVE 2617388.

El propósito principal de esta resolución es aprobar la **taxonomía de incidentes de ciberseguridad**.

---

## Puntos clave

- **Marco Legal y Creación de la Agencia:**  
  La resolución se fundamenta en la Ley N° 21.663, marco de Ciberseguridad, que creó la Agencia Nacional de Ciberseguridad como un servicio público descentralizado y especializado en ciberseguridad. Esta ley también estableció el Equipo Nacional de Respuesta a Incidentes de Seguridad Informática (CSIRT Nacional) dentro de la Agencia.

- **Obligación de Reporte:**  
  El artículo 9° de la ley N° 21.663 establece la obligación de reportar al CSIRT Nacional los ciberataques e incidentes de ciberseguridad que puedan tener efectos significativos.
  - Las instituciones públicas y privadas que presten servicios calificados como esenciales, así como aquellas calificadas como operadores de importancia vital, deben realizar estos reportes.
  - El reporte debe hacerse tan pronto como sea posible.

- **Plataforma de Reporte:**  
  Los reportes se deben realizar a través de la plataforma dispuesta por la Agencia Nacional de Ciberseguridad, disponible en la URL [https://portal.anci.gob.cl](https://portal.anci.gob.cl) las veinticuatro horas, todos los días del año, o por otros medios que la Agencia establezca.

- **Contenido del Reporte y Clasificación:**  
  Los informes enviados al CSIRT Nacional deben incluir una descripción del incidente, si se puede identificar. Para clasificar el incidente, se deben considerar los efectos observables del hecho, es decir, cualquier contexto, escenario o circunstancia que pueda ser observada directamente.

- **Taxonomía de Incidentes de Ciberseguridad:**  
  La resolución establece una taxonomía que consta de **cuatro áreas de impacto** y **once efectos observables**:

  - **Impacto en el uso legítimo de recursos:**
    - Uso no autorizado de redes y sistemas informáticos.
    - Actividades de phishing o fraude en infraestructura propia.
    - Actividades de phishing o fraude relacionadas con la institución.
    - Ejecución no autorizada de código.

  - **Impacto en la confidencialidad de la información:**
    - Exfiltración y/o exposición de datos.
    - Exfiltración y/o exposición de configuraciones.
    - Exfiltración y/o exposición de código fuente.

  - **Impacto en la disponibilidad de un servicio esencial:**
    - Indisponibilidad y/o denegación de servicio.
    - Degradación de servicio.

  - **Impacto en la integridad de la información:**
    - Modificación no autorizada de datos.
    - Manipulación no autorizada de configuración.

- **Categorías de Incidentes por Efecto Observable:**  
  Además de los efectos observables, la resolución detalla categorías específicas para cada uno de ellos, proporcionando una clasificación más granular (por ejemplo, dentro de "Uso no autorizado de redes y sistemas informáticos" se incluyen "Acceso no autorizado a almacenamiento", "Ataque de fuerza bruta exitoso", etc.).

---

La resolución fue firmada por **Daniel Álvarez Valenzuela**, Director Nacional de la Agencia Nacional de Ciberseguridad.

🛡️ Estructura base para playbooks:
Nombre del incidente
Fuente de Información y Marco Normativo  
Clasificación del Incidente según ANCI
Área de impacto
Impacto Operativo
Tipo de Activo Afectado
Descripción
Roles y Responsabilidades
Herramientas y recursos recomendados (NIST/CIS Controls)
Controles NIST SP 800-53 Rev. 5
CIS Critical Security Controls:
Herramientas Recomendadas:
Fases de respuesta
Preparación
Detección y Análisis
Contención
Erradicación
Recuperación
Lecciones Aprendidas
Registros y Evidencias
Indicadores de Compromiso (IOC)
Tiempo Estimado de Contención y Recuperación según casos reales
Checklist de Validación Final
Reporte ANCI (Plataforma) 