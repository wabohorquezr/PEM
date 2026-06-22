
# `docs/Components/MOSFET/Introduction.md`

# Introducción al MOSFET

El MOSFET (Metal Oxide Semiconductor Field Effect Transistor) es el dispositivo por excelencia más utilizado en el mundo de la electrónica. Diseñado en los años 50 del siglo pasado, resultó en un dispositivo que cuenta con diferentes funcionalidades como la amplificación, la ganancia controlada o la conmutación. Cada una de ellas tendrá su sección específica, pero primero se debe familiarizar al lector con una breve descripción física de este dispositivo. Cabe aclarar que el MOSFET es un componente denso y aqui se resumirá lo más posible su explicación por lo que se le recomienda al lector o lectora que complemente la información con el Sedra (se que insisto bastante con este libro y algunos inferiores e insensatos recomendarán el Boylestad, pero ese camino es solo el de los débiles, el de los ingenuos; si realmente quieres tener un alma inquebrantable lee el Sedra).

*Nota del autor: entiendo que un integrante está redactando está sección, o al menos tiene la tarea asignada. Si él ya escribió su parte le pido encarecidamente que remplace la mía, esta redacción será auxiliar.*

## Estructura

Existen diferentes tipos de MOSFET en el mercado, sin embargo, uno de los más vendidos a nivel mundial es el MOSFET de enriquecimiento, por lo que como el lector o lectora deducirá será el único que se explicará. La estructura física del MOSFET se presenta en la Figura 1. No hay por que alarmarse por todas las indicaciones, vamos a ignorar algunas por el momento como la W y la L, y por su parte se presentaran las más fundamentales.

![Estructura](/img/MOSFET/Estructura%20MOSFET.png)
<br>**Fig. 1.** Estructura Física MOSFET, Adaptado de [1]

Lo primero es mencionar que los rectangulos blancos de la imagen son los terminales, es decir, son contactos de metal. Lo que realmente le debe llamar la atención al lector o lectora son las regiones marcadas como **Source**, **Body**, y **Drain**. Las regiones Source y Drain son sustratos de silicios dopados con un elemento donador (eg. Fósforo), mientras que el Body (toda la región fuxia) es un sustrato de silicio dopado con un elemento aceptor (eg. Boro). En otras palabras, el Source y el Drain son sustratos tipo n, mientras que el Body es tipo p, se recomienda encarecidamente ver [Semiconductores](/docs/Physics/semiconductors.md). Nótese que el contacto de metal más grande, es decir, el que está indicado con una G, no está conectado físicamente al Body ya que en medio existe un material aislante (Dióxido de Silicio). Vamos ahora a presentar una vista lateral del MOSFET, la cual se observa en la Figura 2.

![Estructura](/img/MOSFET/Estructura%20Lateral%20del%20MOSFET.png)
<br>**Fig. 2.** Estructura Física del MOSFET vista Lateralmente, Adaptado de [1]

Al observar la estructura del MOSFET podemos deducir el uso de las primeras tres letras de su nomenclatura (Metal Oxide Semicondutor), puesto que en el terminal G hay un contacto de metal, abajo de el hay un aislante hecho por oxido de silicio y por último hay un material semiconductor (el Body). Formalmente podríamos decir que el MOSFET es un dispositivo de 4 terminales: el Gate, el Source, el Drain y el Body. Sin embargo, en muchas aplicaciones se requiere un compartamiento específico del MOSFET en donde los terminales de Body y Source están conectados, es decir, en una conexión en corto, por lo que en la mayoría de las ocasiones se considera al MOSFET como un dispositivo de 3 terminales: el Gate, el Source y el Drain. El por qué de cada nombre será explicado más adelante en su funcionamiento, sin embargo, el lector o lectora puede deducir que el nombre de Body se debe a que representa el cuerpo del dispositivo.

## Funcionamiento

El lector o lectora se podrá preguntar por qué no se hizo más enfásis en la estructura física, sin embargo, en esta parte se adentrará más en su estructura, puesto que es más sencillo verlo una vez en acción. Vamos a considerar diferentes escenarios, pero en todos ellos observaremos que lo que realmente cambia la operación del transistor es la tensión aplicada al terminal de Gate. Como la corriente no puede atravesar físicamente el aislante presente en este terminal el flujo de la misma será cero, y solo será contemplado a través de los terminales de Drain y Source. 

### Operación con Cero Voltios en Gate

Con cero voltios en la terminal de compuerta (Gate en inglés) el transistor se puede modelar como dos diodos en contradicción (Figura 3), ya que como un diodo es básicamente una unión *pn* los sustratos del MOSFET bajo estas condiciones tienen este mismo comportamiento. Esto nos deja entrever que sin importar la tensión que pongamos entre los teminales D y S, que para mayor simplicidad vamos a llamar $`v_{DS}`$, no existirá flujo alguno de corriente.

