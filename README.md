# 🖥️ Proyecto: Instalación de WordPress en Ubuntu Server

## 📖 Descripción
Este proyecto documenta la instalación y configuración de **WordPress en una máquina virtual con Ubuntu Server**.  
Cada paso incluye capturas de pantalla con el login de **Esemtia** visible para validar la autoría.

---

## 🛠️ Pasos realizados

### Instalación de Ubuntu Server en la máquina virtual
- Descarga de la ISO de Ubuntu Server.  
- Creación de la máquina virtual.  
- Configuración básica (idioma, teclado, red).  

📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)

---

### Instalación de entorno gráfico en el Servidor
Comando: ```sudo apt install ubuntu-desktop -y```


### Instalación de los paquetes necesarios
Comandos ejecutados:  
```
sudo apt update && sudo apt upgrade -y<img width="1297" height="1199" alt="1" src="https://github.com/user-attachments/assets/c810c28e-9c8e-4057-bb1c-cd2ba44f48fe" />

````

### Instalación de dependencias necesarias
Para preparar el entorno de WordPress, se instalan Apache, MySQL, PHP y varias extensiones recomendadas.<br>
📸 Captura:

<img width="1297" height="1199" alt="1" src="https://github.com/user-attachments/assets/49c76e14-8e05-4b60-b02c-6745b0dd61ff" />

### 📦 Instalación de WordPress

Se instala WordPress manualmente desde [wordpress.org](https://wordpress.org), en lugar de usar el paquete de Ubuntu, para evitar problemas y obtener la versión más actualizada.

#### 📁 Crear directorio y descargar WordPress
```bash
sudo mkdir -p /srv/www
sudo chown www-data: /srv/www
curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
```

<img width="1392" height="515" alt="2" src="https://github.com/user-attachments/assets/1a28f1f4-26db-427a-87b3-ec6b84a5617b" />


### ⚙️ Configuración de Apache para WordPress

Se crea un sitio en Apache para alojar WordPress.

#### 📝 Crear archivo de configuración

```bash
sudo nano /etc/apache2/sites-available/wordpress.conf
```
📸 Captura del contenido del archivo:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)


### Activar configuración
📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)


### 🚫 Desactivar la página por defecto de Apache
Apache muestra una página por defecto (“It works!”) si no se configura otro sitio. Para evitar conflictos con WordPress, se desactiva con:
```bash
sudo a2dissite 000-default
sudo service apache2 reload
```

### 🗄️ Configuración de la base de datos MySQL
Se crea la base de datos y el usuario necesarios para WordPress.
#### 🔐 Acceder a MySQL como root
```bash
sudo mysql -u root
```
📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)


### 🧱 Crear base de datos y usuario
📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)

### 🔧 Configurar WordPress para conectar con la base de datos

Se configura el archivo `wp-config.php` para que WordPress pueda conectarse a la base de datos creada.

#### 📁 Copiar archivo de configuración base

```bash
sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
```
📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)

### Establecer credenciales de la base de datos:
📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)

### Editar claves de seguridad:
```bash
sudo -u www-data nano /srv/www/wordpress/wp-config.php
```
### Captura del contenido del archivo que hay que eliminar abierto en nano: 
📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)

-Lo eliminamos y lo sus tituimos por el contenido generado desde: 🔗 https://api.wordpress.org/secret-key/1.1/salt/
📸 Captura:  
![Instalación Ubuntu](screenshots/01-instalacion-ubuntu.png)



