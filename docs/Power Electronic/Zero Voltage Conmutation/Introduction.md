# `docs/Zero Voltage Conmutation/Introduction.md`

# Introducción a la Conmutación a Cero Voltios
En esta sección se analizará el comportamiento de la conmutación a cero voltios, se recomienda haber leído previamente la sección [Conversión CC-CC](/docs/Power%20Electronic/Regulation/CC%20-%20CC.md).

## ¿Qué es la conmutación a cero voltios?
Al igual que el caso de la conmutación CC-CC convencional, la conmutación a cero voltios es una forma de conversión de corriente continua en el cual se transmite la potencia en forma de pulsos cuadrados, sin embargo, la principal diferencia es que los tiempos de encendido, y por lo tanto las frecuencias de conmutación, son variables dejando los tiempos de apagado fijos [1]. Otra de las principales diferencias es que cuenta con transiciones de conmutación resonantes lo que permite reducir las perdidas de conmutación a prácticamente cero.

## Antes de
Para llegar de manera orgánica al circuito base para la conmutación de cero voltios (ZVS por sus siglas en ingles) debemos primero analizar algunas configuraciones previas.

## Multi Vibrador Biestable

En eléctronica el biestable es un circuito multivibrador que, como su nombre lo indica, tiene dos estados estables y puede almacenar energía [2]. Los circuitos biestables tienen la capacidad de permanecer en uno de dos estados posibles durante un tiempo indefinido en ausencia de perturbaciones. Para ilustrar esto vamos a considerar el circuito de la Figura 1.
Supongamos que los dos interruptores $`S_1`$ y $`S_2`$ estan inicialmente abiertos, y que los dos transistores son NMOS<sup>1</sup>. Al inicio ambos transistores van a conducir, puesto que la tensión en el terminal de base de cada uno de ellos es positiva.

![Biestable](/img/Flip%20Flop/Biestable.png)

Figura 1. Circuito Biestable.




<sup>1</sup><small>En la construcción del diagrama no se logró interpretar el tipo de construcción del NMOS, adicionalmente se le recomienda al lector leer [MOSFET](/docs/Components/MOSFET.md).</small>



## Referencias
[1] El texas https://www.ti.com/lit/an/slua159/slua159.pdf?ts=1781501340035
[2] https://es.wikipedia.org/wiki/Biestable