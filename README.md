#  Proyecto de Mensajería: Mattermost en Debian 13 (Trixie)

Este repositorio contiene la documentación técnica, el proceso de instalación y las pruebas de funcionamiento de un servidor de mensajería **Mattermost** desplegado en un entorno de red local.


##  1. ¿Qué es Mattermost?

**Mattermost** es una plataforma de colaboración de código abierto (Open Source). Es la alternativa privada a Slack, diseñada para que las organizaciones tengan el control total de sus datos, comunicaciones y archivos en su propio servidor.

### 🔄 Comparativa: Mattermost vs. ejabberd

| Característica | Mattermost | ejabberd |
| :--- | :--- | :--- |
| **Estilo** | Moderno, basado en canales y hilos. | Mensajería clásica (protocolo XMPP). |
| **Interfaz** | Web e intuitiva (tipo WhatsApp/Slack). | Técnica, requiere clientes externos. |
| **Multimedia** | Gestión de archivos nativa y fluida. | Más limitada y compleja de configurar. |
| **Uso Ideal** | Equipos de trabajo y desarrollo. | Sistemas de chat masivos y simples. |



##  2. Proceso de Instalación en Debian 13

La instalación se realizó de forma directa utilizando el repositorio oficial de Mattermost para garantizar la compatibilidad con **Debian 13 "Trixie"**.

### Pasos ejecutados:

1. **Actualizar el sistema:**

   sudo apt update && sudo apt upgrade -y


Configurar el repositorio oficial:
Utilizamos el script de configuración automática para añadir las llaves GPG y el repo:

Bash

curl -L [https://deb.packages.mattermost.com/setup-repo.sh](https://deb.packages.mattermost.com/setup-repo.sh) | sudo bash
Instalar el servidor:

Bash
sudo apt install mattermost -y
 3. Verificación del Servicio
Tras la instalación, comprobamos que el servicio de Mattermost esté corriendo correctamente en el sistema mediante systemctl.

Comando de verificación:

Bash
sudo systemctl status mattermost

<img width="735" height="213" alt="image" src="https://github.com/user-attachments/assets/a4a6dd10-d626-48b1-8eff-e8be2f33248c" />


 4. Configuración de Red (Modo Bridge)
Para permitir que dos Máquinas Virtuales (MV) se comuniquen en la misma red local:

Configuración: Se estableció el adaptador de red en Modo Puente (Bridge) en el virtualizador.

IP del Servidor: La dirección asignada fue 192.168.109.72.

Acceso Cliente: Se abre el navegador en la máquina cliente y se ingresa a: http://192.168.109.72:8065

 5. Prueba de Funcionamiento y Chat
Para validar el éxito del trabajo, se realizó una prueba de mensajería real entre los usuarios chris y punky. Esto confirma que tanto el servidor como la base de datos y la conexión de red funcionan perfectamente.


<img width="1849" height="918" alt="image" src="https://github.com/user-attachments/assets/d7e9518b-48a5-4251-9972-d793dad45e8d" />


 Conclusión
El despliegue ha sido exitoso. Mattermost ofrece una experiencia de usuario muy superior a sistemas antiguos como ejabberd, permitiendo una comunicación moderna, fluida y totalmente privada dentro de nuestra infraestructura local.




