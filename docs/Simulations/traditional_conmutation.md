# `docs/Simulations/traditional_conmutation.md`

# Simulación del Circuito Conmutador

En esta sección se presentan los resultados de simulación para el circuito de conmutación tradicional bajo las dos propuestas presentadas por el administrador del repositorio.

## Conmutación con integrado 555

Este sistema consiste de un circuito oscilador 555 en su configuración Astable (Leer [Oscilador 555](/docs/Components/555.md)), el cual por brevedad no se presentará en una figura como estaba acostumbrado el lector o lectora. Pido perdón, pero debido a temas de presupuesto, y a la complejidad que verá más adelante, espero entienda esta deliberada decisión. En fin, los programas de simulación utilizados son Qucs, Falstad y, por debilidad del administrador, LTspice. Los esquematicos de dichas simulaciones se pueden encontrar en la carpeta de simulaciones, sin embargo, se presenta la lista para mayor agilidad en su acceso:

- Esquematico Qucs:  [Flyback Qucs](/sim/schematics/Conmutation/555/Flyback%20555.sch)
- Esquematico Falstad: [Flyback Falstad](/sim/schematics/Conmutation/555/Flyback%20555.txt)
- Esquematico LTspice: [Flyback LTSpice](/sim/schematics/Conmutation/555/Flyback%20555.asc)

En las referencias se dejará los diferentes programas, cabe resaltar que Falstad es completamente online.

### Qucs

El primer programa de simulación fue Qucs-S en su versión 25.2.0, cuyos resultados se presentan en la Figura 1. Aquí se debe poner un inductor en paralelo al transformador, debido a que internamente el transformador solo hace la multiplicación matemática pero no emula el comportamiento de la bobina que lo conforma, y esto es importante, puesto que la bobina es la que hace el intercambio de energía con el condensador produciendo el famoso circuito tanque. Sin embargo, hay un problema. Radica en que por alguna razón, el transformador altera el comportamiento del sistema mostrando esa onda perfectamente cuadrada, lo cual no es teóricamente correcto. Se podría intentar simular un par de inductores acoplados, lo cual sería más preciso, pero por alguna razón que todavía no logro descifrar la simulación arroja error. Parece un error típico de Qucs. Si el lector o lectora puede jugar un poco con el esquemático y puede arreglar el problema le agradecería.

![Qucs sim](/sim/img/Conmutation/555/Qucs_sim.png)
<br>**Fig. 1.** Simulación de Qucs-S

Si se intenta simular el circuito sin el transformador y tomando la tensión en el condensador obtenemos la gráfica de la Figura 2. Lo cual es más congruente con lo esperado, como digo el transformador ideal modifica de algún modo este comportamiento.

![Qucs sim 2](/sim/img/Conmutation/555/Qucs_inductor_sim.png)
<br>**Fig. 2.** Simulación II de Qucs-S

### Falstad

El segundo programa de simulación fue el Applet Falstad, el cual cuenta con una interfaz muy amigable y una simulación animada. Sin embargo, es limitado en cuando a modificación de los parámetros de cada componente. Ya que contamos con animaciones integradas, he decidido gastar un poco de importe personal para poner la ilustración la cual se presenta en la Figura 3. Si por alguna razón el lector siente trabada la animación dejo un pequeño video ([Animación](/sim/img/Conmutation/555/Conmutation_555_animated.mp4)), que por curiosidad, es más ligero que la imagen GIF.


![Falstad sim](/sim/img/Conmutation/555/Conmutation_555_animated.gif)
<br>**Fig. 3.** Simulación Animada en Falstad

Esta simulación muestra mayor afinidad a la realidad, sin embargo, para corroborar el comportamiento de Qucs-S se realizó una simulación solo con la bobina de 4H, el resultado se ilustra en la Figura 4. Por temas de habilidad con el manejo de la interfaz no pude mostrar los valores en los cuales oscilaba, sin embargo, el lector o lectora pueden corroborar la similitud entre programas de simulación.

![Falstad sim 2](/sim/img/Conmutation/555/Falstad_inductor_sim.png)
<br>**Fig. 4.** Simulación II en Falstad

### LTspice

El último programa de simulación fue LTspice, en el cual se presentan errores muy extraños. El esquemático se presenta en la Figura 5. Se puede observar un par de bobinas acopladas las cuales tienen una relación de transferencia de 1. Pero esto no es lo extraño, lo extraño es que al intentar simular el comportamiento de este circuito con una inductancia de 4H en el primario se encuentra la simulación de la Figura 6. lo cual es completamente ilógico. Incluso con la inductancia ahí presentada no se encuentran resultados similares en los otros dos programas. No se cual será el problema, le pido al lector o lectora revisar la simulación y mirar si pueden modificar algo. Personalmente LTspice no me agrada, como programa de simulación lo siento muy sobrevalorado y bastante confuso. 

![LTspice sim](/sim/img/Conmutation/555/LT_esquematic.png)
<br>**Fig. 5.** Esquemático en LTspice

![LTspice sim 2](/sim/img/Conmutation/555/LT_error.png)
<br>**Fig. 6.** Resultado de Simulación LTspice

## Conclusiones
Algo es claro, las simulaciones difieren en los tres programas, sin embargo, pueden ser problemas relacionados al bajo entendimiento del funcionamiento de spice a nivel interno de cada programa. Recomiendo utilizar más alternativas como Microcap para corroborar resultados. Por mi parte intentaré realizar correcciones a este circuito y actualizaré el repositorio si llego a un resultado más coherente entre los tres programas. Agradezco al lector o lectora por la paciencia, espero tome estas simulaciones como preliminares.


## Referencias

[1] *Qucs Installer* https://ra3xdh.github.io

[2] *Falstad* https://www.falstad.com/circuit/

[3] El muy maldito me bloqueó el acceso