# # 🖥️ Proyecto: Instalación de WordPress en Ubuntu Server

## 📖 Descripción
Este proyecto documenta la instalación y configuración de **WordPress en una máquina virtual con Ubuntu Server**.  
Cada paso incluye capturas de pantalla con el login de **Esemtia** visible para validar la autoría.

---

## 🛠️ Pasos realizados

###Instalación de Ubuntu Server en la máquina virtual
- Descarga de la ISO de Ubuntu Server.  
- Creación de la máquina virtual.  
- Configuración básica (idioma, teclado, red).  

📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)

---

### 2️⃣ Instalación de los paquetes necesarios
Comandos ejecutados:  
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql -y
