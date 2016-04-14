#Ejercicios Tema 4

**T4.1 Buscar información sobre cuánto costaría en la actualidad un mainframe. Comparar precio y potencia entre esa máquina y una granja web de unas prestaciones similares.**

Como podemos leer en el siguiente artículo que adjunto, en 2015 se presento un nuevo modelo de IBM donde el precio de la versión más baja ronda los 200.000$ 
[http://www.ticbeat.com/tecnologias/ibm-reinventa-el-mainframe-en-la-era-movil-z13/]


**T4.2: Buscar información sobre precio y características de balanceadores hardware específicos. Compara las prestaciones que ofrecen unos y otros.**

	**BBF240A Barracuda Load Balancer 240 Appliance**
	Manufacturer    Barracuda Networks
	Video   No
	Maximum Throughput  95 Mbps
	Servers Support 10
	SSL Offloading/Acceleration No
	Features    No
	Precio $1,424.05

	**BBF643A Barracuda Load Balancer 640 ADC w/ 8 1GbE NICs**
	Manufacturer	Barracuda Networks
	Video   No
	Maximum Throughput  4 Gbps
	Servers Support 250
	SSL Offloading/Acceleration 15,000 TPS
	Features    No
	Precio $12,000
	
	
**T4.3: Buscar información sobre los métodos de balanceo que implementan los dispositivos recogidos en el ejercicio 4.2.**

Según la documentación de Barracuda: Barracuda Load Balancer utiliza algoritmos Round Robin, de ponderación y el basado en menos números de conexiones.

Sacado del siguiente pdf [https://www.barracuda.com/assets/docs/datasheets/barracuda_load_balancer_ds_us.pdf]


**T4.4: Instala y configura en una máquina virtual el balanceador ZenLoadBalancer. Compara con la dificultad de la instalación y configuración usando nginx o haproxy (práctica 3).**


**T4.5: Probar las diferentes maneras de redirección HTTP. ¿Cuál es adecuada y cuál no lo es para hacer balanceo de carga global? ¿Por qué?**

*Redirección 301:* Es permanente. Esto le indica a los buscadores que ignoren la dirección original e indexen la nueva dirección. Este tipo de redirección se utiliza cuando estamos cambiando de dominio a una web.

*Redirección 302:* Es temporal. Esto indica que la dirección original no ha cambiado y se seguirá utilizando pero temporalmente cambiaremos de dirección.

En mi opinión, la adecuada es la 302 ya que sería posible redirigir el tráfico a diferentes direcciones temporales y no una permanente, la cuál también la actualizan navegadores.


**T4.6: Buscar información sobre los bloques de IP para los distintos países o continentes. Implementar en JavaScript o PHP la detección de la zona desde donde se conecta un usuario.**

Las direcciones IPs se reparten en bloques entre los distintos paises. Existen diversas bases de datos que identifican que país está en cada bloque. En la siguiente página se encuentra un scrip en .php para detectar nuestro IP y país: [http://chir.ag/projects/geoiploc] El código es el siguiente:

	<?php

	  include("geoiploc.php"); // Must include this

	  // ip must be of the form "192.168.1.100"
	  // you may load this from a database
	  $ip = $_SERVER["REMOTE_ADDR"];
	  echo "Your IP Address is: " . $ip . "<br />";

	  echo "Your Country is: ";
	  // returns country code by default
	  echo getCountryFromIP($ip);
	  echo "<br />\n";

	  // optionally, you can specify the return type
	  // type can be "code" (default), "abbr", "name"

	  echo "Your Country Code is: ";
	  echo getCountryFromIP($ip, "code");
	  echo "<br />\n";

	  // print country abbreviation - case insensitive
	  echo "Your Country Abbreviation is: ";
	  echo getCountryFromIP($ip, "AbBr");
	  echo "<br />\n";

	  // full name of country - spaces are trimmed
	  echo "Your Country Name is: ";
	  echo getCountryFromIP($ip, " NamE ");
	  echo "<br />\n";

	?>

	
**T4.7: Buscar información sobre métodos y herramientas para implementar GSLB.**

GSLB se basa en técnicas como la redirección de DNS, redirección HTTP, RHI, etc. para conseguir su objetivo. Normalmente GSLB se configura en la configuración del centro de datos activo-activo o configuración activo-standby. En configuración activo-activo las solicitudes de los clientes se equilibra su carga a través de los centros de datos activos. En configuración activo-standby, el centro de datos de espera entra en funcionamiento, sólo en el fracaso del centro de datos activo.