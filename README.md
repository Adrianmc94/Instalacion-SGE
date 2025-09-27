 # 🖥️ Proyecto: Instalación de WordPress en Ubuntu Server

## 📖 Descripción
Este proyecto documenta la instalación y configuración de **WordPress en una máquina virtual con Ubuntu Server**.  
Cada paso incluye capturas de pantalla con el login de **Esemtia** visible para validar la autoría.

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

<img width="1081" height="1000" alt="A" src="https://github.com/user-attachments/assets/1d88266b-a5f8-41d6-a0d0-5f4ee344af6a" />

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

<img width="1327" height="941" alt="3" src="https://github.com/user-attachments/assets/9c168cfb-e622-4c79-8c2c-43fcc4a29514" />

### 🚫 Desactivar la página por defecto de Apache
Apache muestra una página por defecto (“It works!”) si no se configura otro sitio. Para evitar conflictos con WordPress, se desactiva con:
```bash
sudo a2dissite 000-default
sudo service apache2 reload
```

<img width="1253" height="878" alt="4" src="https://github.com/user-attachments/assets/baf3f0e2-9abc-493f-8e3a-91a9db9b7798" />

(Como se ve en la captura para quitar la pagina default primero hay que reiniciar apache, sino nos da el fallo que me aparecía a mi)

### 🗄️ Configuración de la base de datos MySQL
Se crea la base de datos y el usuario necesarios para WordPress.
#### 🔐 Acceder a MySQL como root
```bash
sudo mysql -u root
```
### 🧱 Crear base de datos y usuario
📸 Captura:  
<img width="1320" height="989" alt="6" src="https://github.com/user-attachments/assets/d7219965-5bec-4d9d-a9dc-9cebf2b51759" />

### 🔧 Configurar WordPress para conectar con la base de datos

Se configura el archivo `wp-config.php` para que WordPress pueda conectarse a la base de datos creada.

#### 📁 Copiar archivo de configuración base

```bash
sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
```

### Establecer credenciales de la base de datos:
📸 Captura:  

<img width="1323" height="644" alt="UUUUUUUUUUUU" src="https://github.com/user-attachments/assets/b0a04441-eb06-4a2a-9177-a0c1935d47c2" />

### Editar claves de seguridad:
```bash
sudo -u www-data nano /srv/www/wordpress/wp-config.php
```
📸 Captura:  

<img width="1246" height="921" alt="8" src="https://github.com/user-attachments/assets/92ca3a61-bc01-4a30-bc25-83b3359c9385" />
-Lo eliminamos y lo sus tituimos por el contenido generado desde: 🔗 https://api.wordpress.org/secret-key/1.1/salt/

### ⚙️ Configuración de WordPress

📸 Interfaz principal después de iniciar sesión (ajustes de usuario, actividad, plugins, apariencia, etc.):

![Interfaz WordPress](https://github.com/user-attachments/assets/3a8f325c-e026-4428-9d16-7d9ea48ee3ce)

Aquí vemos la interfaz que nos aparece justo después de loguearnos:

![Dashboard WordPress](https://github.com/user-attachments/assets/ae23fe0c-607e-450b-bbfc-b4cdb8d5dca5)

---

### 🎨 Modificación de apariencia y nuevos plugins

**Temas:**  
Para cambiar el tema:  
`Apariencia → Temas → Añadir tema`, seleccionamos el que más nos guste, clic en **Instalar** y luego **Activar**.  
En este caso se instaló el tema **Extendable**, hecho por Extendify.  

📸 Captura:  
![Tema Extendable](https://github.com/user-attachments/assets/d5a7d549-0f5f-43ed-9652-5993e77f19d5)

**Plugins:**  
Para instalar plugins:  
`Plugins → Añadir plugin`, se sigue el mismo proceso que con los temas.  
En este caso se instaló el plugin **MonsterInsights**.  

📸 Captura:  
![Plugin MonsterInsights](https://github.com/user-attachments/assets/9b0f2890-7acb-43e9-ae4f-f2b4cc0458b7)







