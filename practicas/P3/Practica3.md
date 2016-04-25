#Práctica 3 
## Realizada por: Esperanza Jiménez Ávila, Juan Alvarez Carrasco


Esta práctica consiste en instalar dos balanceadores de carga, Nginx y HaProxy. Una vez montadas los dos servidores de la práctica 2, procedemos a crear una nueva máquina balanceador, que se encargará que realizar esta función.

A continuación mostramos las capturas de la configuración y puesta en marcha de cada uno de los balanceadores, para ver su correcto funcionamiento.


##Nginx

Una vez instalado en nuestra máquina, tal y como se indicaba en el guión de práctica:
Importamos la clave del repositorio de software.
	cd /tmp/
	wget http://nginx.org/keys/nginx_signing.key
	apt-key add /tmp/nginx_signing.key
	rm -f /tmp/nginx_signing.key
	
Añadimos el repositorio al final del archivo **/etc/apt/sources.list**, mediante alguna de las siguientes ordenes.
	echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list
	echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list
	
Una vez realizado esto configuramos el archivo **/etc/nginx/conf.d/default.conf** para que actue como en realidad nosotros queremos:

![img](https://github.com/espe90/swap/blob/master/practicas/P3/ConfigNginx.png)


A continuación solo queda comprobar que el balanceador nginx funciona correctamente:

![img](https://github.com/espe90/swap/blob/master/practicas/P3/BalanceoNGINX.png)



##HaProxy

Una vez instalado en nuestra máquina, tal y como se indicaba en el guión de práctica:

Modificamos el archivo **/etc/haproxy/haproxy.cfg**.
![img](https://github.com/espe90/swap/blob/master/practicas/P3/ConfigHaproxy.png)


A continuación solo queda comprobar que el balanceador nginx funciona correctamente:
![img](https://github.com/espe90/swap/blob/master/practicas/P3/BalanceoHaproxy.png)
		
