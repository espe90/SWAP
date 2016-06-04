#Práctica 6
## Realizada por: Esperanza Jiménez Ávila, Juan Alvarez Carrasco

En esta práctica configuraremos dos discos en RAID 1 por software, usando una máquina vírtual con Ubuntu 12.04 server. 

#Configuración de RAID 1 en Ubuntu Server mediante software 
Instalamos mdadm que es el software encargado de la configuración de discos duros RAID:
		sudo apt-get install mdadm

Debemos buscar la información (identificación asignada por Linux) de ambos discos:
		sudo fdisk -l
		
![img](https://github.com/espe90/swap/blob/master/practicas/P6/fdisk.png)
		
Ahora ya podemos crear el RAID 1, usando el dispositivo /dev/md0, indicando el número de dispositivos a utilizar (2), así como su ubicación:
		sudo mdadm -C /dev/md0 --level=raid1 --raid-devices=2 /dev/sdb /dev/sdc

Le aplicamos formato al sistema RAID 1 creado mediante:
		sudo mkfs /dev/md0
		
Creamos el directorio donde se montará el sistema RAID y lo montamos.
		sudo mkdir /datos
		sudo mount /dev/md0 /datos	
		
Como método de comprobación para saber si el RAID se realizó correctamente ejecutaremos lo siguiente:
		sudo mdadm --detail /dev/md0

![img](https://github.com/espe90/swap/blob/master/practicas/P6/detail.png)


#Automatización del RAID 1
La automatización del montaje del RAID al inicio del sistema es muy sencillo. Editamos el fichero /etc/fstab y añadimos la siguiente línea para que se monte de forma automática.
	/dev/md0 /datos ext2 noatime,rw 0 0
	
Reiniciamos la máquina y ya debería montarse el RAID de forma automática.

#Simulación de un fallo en un disco RAID, comprobar su funcionamiento sin él y repararlo
Vamos a generar un fallo en el RAID. Lo produciremos en el disco sdb.
		mdadm --manage --set-faulty /dev/md0 /dev/sdb
		
Por tanto este disco lo eliminamos con el siguiente comando para que el RAID desaparezca y el disco duro sdc sea funcional.
		mdadm --remove /dev/md0 /dev/sdb

Y por último, podemos añadir, también “en caliente”, un nuevo disco que vendría a reemplazar al disco que hemos retirado:
		sudo mdadm --manage --add /dev/md0 /dev/sdb
	
![img](https://github.com/espe90/swap/blob/master/practicas/P6/simulacion.png)