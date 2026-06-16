# `docs/Zero Voltage Conmutation/Introduction.md`

# Introducción a la Conmutación a Cero Voltios
En esta sección se analizará el comportamiento de la conmutación a cero voltios, se recomienda haber leído previamente la sección [Conversión CC-CC](/docs/Power%20Electronic/Regulation/CC%20-%20CC.md).

## ¿Qué es la conmutación a cero voltios?
Al igual que el caso de la conmutación CC-CC convencional, la conmutación a cero voltios es una forma de conversión de corriente continua en el cual se transmite la potencia en forma de pulsos cuadrados, sin embargo, la principal diferencia es que los tiempos de encendido, y por lo tanto las frecuencias de conmutación, son variables dejando los tiempos de apagado fijos [1]. Otra de las principales diferencias es que cuenta con transiciones de conmutación resonantes lo que permite reducir las perdidas de conmutación a prácticamente cero.

## Antes de
Para llegar de manera orgánica al circuito base para la conmutación de cero voltios (ZVS por sus siglas en ingles) debemos primero analizar algunas configuraciones previas.

## Multi Vibrador Biestable

En eléctronica el biestable es un circuito multivibrador que, como su nombre lo indica, tiene dos estados estables y puede almacenar energía [2]. Los circuitos biestables tienen la capacidad de permanecer en uno de dos estados posibles durante un tiempo indefinido en ausencia de perturbaciones. Para ilustrar esto vamos a considerar el circuito de la Figura 1.
Supongamos que los dos interruptores $`S_1`$ y $`S_2`$ estan inicialmente abiertos, y que los dos transistores son NMOS<sup>1</sup>. Al inicio ambos transistores van a conducir, puesto que la tensión en el terminal de compuerta de cada uno de ellos es positiva. Debido a las diferencias de fabricación de los dos transistores uno de ellos va a conducir antes o más rápido que el otro, para nuestro caso supongamos que el transistor $`Q_1`$ conduce primero<sup>2</sup>. Al conducir $`Q_1`$ la tensión $`V_{DS}`$ de dicho transistor se va reduciendo rápidamente, debido a que al aumentar la corrienta la mayor caída de voltaje sucede en la resistencia $`R_1`$. Como no existen corrientes por las resistencias $`R_3`$ y $`R_4`$ (leer encarecidamente [MOSFET](/docs/Components/MOSFET.md)) la tensión $`V_{GS}`$ del transistor $`Q_2`$ es igual a la tensión $`V_{DS}`$ del transistor $`Q_1`$, y por lo tanto también está disminuyendo. Al reducir la tensión en la compuerta de $`Q_{2}`$ este va a ir reduciendo su conducción continuamente hasta que llegue un punto donde toda la tensión de la fuente caiga en el terminal de drenaje, puesto que al no conducir no habrá corriente y por lo tanto no habrá caída de tensión en $`R_2`$. En este punto se alcanza uno de los estados estables del circuito de manera indefinida, puesto que por sí solo no hay forma que el transistor $`Q_2`$ vuelva a conducir de nuevo.

![Biestable](/img/Flip%20Flop/Biestable.png)
<br>Figura 1. Circuito Biestable.

Para pasar al segundo estado biestable supongamos que se cierra y se abre el interruptor $`S_1`$. Al hacerlo la tensión en la compuerta de $`Q_1`$ cae a 0, por lo que esté ya no puede conducir obligando a que no haya caída de tensión en la resistencia $`R_1`$ (debido a que no hay corriente) y que toda la tensión caiga en $`V_{DS}`$. Esto activa la conducción en el transistor $`Q_2`$ y como este ahora empieza a reducir la tensión en la compuerta de $`Q_2`$ lo inahilita llegando al segundo estado estable del circuito. Para repetir el proceso simplemente se cierrra y se abre el interruptor $`S_2`$ para volver al otro estado estable. Existen maneras más automáticas de cambiar entre estados como el ilustrado en la Figura 2, en este caso al entregar un pulso por el nodo T se fuerza a los transistores a cambiar de estado, puesto que los condensadores se oponen al cambio brusco y provocan que el cambio se observe en los terminales de compuerta de los transistores <sup>3</sup>.

![Biestable](/img/Flip%20Flop/Biestable%20Reset.png)
<br>Figura 2. Circuito Biestable con Entrada de Reset.



### _____________________________________________
<sup>1</sup><small> En la construcción del diagrama no se logró interpretar el tipo de construcción del NMOS, adicionalmente se le recomienda al lector leer [MOSFET](/docs/Components/MOSFET.md).</small>