![Estructura](/img/MOSFET/back_to_back.png)
<br>**Fig. 3.** Modelo Equivalente - Diodos Espalda con Espalda

### Creación de un Canal

Consideremos la situación presentada en la Figura 4, en este caso se ha conectado los terminales D y S a tierra y se ha aplicado una tensión al terminal G<sup>1</sup>. Dado que el terminal de Source está conectada a tierra, la tensión de compuerta aparece entre la compuerta y la fuente (el Source) y, por lo tanto, lo denotamos como $`v_{GS}`$. Al aplicar esta tensión estamos generando que las cargas positivas del Body cercanas al aislante sean repelidas hacia el fondo del sustrato, debido a que la tensión es positiva y asumimos que por lo tanto hay cargas positivas en el contacto de metal. La región de deplexión que vemos en la Figura 4 está ocupada por la carga negativa ligada asociada a los átomos aceptores del sustrato. Estas cargas quedan “descubiertas” porque las cargas positivas (o huecos) se han desplazado hacia abajo, hacia el sustrato. Además, la tensión positiva de la compuerta atrae electrones desde las regiones de fuente y drenaje (donde se encuentran en abundancia) hacia la región del canal. Cuando se acumula una cantidad suficiente de electrones cerca de la superficie del sustrato bajo la compuerta, se crea una región n, que conecta las regiones de fuente y drenaje, como se muestra en la Figura 4. 

Ahora, si se aplica una tensión entre Drain y Source la corriente si tiene un camino por el cual fluir, el canal n inducido. De aqui podemos deducir los nombres de estos terminales. Es sabido que los electrones fluyen en dirección opuesta a la corriente, es decir, si la corriente fluye de Drain a Source entonces los electrones fluyen de Source a Drain. En otras palabras, Source es la *"fuente"* de los electrones y Drain es donde se van o *"drenan"* los electrones. Como el canal inducido es de tipo n, a estos transistores se les conoce como *MOSFET de canal n* o *NMOS*.

![Tensión Aplicada](/img/MOSFET/Voltaje%20en%20el%20Gate.png)
<br>**Fig. 4.** Tensión Aplicada en $`v_{GS}`$, Adaptado de [1]

Como mencionamos anteriorermente necesitamos una tensión $`v_{GS}`$ para poder crear el canal que permitirá el flujo de corriente, sin embargo, hay una tensión mínima a la cual existe el suficiente número de electrones para formar este canal. A esta tensión mínima se le conoce como tensión de umbral y se denota como $`V_{GS(th)}`$ (Threshold)<sup>2</sup>. Este valor es controlado durante la fabricación del transistor y ronda valores entre 0.3V a 1V, sin embargo, MOSFET de potencia pueden llegar hasta los 4V. 

Una última observación es que la compuerta y la región del canal del MOSFET forman un condensador de placas paralelas, donde la capa de óxido actúa como dieléctrico. La tensión positiva en la compuerta provoca la acumulación de carga positiva en la placa superior del condensador (el electrodo de compuerta). La correspondiente carga negativa en la placa inferior se genera por los electrones en el canal inducido. De este modo, se desarrolla un campo eléctrico en dirección vertical. Este campo controla la cantidad de carga en el canal y, por lo tanto, determina la conductividad del canal y, a su vez, la corriente que circulará por él al aplicar una tensión $`v_{DS}`$. Este es el origen del nombre *transistor de efecto de campo* (FET). ¡Ya sabemos porque se llama MOSFET!


### _____________________________________________
<sup>1</sup><small> El lector o lectora deberá acostumbrarse a los múltiples nombres que les otorgo a cada uno de los terminales, espero esté atento o atenta.</small><br>
<sup>2</sup><small> Dependiendo del autor tiene otras notaciones como $V_t$ o $`V_{tn}`$</small>


### Aplicando una pequeña tensión $`v_{DS}`$

Como vimos anteriormente para que exista un flujo de electrones debe haber una tensión mínima $`v_{GS}`$. Supongamos que el transistor ya tiene un canal creado, es decir, hay una tensión $`v_{GS}`$ mayor al umbral. Ahora vamos a estudiar el comportamiento del transistor cuando se aplica una tensión *"pequeña"* entre los terminales de Drain y Source. Claramente deberemos definir que es pequeño, pero por el momento vamos a describir su comportamiento. La explicación de esto es un poco extensa y cofunsa, por lo que se le recomienda al lector o lectora investigar [1] para mayor profundización, pero básicamente la relación entre tensión y corriente es la siguiente:

