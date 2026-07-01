# `docs/Simulations/traditional_conmutation.md`

# Simulación del Circuito Conmutador

En esta sección se presentan los resultados de simulación para el circuito de conmutación tradicional bajo las dos propuestas presentadas por el administrador del repositorio.

*Edit: La matrix cada vez está más cerca. No ya en serio, se han realizado algunas correcciones, las simulaciones anteriores están en la carpeta old (solo imágenes).*

## Conmutación con integrado 555

Este sistema consiste de un circuito oscilador 555 en su configuración Astable (Leer [Oscilador 555](/docs/Components/555.md)), el cual por brevedad no se presentará en una figura como estaba acostumbrado el lector o lectora. Pido perdón, pero debido a temas de presupuesto, y a la complejidad que verá más adelante, espero entienda esta deliberada decisión. En fin, los programas de simulación utilizados son Qucs, Falstad y, por debilidad del administrador, LTspice. Los esquematicos de dichas simulaciones se pueden encontrar en la carpeta de simulaciones, sin embargo, se presenta la lista para mayor agilidad en su acceso:

- Esquemático Qucs:  [Flyback Qucs](/sim/schematics/Conmutation/555/Flyback%20555.sch)
- Esquemático Falstad: [Flyback Falstad](/sim/schematics/Conmutation/555/Flyback%20555.txt)
- Esquemático LTspice: [Flyback LTSpice](/sim/schematics/Conmutation/555/Flyback%20555.asc)

*Edit*: Recientemente el escriba ha obtenido un nuevo programa de simulación, por lo que adicionalmente a los programas de simulación anteriores se cuenta con el uso de MATLAB cuyo esquemático también está disponible en simulaciones:

- Esquemático MATLAB: [Flyback MATLAB](/sim/schematics/Conmutation/555/Flyback.slx)


En las referencias se dejará los diferentes programas, cabe resaltar que Falstad es completamente online.

### Qucs

El primer programa de simulación fue Qucs-S en su versión 25.2.0, cuyo esquemático se presentan en la Figura 1. En este caso se hace uso de dos bobinas acopladas, debido a que el transformador ideal internamente solo funciona como un multiplicador de tensión y esto impide observar el efecto de resonancia con el condensador. La multiplicación de tensión es de aproximadamente 32, esto ya que las bobinas son de $`4\, \text{mH}`$ y $`4\, \text{H}`$ para el primario y secundario respectivamente. El lector o lectora se preguntará el por qué de la resistencia $`R_4`$ con un valor elevado. Anteriormente la simulación presentaba errores de convergencia que no fueron solucionados en el primer intento, sin embargo, al analizar más a fondo se llegó a la conclusión de que la divergencia de la simulación se debía a la falta de una referencia a tierra en la segunda bobina, sin embargo, no es factible poner la tierra directamente en la salida, puesto que no son el mismo nodo, por ello se pone la Resistencia $`R_4`$, la cual permite vincular la tierra con la nueva malla sin alterar de manera significativa el circuito.

![Qucs sim](/sim/img/Conmutation/555/Qucs_esquematic.png)
<br>**Fig. 1.** Esquemático de Qucs-S

Esto nos permite llegar a la gráfica de tensión presentada en la Figura 2 para una simulación de 10ms, en la cual se observa un comportamiento bastante razonable con lo esperado, un análisis con ecuaciones diferenciales sería ideal para dejar de suponer el resultado, si me suben el presupuesto lo haré. Con MATLAB resultaría sencillo.

![Qucs sim res](/sim/img/Conmutation/555/Qucs_esquematic.png)
<br>**Fig. 2.** Simulación de Qucs-S


### Falstad

El segundo programa de simulación fue el Applet Falstad, el cual cuenta con una interfaz muy amigable y una simulación animada. Sin embargo, es limitado en cuando a modificación de los parámetros de cada componente. Ya que contamos con animaciones integradas, he decidido gastar un poco, bastante, de importe personal para poner la ilustración la cual se presenta en la Figura 3. Si por alguna razón el lector siente trabada la animación dejo un pequeño video ([Animación](/sim/img/Conmutation/555/Conmutation_555_animated.mp4)), que por curiosidad, es más ligero que la imagen GIF.


