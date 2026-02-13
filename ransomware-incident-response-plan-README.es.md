#  Plan de respuesta a incidente de ransomware basado en NIST
<!-- hide -->

> By [@rosinni](https://github.com/rosinni) and [other contributors](https://github.com/breatheco-de/ransomware-incident-response-plan/graphs/contributors) at [4Geeks Academy](https://4geeksacademy.co/)

[![build by developers](https://img.shields.io/badge/build_by-Developers-blue)](https://4geeks.com)
[![build by developers](https://img.shields.io/twitter/follow/4geeksacademy?style=social&logo=twitter)](https://twitter.com/4geeksacademy)

*Estas instrucciones estan [disponibles en español](https://github.com/breatheco-de/ransomware-incident-response-plan/blob/main/README.es.md)*
<!-- endhide -->


<!-- hide -->


### Antes de empezar...

> ¡Te necesitamos! Estos ejercicios se crean y mantienen en colaboración con personas como tú. Si encuentras algún error o falta de ortografía, contribuye y/o repórtalo.

<!-- endhide -->

## 🌱 ¿Cómo empezar este proyecto?
Este ejercicio se centra en el desarrollo de un **Plan de Respuesta a Incidente de Ransomware** utilizando el marco de ciberseguridad NIST, basado en el caso de estudio de una empresa ficticia llamada **TechCo**. Se explorarán las áreas de identificación, protección, detección, respuesta y recuperación frente a un ataque de ransomware. 

## 🔍 Caso de Ejemplo: TechCo bajo Ataque de Ransomware

La empresa ficticia **TechCo**, dedicada a ofrecer servicios en la nube y gestionar datos confidenciales de sus clientes, ha sido víctima de un ataque de ransomware.

### Descripción del incidente:
- **Origen del ataque**: Un empleado de TechCo recibió un correo electrónico de phishing que parecía legítimo, con un archivo adjunto malicioso disfrazado de factura. El empleado descargó el archivo, permitiendo a los atacantes instalar el ransomware en la red interna de TechCo.

- **Propagación**: El ransomware se extendió rápidamente a varios servidores críticos. Los sistemas afectados incluyen:
  - El **servidor de archivos**, donde se almacenan documentos y datos esenciales para el funcionamiento diario.
  - La **base de datos de clientes**, que contiene información personal y financiera sensible.
  - Los **sistemas de backup** internos que, desafortunadamente, también se encontraban dentro de la misma red comprometida.

- **Impacto del ataque**: Los archivos fueron cifrados, y la empresa recibió un mensaje exigiendo el pago de 50 Bitcoins (equivalente a más de $1,000,000) para obtener la clave de descifrado. Los atacantes amenazaron con eliminar permanentemente todos los archivos si el rescate no se paga en un plazo de 72 horas.

- **Problemas adicionales**:
  1. La red no contaba con una segmentación adecuada, lo que permitió que el ransomware afectara tanto los sistemas de producción como los backups.
  2. No había un protocolo de alerta temprana ni sistemas de monitoreo en tiempo real, por lo que la propagación del ransomware no fue detectada hasta que los empleados comenzaron a notar la falta de acceso a los archivos.
  3. Los esfuerzos por restaurar los sistemas desde los backups fallaron, ya que estos también estaban cifrados por el ransomware.

### Solicitud de la empresa:
La gerencia de TechCo busca desarrollar un plan de respuesta formal para evitar que incidentes similares ocurran en el futuro y para mitigar el impacto de ataques futuros.


## 📝 Instrucciones

Para realizar el informe ten en cuenta los siguientes items.

1. **Identificación:** Identifica los activos críticos de **TechCo** que han sido afectados o podrían haber sido el objetivo del ataque. Considera los sistemas clave para las operaciones de la empresa y evalúa las posibles vulnerabilidades que facilitaron el ataque.

2. **Protección:** Describe las medidas preventivas que **TechCo** debería haber implementado para protegerse del ataque. Evalúa qué políticas y controles de seguridad hubieran mitigado o evitado la propagación del ransomware.

3. **Detección:** Proporciona métodos y herramientas que **TechCo** podría haber utilizado para detectar el ataque de ransomware en sus primeras fases. Considera cómo un protocolo de alerta temprana podría haber mejorado la detección del incidente.

4. **Respuesta:** Desarrolla un plan detallado para responder al ataque de ransomware en **TechCo**. Define los pasos que el equipo debe seguir una vez detectado el incidente. Asigna roles y responsabilidades claras al equipo de respuesta y especifica cómo deben comunicarse tanto interna como externamente.

5. **Recuperación:** Describe los pasos que **TechCo** debería tomar para restaurar los sistemas y datos afectados por el ataque de ransomware. Asegúrate de incluir planes de continuidad del negocio durante y después de la recuperación.

6. **Mejora continua:** Propon un método para evaluar la eficacia del plan de respuesta después del incidente. Considera cómo pueden integrarse las lecciones aprendidas en futuras mejoras del plan.

## 📦 ¿Cómo entregar este proyecto?

Entrega un informe que cubra cada una de las áreas mencionadas, alineado con las cinco funciones clave del marco de ciberseguridad NIST: Identificación, Protección, Detección, Respuesta y Recuperación.


<!-- hide -->

## Colaboradores

Gracias a estas personas maravillosas ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

1. [Rosinni Rodriguez (rosinni)](https://github.com/rosinni) contribution: (build-tutorial) ✅, (documentation) 📖
  
2. [Alejandro Sanchez (alesanchezr)](https://github.com/alesanchezr),  contribution: (bug reports) 🐛

Este proyecto sigue la especificación [all-contributors](https://github.com/kentcdodds/all-contributors). ¡Todas las contribuciones son bienvenidas!

Este y otros ejercicios son usados para [aprender a programar](https://4geeksacademy.com/es/aprender-a-programar/aprender-a-programar-desde-cero) por parte de los alumnos de 4Geeks Academy [Coding Bootcamp](https://4geeksacademy.com/us/coding-bootcamp) realizado por [Alejandro Sánchez](https://twitter.com/alesanchezr) y muchos otros contribuyentes. Conoce más sobre nuestros [Cursos de Programación](https://4geeksacademy.com/es/curso-de-programacion-desde-cero?lang=es) para convertirte en [Full Stack Developer](https://4geeksacademy.com/es/coding-bootcamps/desarrollador-full-stack/?lang=es), o nuestro [Data Science Bootcamp](https://4geeksacademy.com/es/coding-bootcamps/curso-datascience-machine-learning).Tambien puedes adentrarte al mundo de ciberseguridad con nuestro [Bootcamp de ciberseguridad](https://4geeksacademy.com/es/coding-bootcamps/curso-ciberseguridad).

<!-- endhide -->
