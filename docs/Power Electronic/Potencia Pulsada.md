# `docs/Potencia Pulsada.md`

# Potencia Pulsada

## Descripción

La potencia pulsada es un sistema donde la energía almacenada se descarga como energía eléctrica en una carga en un pulso o en una serie de ellos con una tasa de repetición controlada. Básicamente la potencia pulsada busca entregar la mayor cantidad de energía en el menor tiempo posible, y debido a que:

```math
P = \frac{dE(t)}{dt}
```

La potencia entregada a la carga resulta ser usualmente muy alta, rondando los valores de Gigavatios ( $`10^9`$ W).

## Fases de Generación

En general los sistemas de potencia pulsada constan de las siguientes fases:

- Fuente de alimentación: se encarga de alimentar el generador, usualmente es DC.
- Almacenamiento de Energía: como su nombre lo indica permite el almacenamiento de energía.
- Formación del Pulso: en esta fase se busca realizar la forma que será recibida por la carga.
- Carga: el circuito al que se desea que reciba el pulso de alta potencia.

## Almacenamiento de Energía

Una de las fases más esenciales al momento de diseñar un sistema de potencia pulsada, ya que en base a esta se logran determinar las demás caracteristicas del sistema, y en general toda la eficiencia del sistema. Los métodos de almacenamiento más comunes se presentan a continuación:

### Condensadores

El sistema más utilizado de almacenamiento es el del banco de condensadores, debido a su prácticidad y escalabilidad. 

### Inductores

El sistema de inductores resulta más laborioso, debido que para mantener la energía almacenada en el inductor se debe tener una corriente circulando por el mismo. A diferencia del condensador que puede mantener su carga de manera prolongada.

### Mecánicos

Estos sistemas generalmente aprovechan la inercia para almacenar la energía. Un ejemplo común es el volante de inercia, sin embargo, cuentan con la desventaja de ser complicados para generar pulsos rápidos.

### Químicos

Estos sistemas resultan familiares para varios: baterías. Existen reacciones interesantes entre estos componentes que pueden generar grandes desprendimientos de energía. Sin embargo, conllevan a posibles riesgos si no se cuenta con la debida experiencia.


## Variables de Interés

En potencia pulsada existen ciertas variables que resultan importantes en el estudio de pulsos de alta potencia. Las cuales son:

- Amplitud Pico: es sencillamente el valor máximo del pulso.

- Anchura a media Altura (FWHM): conocido vulgarmente como duración, determina la distancia (en su unidad correspondiente) entre los puntos donde su valor es la mitad de su valor máximo.

- Tiempo de subida: conocido vulgarmente como rise_time, no hay reclamos en este caso, determina la diferencia de tiempo en el cual el valor pasa del 10% al 90% del valor máximo.


## Sistema RC

Una de las maneras de almacenar energía de manera efectiva es un banco de condensadores, debido a que pueden entregar gran parte de su energía almacenada en poco tiempo, pueden mantener la energía por mucho tiempo, y son más económicos que los otros sistemas de almacenamiento. Por eso, es coveniente explicar la matemática que hay detrás de este sistema.

En general, un sistema de almacenamiento de condensadores tiene todos sus componentes conectados en paralelo, logrando que se carguen todos a la misma tensión. A cada condensador se le conoce como etapa. Se puede realizar un esquema equivalente como sigue:

![Circuito RC](/img/pulse_power/rc.png)

En donde $`V_0`$ representa la tensión de la fuente que carga el sistema. Se puede observar que al cerrar el interruptor el circuito resultante es un circuito RC. Sabemos que la relación de tensión y corriente para un condensador es:

```math
i_c(t) = C\frac{d v_c(t)}{dt}
```

Por lo que al aplicar la ley de tensiones de Kirchoff (solo considerando el circuito RC) quedaría:

```math
i\cdot R + \frac{1}{C} \int{i(t)\,dt} = 0
```

Al aplicar el operador lineal "derivada" a ambos de la ecuación quedaría:

```math
R\cdot \frac{d i(t)}{dt} + \frac{1}{C}\cdot i(t) = 0
```

Manipulando para conseguir un ecuación "mónica":

```math
\frac{d i(t)}{dt} + \frac{1}{RC}\cdot i(t) = 0
```

Es sencillo ver que las soluciones a esta ecuación diferencial son de la forma:

```math
i(t) = K\cdot e^{-\frac{t}{RC}}
```

Si lo que nos interesa es la tensión en la resistencia simplemente multiplicamos la corriente por el valor de tensión:

```math
V_R(t) = K_2 \cdot e^{-\frac{t}{RC}}
```

Para hallar la constante podemos observar que el condensador quedo cargado a la tensión de la fuente $V_0$, por lo que no es difícil ver que:

```math
 V_R(t) = V_0 \cdot e^{-\frac{t}{RC}}
```