```math
i_d = \left[(\mu_n C_{ox}) \left(\frac{W}{L}\right)(v_{GS} - v_{GS(th)})\right]\cdot v_{DS}
```

No se me asuste lector o lectora, deme un segundo para explicarlo. La constante $`\mu_n`$ es la movilidad de los electrones, y está relacionada con el tipo de material y el tipo de dopaje. La constante $`C_{ox}`$ es la capacitancia del condensador de placas paralelas donde el óxido es el aislante. La constante $`W`$ es el ancho del transistor y $`L`$ es el largo del canal. El resto de términos ya fueron mencionados anteriormente. Nótese que me referí a la mayoría de ellos como constantes, y en general lo son y solo dependen de las condiciones de fabricación del transistor, por lo que la manera más sencilla de escribir la ecuación es condensando todas estas constantes en una sola, por lo que definiremos:

```math
k_n = (\mu_n C_{ox}) \left(\frac{W}{L}\right)
```
Por lo que quedaría la ecuación:

```math
i_d = k_n(v_{GS} - v_{GS(th)})\cdot v_{DS}
```

La cual es una ecuación que nos da menos susto. Para que el análisis dimensional sea coherente $`k_n`$ debe tener unidades de $`A/V^2`$. No lo mencioné, pero claramente $`i_d`$ hace referencia a la corriente que fluye desde Drain a Source. Nótese que para un valor fijo de $`v_{GS}`$ la relación entre tensión $`v_{DS}`$ e $`i_d`$ es lineal. ¿A que les recuerda eso? Exactamente a una resistencia, bueno más precisamente a una conductancia por la forma en la que se multiplican pero son análogos. Si cambias el valor de $`v_{GS}`$ estas cambiando el valor de esta "pendiente". Observemos este comportamiento en la Figura 5. Para contextualizar un poco se le llama *overdrive voltage* ($`V_{OV}`$) a la diferencia $(v_{GS} - v_{GS(th)})$. Podemos observar que para valores menores a $V_t$ (otra forma de llamar al $`v_{GS(th)}`$ o tensión de umbral) la curva es cero, pues no ha superado el umbral y por lo tanto no puede haber flujo. Para valores mayores a la tensión de umbral la curva se vuelve más pronunciada, y como mencionamos anteriormente, está relacionada con la conductancia.


![Región Lineal](/img/MOSFET/Curvas%20del%20Triodo.png)
<br>**Fig. 5.** Curvas de $`i_d`$ vs $`v_{DS}`$ para diferentes valores de $`v_{GS}`$, Adaptado de [1]

Estos nos deja entrever que tenemos una resistencia controlada por tensión, la tensión $`v_{GS}`$. A esta región de trabajo se le llama *"zona de tríodo"*, es decir, la región donde aplicamos una tensión $`v_{DS}`$ pequeña.

Después de esta pequeña presentación surge la pregunta *¿Qué es pequeño?*, por lo que diremos que el transistor estará en zona de tríodo siempre y cuando:

```math
v_{DS} < v_{GS} - v_{GS(th)}
```

A esos valores de tensión $`v_{DS}`$ se les considerará pequeños.

### ¿Qué pasa si me paso? - Zona de Saturación

Surge la pregunta: "*¿Y si decido aumentar la tensión $`v_{DS}`$ por encima de la condición? ¿Acaso se quemará mi querido transistor que con tanto esfuerzo estoy intentando aprender?*", y no mi querido lector o lectora, ya te explico que pasa. Primero, consideremos una tensión $`v_{GS}`$ por encima del umbral, esto provoca la creación de un canal cuyo ancho es directamente proporcional a la diferencia de potencial. Lo que sucede es que, al crear una diferencia de potencial $v_{DS}$, inconscientemente estamos modificando la tensión en cada punto del canal; por lo tanto, el ancho también se ve modificado. En los puntos más cercanos a Source, la diferencia de potencial será exactamente $v_{GS}$; sin embargo, en los puntos más cercanos a Drain, la tensión será $`v_{GS} - v_{DS}`$, debido a que estas tensiones se contradicen al aplicar Kirchhoff. Por lo que, al ir aumentando la tensión $v_{DS}$, este canal va volviéndose más estrecho en la parte de Drain. Veamos esto en la Figura 6. En esta figura podemos observar que el ancho del canal en la parte de Source es proporcional a la tensión $V_{OV}$ (*overdrive voltage*), mientras que en la parte de Drain es proporcional a $V_{OV} - v_{DS}$. Esta relación de proporcionalidad viene de un análisis un poco más complejo que por brevedad no será explicado, pero que el lector o lectora podrá consultar en [1].

