#Pr·ctica 2 
## Realizada por: Esperanza JimÈnez ¡vila, Juan Alvarez Carrasco


Esta pr·ctica consiste en instalar dos balanceadores de carga, Nginx y HaProxy. Una vez montadas los dos servidores de la pr·ctica 2, procedemos a crear una nueva m·quina balanceador, que se encargar· que realizar esta funciÛn.

A continuaciÛn mostramos las capturas de la configuraciÛn y puesta en marcha de cada uno de los balanceadores, para ver su correcto funcionamiento.


##Nginx

Una vez instalado en nuestra m√°quina, tal y como se indicaba en el gui√≥n de pr√°ctica:
Importamos la clave del repositorio de software.
	cd /tmp/
	wget http://nginx.org/keys/nginx_signing.key
	apt-key add /tmp/nginx_signing.key
	rm -f /tmp/nginx_signing.key
	
A√±adimos el repositorio al final del archivo **/etc/apt/sources.list**, mediante alguna de las siguientes ordenes.
	echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list
	echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list
	
Una vez realizado esto configuramos el archivo **/etc/nginx/conf.d/default.conf** para que actue como en realidad nosotros queremos:

![img](https://github.com/espe90/swap/blob/master/practicas/P3/ConfigNginx.png)


A continuaci√≥n solo queda comprobar que el balanceador nginx funciona correctamente:

![img](https://github.com/espe90/swap/blob/master/practicas/P3/BalanceoNGINX.png)



##HaProxy

Una vez instalado en nuestra m√°quina, tal y como se indicaba en el gui√≥n de pr√°ctica:

Modificamos el archivo **/etc/haproxy/haproxy.cfg**.
![img](https://github.com/espe90/swap/blob/master/practicas/P3/ConfigHaproxy.png)


A continuaci√≥n solo queda comprobar que el balanceador nginx funciona correctamente:
![img](https://github.com/espe90/swap/blob/master/practicas/P3/BalanceoHaproxy.png)
		