<sup>2</sup><small> En la Figura 1 $Q_1$ es el de la izquierda y $`Q_2`$ el de la derecha, pido disculpas al lector o lectora por el error</small>

<sup>3</sup><small> El lector o lectora se podrá extrañar de que en la Figura 2 se presenten las nomenclaturas de manera correcta, debido a temas de presupuesto esto no fue implementado en la Figura 1. Adicionalmente el diseño con condensadores tiene un comportamiento ligeramente diferente que por brevedad no será explicado.</small>


## Multi Vibrador Astable
A diferencia del anterior el astable no posee estados estables, ojo, esto no quiere decir que no tenga estados, sino que los estados que posee no mantienen estabilidad y cambiar continuamente entre ellos [3]. Aunque parezca algo novedoso el esquema es similar al usado en el biestable. Empecemos con el análisis.

 *Nota del autor: Acabo de leer mi explicación y admito que es bastante confusa. Me disculpo por ello. Recomiendo al lector o lectora que a la par de la explicación se observe la animación de la Figura 4 para mayor entendimiento. Si me aumentan el presupuesto animaré también el biestable y el ZVS.*

Consideremos el circuito de la Figura 3, a simple vista parece complicado pero vamos a ir paso por paso. Al igual que el caso anterior al inicio uno de los transistores va a conducir antes que el anterior debido a las condiciones físicas con las que fueron construidos. Supongamos que $`Q_1`$ es el que empieza a conducir. Esto provoca que la tensión $`V_{DS}`$ caiga rápidamente a cero. El condensador $`C_{1}`$<sup>4</sup>, cuya diferencia de potencial es cero, al ver este cambio rápido de tensión no experimenta directamente el cambio instantáneo de tensión si no que lo pasa al resistor $`R_6`$, me refiero a que como el condensador se opone a los cambios bruscos de tensión su voltaje permanece constante, sin embargo, para que se cumpla la ley de tensiones de Kirchoff es necesario que la tensión en la resistencia $`R_6`$ caiga por debajo de 0 V, un poco por arriba de $`-V_{in}`$. Al caer dicha tensión se bloquea el transistor $`Q_2`$ puesto que acabamos de alimentar la tensión de la compuerta por debajo del umbral. Esto a simple vista parece el estado estable de la etapa anterior, sin embargo, no lo es. Al tener el condensador $`C_{1}`$ con el terminal izquierdo a tierra, puesto que el votaje $`V_{DS}`$ es cero, el condensador empieza a cargarse a través de la resistencia $`R_2`$. Al cargarse el condensador estamos aumentando la tensión de la compuerta del transistor $`Q_2`$ hasta que llega un punto en que esta supera la tensión de umbral activando el transistor $`Q_2`$. Al activarse, la tensión $`V_{DS}`$ cae rápidamente a cero, y el condensador $`C_2`$ ante este cambio abrupto hace que la tensión en la resistencia $`R_5`$ caiga a valores negativos bloqueando el transistor $`Q_1`$. Al crear un nodo a tierra en el terminal izquierdo del condensador $`C_2`$ este empieza a cargarse a través de la resistencia $`R_3`$. Una vez se carga vuelve a activar el transistor $`Q_1`$ al aumentar su voltaje de compuerta repitiendo el ciclo <sup>5</sup>. 

![Circuito Astable](/img/Flip%20Flop/Astable.png)
<br> Figura 3. Circuito Astable.

![Animación Astable](/img/Flip%20Flop/Astable%20animated.gif)
<br> Figura 4. Animación de Funcionamiento del Circuito Astable.

### _____________________________________________
<sup>4</sup><small> Aunque aumentó el presupuesto entre imagenes se presentan pequeños errores ocasionales. En este caso el condensador $C_1$ es el que está marcado como $`C_!`$</small>

<sup>5</sup><small> El modelo original del oscilador astable usa transistores BJT los cuales permiten flujos de corriente por el terminal de Base prescindiendo así de las resistencias $R_5$ y $`R_6`$</small>

### Conmutación a Cero Voltios
En este punto el lector o lectora estará en duda del por qué presente las dos configuraciones anteriores. Resulta que el ZVS es una modificación de un oscilador astable. El diseño más común que se puede encontrar sobre este circuito es el diseñado por Mazilli.

## Referencias
[1] El texas https://www.ti.com/lit/an/slua159/slua159.pdf?ts=1781501340035
[2] https://es.wikipedia.org/wiki/Biestable
[3] https://es.wikipedia.org/wiki/Astable