![Ensanchamiento del canal](/img/MOSFET/Anchura%20del%20Canal.png)
<br>**Fig. 6.** Estrechamiento del Canal, Adaptado de [1]

Nótese que para que exista un ancho en la parte de Drain la tensión $`v_{DS}`$ debe ser menor al *overdrive voltage*, el cual se define como $`v_{GS} - v_{GS(th)}`$ ¡De aquí viene nuestra relación de pequeño $v_{DS}$! Y diras *"Ya entiendo lo que me quieres decir con el canal, pero ¿Qué sucede realmente si me llego a pasar? ¿Frenaré el flujo de corriente haciendo inservible mi pobre transistor que tanto está sufriendo?"*. Consideremos primero el caso en que $`v_{DS} = v_{GS} - v_{GS(th)}`$ el cual se presenta en la Figura 7. En este caso el ancho del canal en el terminal de Drain es cero y a esto se le llama **pinch-off** o estrangulamiento del canal.  Aumentar $`v_{DS}`$ más allá de este valor (es decir, $`v_{DS} > v_{GS} - v_{GS(th)}`$) no afecta a la forma ni a la carga del canal, y la corriente que lo atraviesa permanece constante en el valor alcanzado cuando  $`v_{DS} = V_{OV}`$. Es decir la corriente se **satura**, no puede aumentar más por mucho que aumentemos la tensión. 


![Estrangulamiento del canal](/img/MOSFET/pinch%20off.png)
<br>**Fig. 7.** Estrangulamiento del Canal, Adaptado de [1]

Cuando la condición $`v_{DS} \geq v_{GS} - v_{GS(th)}`$ se cumple se dice que el transistor está tranbajando en *"zona de saturación"*. La ecuación que describe el comportamiento en esta zona es la siguiente:

```math
i_d = \frac{1}{2}k_n\cdot \left(v_{GS} - v_{GS(th)}\right)^2
```

Para mayor comodidad vamos a definir una nueva constante $`k`$ tal que:

```math
k = \frac{1}{2}k_n = \frac{1}{2}(\mu_n C_{ox}) \left(\frac{W}{L}\right)
```

Por lo que nuestra relación quedaría:

```math
i_d = k\cdot \left(v_{GS} - v_{GS(th)}\right)^2
```

Podemos observar que la corriente ahora solo depende únicamente de la tensión aplicada a la compuerta y no la tensión $`v_{DS}`$. Esta relación también plantea un comportamiento no lineal entre la corriente y la tensión.

## Curvas del MOSFET

Una vez explicado los funcionamientos básicos viene bien resumirlos en una gráfica que relacione el comportamiento de la corriente $`i_d`$ vs la tensión $`v_{DS}`$ con la suposición de que la tensión $`v_{GS}`$ superó el umbral. Esta gráfica se presenta en la Figura 8. En esta gráfica podemos ver que cuando $`v_{DS}`$ no ha superado la *overdrive voltage* (el $`v_{GS} - v_{GS(th)}`$) la curva presenta un comportamiento mayoritariamente lineal cerca del cero, con una pequeña curvatura cerca del límite de esta condición. Una vez superado la *overdrive voltage*<sup>1</sup> la relación entre tensión y corriente se vuelve una constante, es decir, que sin importar el valor de tensión la corriente permanece constante.

![Curva General del MOSFET](/img/MOSFET/Curva%20General%20del%20MOSFET.png)
<br>**Fig. 8.** Curva $`i_d`$ vs $`v_{DS}`$, Adaptado de [1]

### _____________________________________________
<sup>1</sup><small> Me niego a llamarle tensión de sobrecarga.</small><br>


## Modelo Circuital

Después de toda esa presentación del funcionamiento el lector o lectora se podría preguntar. *"Oye, ¿Cada vez que quiera análizar un circuito con un NMOS debo dibujar esa caja toda grande?"* y no, existe un símbolo que representa este dispositivo, sin embargo, no es universal, difiere tanto del autor como del simulador de circuitos. Pero no te preocupes lector o lectora, te mostraré los dos modelos más utilizados para representar el NMOS.

## ¿Qué pasa si pienso al revés? - PMOS

Un lector o lectora curios@ podría pensar *"Oye, me presentaste una configuración donde el canal era tipo n y todo era muy bonito, ¿Qué pasaría si yo quiero ser hambrient@ de poder y quiero un canal tipo p?"* Y yo te diría mi querido lector o lectora que tienes una curiosidad invaluable y una pregunta muy genuina, por eso te voy a explicar ahora qué es el *MOSFET de canal p* o *PMOS*.




## Referencias

[1] El Sedra, libro solo apto para los eruditos, seres dotados de razón, no para débiles