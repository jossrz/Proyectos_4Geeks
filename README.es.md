<!-- hide -->
# Proyecto final de ciberseguridad

> By [@rosinni](https://github.com/rosinni) and [other contributors](https://github.com/4GeeksAcademy/cybersecurity-final-project/graphs/contributors) at [4Geeks Academy](https://4geeksacademy.co/)

![last commit](https://img.shields.io/github/last-commit/4geeksacademy/cybersecurity-final-project)
[![build by developers](https://img.shields.io/badge/build_by-Developers-blue)](https://4geeks.com)
[![build by developers](https://img.shields.io/twitter/follow/4geeksacademy?style=social&logo=twitter)](https://twitter.com/4geeksacademy)

*These instructions are [available in english](https://github.com/breatheco-de/cybersecurity-final-project/blob/main/README.md)*

### Antes de empezar...

> ¡Te necesitamos! Estos ejercicios se crean y mantienen en colaboración con personas como tú. Si encuentras algún error o falta de ortografía, contribuye y/o repórtalo.
<!-- endhide -->

## 🌱 ¿Cómo empezar este proyecto?

Para este proyecto final, asumirás el rol de analista de ciberseguridad encargado de restaurar y proteger un servidor crítico que ha sido comprometido en 4Geeks Academy. Se te proporcionará una [máquina hackeada](https://storage.googleapis.com/breathecode/virtualbox/debian-final-project.ova) que simula un servidor clave de la empresa, y tu tarea será restablecer su seguridad, corregir las vulnerabilidades explotadas y garantizar su funcionamiento óptimo. El ejercicio se divide en tres fases que pondrán a prueba tus habilidades en análisis forense, detección y corrección de vulnerabilidades, y respuesta ante incidentes.

- **Fase 1 - Corrección de un hackeo**
Durante la primera fase, deberas realizar un análisis forense del incidente, identificar las vulnerabilidades explotadas por el atacante, y bloquear el exploit para evitar que el ataque escale. 

- **Fase 2 - Detección y corrección de una nueva vulnerabilidad**
En la segunda fase, escanea el sistema en busca de una vulnerabilidad adicional, diferente a la explotada anteriormente. Tras detectarla, explota la vulnerabilidad de manera controlada para entender su impacto, escalar sus privilegios, corregirla, y crear un informe que explique todo el proceso.

- **Fase 3 - Plan de respuesta a incidentes y certificación**
La fase final consiste en diseñar un plan de respuesta a incidentes basado en las mejores prácticas de la industria, como las recomendaciones del NIST. Como parte de este ejercicio, debes desarrollar un Sistema de Gestión de Seguridad de la Información (SGSI) conforme a la norma ISO 27001, que incluya medidas para prevenir la fuga de datos mediante políticas de prevención de pérdida de datos (DLP).

## 📝 Instrucciones

### Fase 1: Reconocimiento y recolección de evidencias

**Objetivo:** Lleva a cabo un análisis forense para bloquear el exploit, corregir la vulnerabilidad y evitar que el atacante escale.

1. Identifica qué servicios fueron comprometidos y cómo el atacante accedió al servidor. Pueden usar herramientas como grep para revisar los logs del sistema (por ejemplo, /var/log/auth.log para conexiones SSH).
2. Identifica archivos sospechosos, procesos en ejecución y cualquier modificación inusual en el sistema.
3. Realiza un escaneo del servidor para detectar rootkits o malware.
4. Bloquea el exploit y previene la escalación. Deten los servicios comprometidos temporalmente (`systemctl stop servicio`) en caso de ser necesario.
5. Revierte los cambios realizados por el atacante (eliminar usuarios no autorizados, eliminar backdoors, cerrar puertos innecesarios).
6. Actualiza y corrige configuraciones de seguridad (actualiza paquetes, cambia contraseñas, mejora configuraciones de firewall, si es necesario).
7. Prepara un informe detallado que incluya las medidas tomadas para mitigar el ataque y evitar la escalación. Además incluye recomendaciones sobre cómo prevenir futuros ataques de la misma índole.

### Fase 2: Detecta y corrige una vulnerabilidad diferente

**Objetivo:** Escanear, detectar y explotar una vulnerabilidad diferente a la explotada anteriormente y crear un informe que explique todo el proceso.

1. Realiza un escaneo completo del sistema usando herramientas como `Nmap`.
2. Detecta una vulnerabilidad no relacionada con el hackeo anterior, como una mala configuración en Apache, puertos abiertos innecesarios, o un servicio expuesto y explota esta vulnerabilidad detectada.
4. Documenta el proceso de explotación y los pasos realizados para comprometer el servicio o escalar privilegios.
5. Aplica medidas para corregir la vulnerabilidad encontrada, como cerrar puertos, cambia configuraciones de seguridad, o restringe accesos.
6. Prepara un informe detallado que incluya la vulnerabilidad detectada, el proceso de explotación y las medidas aplicadas para corregirla.

### Fase 3: Plan de respuesta de incidentes y certificación

**Objetivo:** Diseña un plan de respuesta a incidentes basado en las mejores prácticas y desarrolla un Sistema de Gestión de Seguridad de la Información (SGSI) conforme a la norma ISO 27001.

1. Desarrolla un plan de respuesta basado en la guía del NIST SP 800-61, que incluya cómo identificar, contener, erradicar y recuperar de futuros incidentes de seguridad.
2. Detalla cómo la organización respondería a un ataque similar al hackeo realizado y cómo prevenir la recurrencia.
3. Identifica y documenta los mecanismos de protección de datos, como el uso de respaldos periódicos, cifrado de datos sensibles y la implementación de controles de acceso estrictos.
4. Implementar un SGSI (ISO 27001). Desarrolla un Sistema de Gestión de Seguridad de la Información (SGSI) que cumpla con los estándares de ISO 27001, como: análisis de riesgos,
definición de políticas de seguridad, planes de acción para proteger la información crítica de la empresa.

## 📦 ¿Cómo entregar este proyecto?

- [ ] Crea un **diagrama de la red** usando herramientas como Packet Tracer, que refleje la topología de la red actual y los cambios recomendados.
- [ ] Presenta la **máquina virtual Debian** con los servicios configurados correctamente y los problemas solucionados.
- [ ] Elabora un **informe de pentesting**.
- [ ] Elabora un **informe de incidente de seguridad** detallando el análisis forense, las acciones correctivas y las medidas preventivas aplicadas.
- [ ] Elabora un **plan para la recuperación en caso de incidencia**, asegurando la continuidad de los servicios críticos de la empresa.
- [ ] Elabora una **presentación** con un enfoque ejecutivo para la gerencia, explicando lo ocurrido, las acciones tomadas, y las recomendaciones futuras.


## 👨‍💻 Para profesores

A continuación, se detallan las revisiones clave que el profesor debe considerar en el entregable del estudiante:

### Identificación y documentación de vulnerabilidades

- **Verificación de la configuración de MySQL:**
    - Confirmar que el estudiante ha identificado correctamente el usuario con contraseña débil.
    - Revisar si se sugiere una solución concreta (uso de contraseñas seguras, restricciones de acceso, etc.).

- **Configuración del servidor FTP:**
    - Validar que el estudiante ha analizado los permisos y acceso anónimo.
    - Confirmar si se recomienda desactivar accesos inseguros o reforzar la configuración.

- **Acceso SSH inseguro:**
    - Revisar si se han detectado métodos de autenticación débiles.
    - Confirmar si se proponen soluciones como deshabilitar root login o usar autenticación con clave pública.

- **Puertos abiertos innecesarios:**
    - Comprobar si el estudiante ha realizado un escaneo de puertos con nmap o herramientas similares.
    - Validar que ha identificado los servicios innecesarios y ha propuesto cerrar los puertos correspondientes.

- **Permisos en wp-config.php:**
    - Confirmar si se han revisado los permisos actuales y se propone una corrección (ejemplo: chmod 600 wp-config.php).

- **Directorio web listable:**
    - Revisar si se ha identificado la configuración en el servidor web (Apache/Nginx).
    - Comprobar si el estudiante ha aplicado la solución correcta (modificar .htaccess o Options -Indexes).


### Configuración y validación de la máquina Debian
- Revisar si la máquina con Debian tiene correctamente configurados los servicios con seguridad reforzada.
- Comprobar que se han aplicado las soluciones propuestas y que se han realizado pruebas para validar su efectividad.

### Informes requeridos
    
- Informe de pentesting: Confirmar que incluye detalles de cada vulnerabilidad, pruebas realizadas y soluciones aplicadas.

- Informe de incidente de seguridad: Validar si se describe un análisis forense de los hallazgos y revisar que se expliquen las medidas correctivas y preventivas implementadas.

- Plan de recuperación ante incidentes: Comprobar si el plan cubre los servicios críticos y detalla procedimientos de recuperación.

- Presentación ejecutiva para la gerencia: Evaluar si está estructurada de forma clara y profesional. Verificar si incluye un resumen de los problemas detectados, soluciones implementadas y recomendaciones futuras.

<-- hide -->
El profesor debe asegurarse de que el entregable no solo documente los hallazgos, sino que también proponga soluciones aplicables y muestre pruebas de su implementación. La presentación debe estar alineada con un enfoque profesional y orientado a la gerencia.

## Colaboradores

Gracias a estas personas maravillosas ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

1. [Rosinni Rodríguez (rosinni)](https://github.com/rosinni) contribución: (build-tutorial) ✅, (documentación) 📖
  
2. [Alejandro Sanchez (alesanchezr)](https://github.com/alesanchezr),  contribución: (detector bugs) 🐛

Este proyecto sigue la especificación [all-contributors](https://github.com/kentcdodds/all-contributors). ¡Todas las contribuciones son bienvenidas!

Este y otros ejercicios son usados para [aprender a programar](https://4geeksacademy.com/es/aprender-a-programar/aprender-a-programar-desde-cero) por parte de los alumnos de 4Geeks Academy [Coding Bootcamp](https://4geeksacademy.com/us/coding-bootcamp) realizado por [Alejandro Sánchez](https://twitter.com/alesanchezr) y muchos otros contribuyentes. Conoce más sobre nuestros [Cursos de Programación](https://4geeksacademy.com/es/curso-de-programacion-desde-cero?lang=es) para convertirte en [Full Stack Developer](https://4geeksacademy.com/es/coding-bootcamps/desarrollador-full-stack/?lang=es), o nuestro [Data Science Bootcamp](https://4geeksacademy.com/es/coding-bootcamps/curso-datascience-machine-learning).Tambien puedes adentrarte al mundo de ciberseguridad con nuestro [Bootcamp de ciberseguridad](https://4geeksacademy.com/es/coding-bootcamps/curso-ciberseguridad).
<!-- endhide -->