![Falstad sim](/sim/img/Conmutation/555/Conmutation_555_animated.gif)
<br>**Fig. 3.** Simulación Animada en Falstad

Esta simulación en comparación con la antigua tiene algunas correcciones como los valores de inductancia y amplificación del transformador. *Nota: El simulador parece mostrar un valor pico de 487V pero esto es un problema de resolución de la etiqueta ( debido al signo del valor el cual es negativo), si se observa la escala se puede ver claramente un pico de $`\sim 3\,\text{kV}`$. Adicionalmente en la Figura 4 se observa el valor registrado de pico por Falstad.* 

![Falstad sim](/img/misc/peak_voltage_flyback.png)
<br>**Fig. 4.** Tensión Máxima en Falstad *(por obvias razones no puede ser 3.4V)*


### LTspice

El siguiente programa de simulación fue LTspice, en el cual se presentan errores muy extraños. El esquemático se presenta en la Figura 5. Se puede observar un par de bobinas acopladas las cuales tienen una relación de transferencia de 1. Pero esto no es lo extraño, lo extraño es que al intentar simular el comportamiento de este circuito con una inductancia de 4H en el primario se encuentra la simulación de la Figura 6. lo cual es completamente ilógico. Incluso con la inductancia ahí presentada no se encuentran resultados similares en los otros dos programas. No se cual será el problema, le pido al lector o lectora revisar la simulación y mirar si pueden modificar algo. Personalmente LTspice no me agrada, como programa de simulación lo siento muy sobrevalorado y bastante confuso. 

![LTspice sim](/sim/img/Conmutation/555/LT_esquematic.png)
<br>**Fig. 5.** Esquemático en LTspice

![LTspice sim 2](/sim/img/Conmutation/555/LT_error.png)
<br>**Fig. 6.** Resultado de Simulación LTspice


### MATLAB *El padre de todos*

El último programa de simulación fue MATLAB en su versión R2026a, cuyo esquemático se presenta en la Figura 7. Igual que en el caso de Qucs fue necesario poner una resistencia para establecer una referencia a tierra. Personalmente me agrada mucho el programa, la forma de conectar componentes y configurarlos es bastante sencilla. El lector o lectora podrá afirmar que MATLAB se parece a LTspice por el diseño visual, y te tengo que decir, NO. El escriba hizo esto intencionalmente, para que LTspice se pareciera más a MATLAB y así no ponerle tanto rencor.

![MATLAB sim](/sim/img/Conmutation/555/Matlab_esquematic.png)
<br>**Fig. 7.** Esquemático de MATLAB

El resultado de esta simulación para un tiempo de 10ms se presenta en la Figura 8. Se puede observar una alta congruencia con la simulación de Qucs y Falstad, con alguna ligera discrepancia en los picos, posiblemente a los modelos matemáticos internos.

![MATLAB sim](/sim/img/Conmutation/555/Matlab_sim.png)
<br>**Fig. 8.** Simulación en MATLAB



## Conclusiones
Algo es claro, LTspice es un programa para niñas. Formalizando un poco, es cierto que el narrador posee un rencor intrínseco hacia dicho programa, por lo mismo no se intentó corregir el resultado anterior. En cambio en los otros tres programas se llega a un resultado mucho mas coherente y por lo tanto se puede validar el modelo empleado. *¿Quieres cambiar el mundo?, no seas como los demás, no uses LTspice*.


## Referencias

[1] *Qucs Installer* https://ra3xdh.github.io

[2] *Falstad* https://www.falstad.com/circuit/

[3] El muy maldito me bloqueó el acceso

[4] *MATLAB, el único que merece ser temido y adorado*, https://www.mathworks.com/products/matlab.html