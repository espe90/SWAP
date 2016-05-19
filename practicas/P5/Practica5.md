#Práctica 5
## Realizada por: Esperanza Jiménez Ávila, Juan Alvarez Carrasco

En esta práctica realizaremos la creación de copias de seguridad de las bases de datos en MySQL. Dichas copias la realizaremos con mysqldump y las restauraremos en la segunda máquina. Estos pasos se automatizarán gracias a una configuración maestro-esclavo.

#Creación de base de datos
Lo primero que debemos hacer es acceder a MySQL desde la máquina 1. Esto lo hacemos con:

	mysql -uroot -p 

Una vez hecho esto, creamos la base de datos que se llamará contactos.sql e introducimos un valor, de la siguiente manera:
	
	create database contactos;
	use contactos;
	create table datos(nombre varchar(100),tlf int);
	insert into datos(nombre,tlf) values ("pepe",95834987);

Quedando de la siguiente manera:
![img](https://github.com/espe90/swap/blob/master/practicas/P5/tabla.png)

#Replicación de la BD con mysqldump	
A continuación, con el uso del siguiente comando, copiaremos desde la máquina principal (1) a la máquina secundaria (2) los datos que hay almacenados en la BD:
![img](https://github.com/espe90/swap/blob/master/practicas/P5/CopiaSSH.png)

#Replicación de la BD mediante una configuración maestro-esclavo
En la máquina principal, editamos el fichero /etc/mysql/my.cnf. Comentamos el parámetro de bind-address. Le indicamos un fichero para la generación de errores si no está creado por defecto, establecemos server-id = 1 y descomentamos log_bin. Guardamos y reiniciamos el servicio MySQL.

Pasamos a la segunda máquina y volvemos a editar el fichero /etc/mysql/my.cnf. Pondremos lo mismo que en el anterior salvo server-id que será 2.

Pasamos a la primera máquina y entramos en MySQL para crear un usuario que posea permisos de replicación. Debemos introducir lo siguiente:

	CREATE USER esclavo IDENTIFIED BY 'esclavo';
	GRANT REPLICATION SLAVE ON *.* TO 'esclavo'@'%' IDENTIFIED BY 'esclavo';
	FLUSH PRIVILEGES;
	FLUSH TABLES;
	FLUSH TABLES WITH READ LOCK;
	SHOW MASTER STATUS;
	
Una vez hecho esto, accedemos de nuevo al MySQL de la segunda máquina (esclava). Introduciremos la IP del maestro, su puerto, el usuario, la contraseña, el fichero de la base de datos y su posición. En nuestro caso sería así:
![img](https://github.com/espe90/swap/blob/master/practicas/P5/MysqlESCLAVOS.png)

Para asegurarnos que está funcionando de forma correcta introduciremos el siguiente comando y comprobaremos que el valor de Second_Behind_Master es distinto de "null".

	SHOW SLAVE STATUS\G 

![img](https://github.com/espe90/swap/blob/master/practicas/P5/EsclavosOK.png)

Como última comprobación, insertamos una tupla nueva en la máquina maestro y comprobaremos que se replica en el esclavo.

![img](https://github.com/espe90/swap/blob/master/practicas/P5/m1CreaDatosNuevos.png)
![img](https://github.com/espe90/swap/blob/master/practicas/P5/m2ConDatosNuevos.png)

