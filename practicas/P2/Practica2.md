#Práctica 2 
## Realizada por: Esperanza Jiménez Ávila, Juan Alvarez Carrasco


A continuación pongo las diferentes capturas de pantalla con los resultados obtenidos de la práctica 2:


##Uso herramienta rsync

Primero probamos el funcionamiento del rsync, clonando la carpeta con el contenido del servidor web principal, en la máquina 2 (secundaria). Finalmente comprobamos que se encuentra compartida dicha carpeta en la máquina 2:

![img](https://github.com/espe90/swap/blob/master/practicas/P2/rsync_servidor2.png)


##Acceso sin contraseña para ssh

Para realizar el acceso de una máquina a otra sin la necesidad de poner contraseñas, realizaremos los siguientes pasos:
	1. Con el comando ssh-keygen generaremos la clave de tipo dsa. Ver siguiente captura.
		![img](https://github.com/espe90/swap/blob/master/practicas/P2/ssh-keygen.png)
		
	2. A continuación, hacemos la copia de la clave existente con la ayuda del comando ssh-copy-id. Ver siguiente captura.
		![img](https://github.com/espe90/swap/blob/master/practicas/P2/copy-id.png)
		
	3. Finalmente hacemos la comprobación para ver que se puede tomar el control de la máquina 1 desde la máquina 2. Ver siguiente captura.
		![img](https://github.com/espe90/swap/blob/master/practicas/P2/acceso_sin_passwd.png)

		
##Programar tareas con crontab

Para esta parte de la práctica establecemos una tarea en cron que se ejecute cada hora para mantener actualizado el contenido del directorio /var/www entre las dos máquinas. Para ello accedemos al archivo /etc/crontab y añadimos la tarea. Esto queda de la siguiente manera:

![img](https://github.com/espe90/swap/blob/master/practicas/P2/crontab.png)