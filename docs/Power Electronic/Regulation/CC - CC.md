# `docs/Power Electronic/Regulation/CC - CC.md`

# Convertidores CC-CC
En esta sección vamos a tratar el tema de la conversión de corriente continua a corriente continua, visualizando los principales modos de conversión existentes.

## ¿Que es la conversión CC-CC?
la conversión CC-CC se basa en transformar una señal de corriente continua en otra, a un nivel de voltaje diferente. Un ejemplo podría ser convertir una entrada de 12V a una salida de 5V, es decir, un reductor de tensión. Sin embargo, estos circuitos también pueden convertir una señal no regulada, como la presente en la etapa final de un circuito convertidor de AC DC como el de la Figura 1. Por lo tanto, existen tres aplicaciones básicas de un convertidor CC-CC, reducción de voltaje, amplificación de voltaje y regulación de voltaje.

![Regulador de Tensión](/img/power_electronic/Power%20Supply%20Diagram.png)
<br>Figura 1. Diagrama de Bloques de una Fuente de Poder, Adaptado de [1]

## Conversión CC-CC Método Tradicional
La conversión CC-CC tradicional (también conocida como regulación CC-CC Lineal, el nombre de tradicional se lo di yo, el autor, ¿Por qué? porque si) consiste en usar elementos lineales, como resistencias o transistores en la región lineal, para convertir niveles de tensión en otros. Básicamente se comportan como divisores resistivos, en los cuales varía continuamente su resistencia para mantener una tensión de salida constante [2]. El diagrama básico de este dispositivo se ilustra en la Figura 2. En este caso el MOSFET (Leer [MOSFET](/docs/Components/MOSFET.md)) se comporta como una resistencia variable controlada por tensión.

![Conversión CC-CC Lineal](/img/power_electronic/Linear%20CC-CC.png)
<br>Figura 2. Circuito de regulación de Línea básico, Adaptado de [2]

Adicionalmente se puede agregar amplificadores operacionales para aumentar la tensión de salida<sup>1</sup>. Este método auque útil trae consigo un pequeño problema, la pérdida de energía. Al utilizar un divisor resistivo parte de la potencia entregada se disipa en forma de calor siguiendo la famosa ecuación:

```math
P = V\cdot I
```
Por ejemplo, si un convertidor pasa una señal CC de 12V a 5V con una corriente de 100mA la potencia disipada es:

```math
P = (V_{entrada} - V_{salida})\cdot I = (12\text{V} - 5\text{V})\cdot 100\text{mA} = 0.7\text{W}
```

Si lo comparamos con la potencia entregada por la fuente, la cual es 1.2 W, es bastante elevada. ¡Quiere decir que estamos perdiendo el 58% en forma de calor!


<sup>1</sup> <small>No se profundizará en el método de amplificación de tensión, pero se le recomienda al lector leer [Amplificadores Operacionales](). </small>

## Conversión CC-CC por Conmutación

Como vimos uno de los problemas de la conversión tradicional es la pérdida de energía, y en aplicaciones de alta potencia estos consumos resultan significativos. Una de las alternativas que soluciona esto es la conversión CC-CC por Conmutación. Este tipo de conversión consiste en "romper" la onda CC original en una serie de pulsos cuadrados. Esto se consigue utilizando un interruptor, el cual cambia de estado bajo ciertos tiempos de encendido y apagado. Para explicar esto consideremos el diagrama ilustrado en la Figura 3. Cuando el interruptor esta encendido la tensión en la resistencia es exactamente la tensión de entrada, mientras que cuando abrimos el interruptor la tensión de salida es exactamente cero. Este comportamiento causa que la tensión media de la salida dependa del tiempo de encendido y apagado en cada ciclo (suponiendo que se ejecutan de manera periódica). El comportamiento de la señal de salida se ilustra en la Figura 4.

![Conmutación CC-CC](/img/power_electronic/Conmuting%20CC-CC.png)
<br>Figura 3. Diagrama de Conmutación, Adaptado de [3]

![Gráfica de Conmutación CC-CC](/img/power_electronic/time%20conmuting%20CC-CC.png)
<br>Figura 4. Gráfica de salida Conmutación CC-CC, Adaptado de [3]


Uno de los métodos para controlar la tensión de salida emplea la conmutación con una frecuencia constante, es decir, el periodo de los pulsos cuadrados será $`T = t_{on}+t_{off}`$, y lo único que cambiará sera la relación entre los tiempos de encendido y apagado, donde la relación de trabajo del interruptor D se define como la proporción de la duración de encendido con el periodo de conmutación [3]. Este método es conocido como modulación por anchura de pulsos o PWM por sus siglas en inglés.

## Referencias
[1] Sedra si que si

[2] https://www.monolithicpower.com/en/learning/resources/dc-dc-converters-common-types-functionality-parameters-applications

[3] EL loco ese de las conmutaciones