Al producto $`R\cdot C`$ lo denominaremos con el símbolo $`\tau`$ (tau), y lo llamaremos tiempo de extinción. Si estuvieramos interesados en hallar el FWHM sencillamente debemos considerar el tiempo que se demora a llegar a la mitad de tensión, es decir:

```math
 V_R(t_{fwhm}) = \frac{V_0}{2}
```

Para ello observemos que para que esto ocurra se debe cumplir que:

```math
e^{-\frac{t_{fwhm}}{\tau}} = 0.5
```

Despejando $t_{fwhm}$:

```math
 t_{fwhm} = \ln{2}\cdot \tau
 ```


## Inducción Electromagnética

Sabemos gracias a la Ley de Amperé-Maxwell (Leer [Ecuaciones de Maxwell](/docs/Physics/maxwell_eqs.md)) que una corriente que circula por un cable genera un campo magnético alrededor. El flujo de este campo magnético se define como:

```math
\Phi_B = \iint_R\vec{B}\cdot d\vec{A}
```

O en notación feyniana (Leer [Teoría de la Integración](/docs/Mathematics/integration_theory.md)):

```math
 \Phi_B = \iint_R\mathbb{B}\cdot d\mathbb{A}
 ```

La inductancia se define como la medida de la oposición al cambio de la corriente. Aunque es un término comúnmente asociado a inductores o bobinas, esta oposición está siempre presente en los conductores cuya corriente varía con el tiempo. Al variar la corriente, se produce un cambio en el campo magnético alrededor del conductor que, de acuerdo con la Ley de Faraday, induce una tensión en el propio circuito. Si bien estos efectos de autoinductancia no suelen ser apreciables en circuitos de baja corriente y baja frecuencia, se manifiestan con mayor intensidad en las líneas de transmisión. La inductancia matemáticamente se escribe como:

```math
L = \frac{\Phi_B}{i}
```

Este efecto es indeseable debido a que la inductancia no permite los cambios bruscos de corriente, y como veremos más adelante, la inductancia esta relacionada con el tiempo de subida.





## Sistema más completo (RLC)

El modelo RC es una pequeña aproximación al sistema de alta potencia, sin embargo, los efectos inductivos presentados por la circulación de corriente hace que el modelo quede insuficiente para nuestras necesidades. Para realizar la matemática correspondiente consideremos el siguiente circuito RLC:


![Circuito RLC](/img/pulse_power/rlc.png)

$C$ representa la la capacitancia efectiva del banco de condensadores, mientras que $L$ representa los efectos inductivos debido a las corrientes que circulan por los cables. Cuando se cierra el interruptor resulta en un circuito RLC serie, cuya ecuación (obtenida de la Ley de Tensiones de Kirchoff) es:

```math
\frac{1}{C} \cdot \int{i(t)\>dt} + L\cdot \frac{d i(t)}{dt} + i(t)R = 0
```

El lector o lectora (agregado de último momento, perdóname Gabriela) podrá notar que usamos la relación integral del condensador. Por su parte la ecuación que usamos para el inductor es la definición del comportamiento de este circuito dinámico, la cual es:

```math
v(t) = L\cdot \frac{d i(t)}{dt}
```

Aplicando el operador lineal "derivada" en la ecuación de malla resulta en:

```math
\frac{1}{C}\cdot i(t) + L\cdot \frac{d^2 i(t)}{dt^2} + \frac{di(t)}{dt}R = 0
```

Convirtiendo la ecuación en "mónica" y reorganizando:

```math
\frac{d^2 i(t)}{dt^2} + \frac{R}{L}\cdot\frac{di(t)}{dt} + \frac{1}{LC}\cdot i(t)= 0
```

Como se puede observar esta es una ecuación de segundo orden de coeficientes constantes, cuya ecuación característica es:

```math
r^2 + \frac{R}{L}\cdot r + \frac{1}{LC} = 0
```

Aplicando el capricho del diablo a dicha ecuación:

```math
r_{1,2} = \frac{-\frac{R}{L} \pm \sqrt{\left(\frac{R}{L}\right)^2-4\left(\frac{1}{LC}\right)}}{2}
```

Realizando una pequeña manipulación llegamos a:

```math
r_{1,2} = -\frac{R}{2L} \pm \sqrt{\left(\frac{R}{2L}\right)^2-\frac{1}{LC}}
```

Definiremos $`\omega_0`$ y $`\alpha`$ como:

```math
\omega_0 = \frac{1}{\sqrt{LC}}
```

```math
\alpha = \frac{R}{2L}
```

De tal forma que las soluciones quedarían:

```math
r_{1,2} = -\alpha \pm \sqrt{\alpha^2-\omega^2}
```

Dependiendo del resultado dentro de la raices podremos tener dos casos, realmente son tres pero el caso criticamente amortiguado no se tendrá en cuenta.

