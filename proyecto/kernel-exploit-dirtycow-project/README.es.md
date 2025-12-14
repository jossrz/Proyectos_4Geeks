# Escalamiento de Privilegios usando el Kernel Exploit Dirty Cow
<!-- hide -->

> By [@rosinni](https://github.com/rosinni) and [other contributors](https://github.com/breatheco-de/kernel-exploit-dirtycow-project/graphs/contributors) at [4Geeks Academy](https://4geeksacademy.co/)

[![build by developers](https://img.shields.io/badge/build_by-Developers-blue)](https://4geeks.com)
[![build by developers](https://img.shields.io/twitter/follow/4geeksacademy?style=social&logo=twitter)](https://twitter.com/4geeksacademy)

*Estas instrucciones están [disponibles en español](https://github.com/breatheco-de/kernel-exploit-dirtycow-project/blob/main/README.es.md)*
<!-- endhide -->

<!-- hide -->

### Antes de empezar...

> ¡Te necesitamos! Estos ejercicios se crean y mantienen en colaboración con personas como tú. Si encuentras algún error o falta de ortografía, contribuye y/o repórtalo.

<!-- endhide -->

## 🌱 ¿Cómo empezar este proyecto?

En la academia se encuentra desplegada una máquina virtual con una versión vulnerable de Ubuntu Server (16.04.1), que corre un kernel afectado por la falla **Dirty Cow** (CVE-2016-5195).

Como alumno, ya cuentas con acceso a este sistema mediante un usuario limitado llamado `student`. Tu objetivo será **identificar que el sistema es vulnerable**, **compilar y ejecutar un exploit real**, y **escalar tus privilegios para obtener acceso como root**. Este ejercicio representa una situación realista donde un atacante local, sin privilegios administrativos, logra comprometer completamente el sistema aprovechando una falla en el núcleo del sistema operativo. Los objetivos serán:

- Verificar la versión del kernel de un sistema Linux.
- Compilar un exploit real con `g++`, el cual es un compilador que se utiliza para compilar y enlazar programas escritos en **C++**, generando un archivo ejecutable a partir del código fuente.
- Escalar privilegios de un usuario limitado a `root`.
- Demostrar el éxito del ataque capturando una flag ubicada en `/root`.

Este tipo de explotación es típica en auditorías de seguridad avanzada y en entornos Red Team. Te permitirá conectar conceptos de bajo nivel del sistema operativo con técnicas ofensivas reales, de forma práctica y guiada.

### Requisitos

* [Máquina Ubuntu vulnerable con kernel `4.4.0-21-generic` (o similar sin parchear)](https://storage.cloud.google.com/cybersecurity-machines/dirty-cow-lab.ova)
* Acceso como usuario no privilegiado a la maquina vulnerable (`student:password123`)
* Maquina kali linux **(Atacante)**. Esta máquina es donde vas a realizar toda la preparación del exploit y debe contar con las siguientes herramientas:

    - **🔧 `Docker`:** Usaremos Docker para lanzar un contenedor de Ubuntu 16.04 y compilar el exploit con las mismas librerías que usa la víctima. Esto garantiza compatibilidad y evita errores por versiones modernas de compiladores o `glibc`.

    - **🔧 `g++`:** Es el compilador de C++. Lo usaremos para compilar el exploit `dirty.cpp`, que está escrito en este lenguaje. Nos permite generar un ejecutable (`dirty`) desde el código fuente.

    - **🔧 `scp` (Secure Copy Protocol):** Es una herramienta para copiar archivos de forma segura entre sistemas Linux. La usaremos para transferir el exploit compilado desde Kali hacia la máquina víctima.


> 🚨 Aviso Legal: Este repositorio contiene una versión limpia y comentada del exploit **Dirty Cow** (CVE-2016-5195), diseñada exclusivamente para fines **educativos**. Esta variante crea un nuevo usuario con privilegios de root explotando una condición de carrera en el subsistema de memoria del kernel de Linux. Este exploit es solo para **uso educativo**. Debe utilizarse en entornos **controlados y legales**, como laboratorios, máquinas virtuales de práctica o clases de ciberseguridad.

## 📝 Instrucciones

### Paso 1: Verificar la versión del kernel

1. Inicia sesión en la máquina vulnerable con el usuario limitado y ejecuta:

    ```bash
    uname -a
    ```

    Esto devuelve algo como:

    ```bash
    Linux dirtycow-lab 4.4.0-31-generic #50-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64 x86_64 x86_64 
    ```
2. Anota la version e investiga cómo explotar esa vulnerabilidad utilizando bases de datos como [Exploit-DB](https://www.exploit-db.com/exploits/40847), GitHub o searchsploit desde Kali. Para esta práctica **te proporcionamos un exploit funcional y documentado que puedes [descargar](https://raw.githubusercontent.com/breatheco-de/kernel-exploit-dirtycow-project/refs/heads/main/assets/dirty.cpp)**.



> ⚠️ **¡IMPORTANTE!** La máquina vulnerable no tiene herramientas de compilación instaladas, ni permisos `sudo` para agregarlas. Por eso, debemos compilar el exploit en Kali, dentro de un contenedor Docker con Ubuntu 16.04, que tenga las mismas versiones de glibc, libstdc++ y librerías del sistema de la maquina vulnerada porque de lo contrario dará problemas de versiones.

### Paso 2: Preparar el entorno en Kali con Docker

1. Instala Docker en Kali:

    ```bash
    sudo apt update
    sudo apt install docker.io -y
    sudo systemctl start docker
    sudo systemctl enable docker
    ```

2. Descarga la imagen de Ubuntu 16.04:

    ```bash
    sudo docker pull ubuntu:16.04
    ```

3. Lanza un contenedor:

    ```bash
    sudo docker run -it --name compile-ubuntu16 ubuntu:16.04
    ```

4. Instala herramientas de compilación:

    ```bash
    apt update
    apt install build-essential libutil-dev -y
    ```

### Paso 3: Crear y compilar el exploit dirty.cpp

1. Crea el archivo dentro del contenedor:

    ```bash
    nano dirty.cpp
    ```

    (Pega el código completo del exploit [dirty.cpp](https://raw.githubusercontent.com/breatheco-de/kernel-exploit-dirtycow-project/refs/heads/main/assets/dirty.cpp) proporcionado por la academia o desde [Exploit-DB 40847](https://www.exploit-db.com/exploits/40847))

2. Compila el binario:

    ```bash
    g++ -Wall -pedantic -O2 -std=c++11 -pthread -o dirty dirty.cpp -lutil
    ```

3. Sal del contenedor:

    ```bash
    exit
    ```

4. Copia el binario compilado desde el contenedor a Kali:

    ```bash
    sudo docker cp compile-ubuntu16:/dirty ./dirty
    ```

### Paso 4: Ejecutar en la víctima

1. Transfiere el binario a la víctima:

    ```bash
    scp dirty student@<IP_VICTIMA>:/home/student
    ```

2. En la víctima, ejecútalo:

    ```bash
    chmod +x dirty
    ./dirty
    ```

    Si el exploit tiene éxito veras un mensaje diciendote la contraseña asignada al usuario root.

### Paso 5: Escalar privilegios

1. Una vez finalizada la ejecución del exploit, cambia de usuario a `root`.
2. Verifica que tienes acceso como `root` ingresando la contraseña generada.
3. Por ultimo captura la flag. Para confirmar el éxito del ataque, lee el contenido del archivo de flag ubicado en el directorio `/root/flag.txt`. Si todo funcionó correctamente, verás el contenido de la flag.

