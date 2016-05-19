#Práctica 4
## Realizada por: Esperanza Jiménez Ávila, Juan Alvarez Carrasco

En la cuarta práctica realizaremos unas pruebas de rendimiento a las opciones de balanceo de carga que se propusieron en la práctica anterior. Para ello utilizaremos los siguientes benchmark.


#Apache Benchmark
El primer benchmark que vamos a usar es el desarrollado por Apache. Lo realizaremos en una de las máquinas donde tenemos instalado Apache server. Lanzaremos el AB de la siguiente forma:

	ab -n 1000 -c 10 http://www.example.com/test.html

En la que se realizan 1000 solicitudes en concurrencias de 10. La URL es la ubicación de nuestro script en el servidor. 

Para calcular la media y la desviación deberemos generar una tabla como la de la siguiente imagen:
![img](https://github.com/espe90/swap/blob/master/practicas/P4/ab.png)
		
Los resultados, ya representados en gráficas, son los siguientes:
![img](https://github.com/espe90/swap/blob/master/practicas/P4/rps_ab.png)
![img](https://github.com/espe90/swap/blob/master/practicas/P4/ttft_ab.png)
![img](https://github.com/espe90/swap/blob/master/practicas/P4/failed_ab.png)

#Siege
Dado que desde nuestra máquina virtual no ha sido posible realizar las oportunas medidas, lo hemos realizado desde windows, con la siguiente orden:

	siege -c10 -d10 -r1 -v http://ip_máquina
	
Para calcular la media y la desviación deberemos generar una tabla como la de la siguiente imagen:

![img](https://github.com/espe90/swap/blob/master/practicas/P4/siege.png)

Los resultados, ya representados en gráficas, son los siguientes:

![img](https://github.com/espe90/swap/blob/master/practicas/P4/elapsed_siege.png)
![img](https://github.com/espe90/swap/blob/master/practicas/P4/transaction_siege.png)
![img](https://github.com/espe90/swap/blob/master/practicas/P4/failed_siege.png)
