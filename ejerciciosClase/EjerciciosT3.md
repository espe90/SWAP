#Ejercicios Tema 3

**T3.1 Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el enrutamiento del tráfico de un servidor para pasar el tráfico desde una subred a otra.**

En Linux: usamos el comando route. El esquema que se utiliza es el siguiente:

	route operación [tipo] destino enrutador saltos
	
	Ejemplo: route add -net 192.168.1.115 gw 192.168.1.117 dev eth0

En Windows Server existe una herramienta llamada "Enrutamiento y servicio remoto".


**T3.2 Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el filtrado y bloqueo de paquetes.**

En Linux podemos usar las distintas funcionalidades del comando iptables para el filtrado de paquetes.

En Windows lo podemos realizar mediante IPSec.