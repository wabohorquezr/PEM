# `docs/Mathematics/integration_theory.md`

# Teoría de la Integración

Personalmente esta parte de la documentación representa la gran totalidad de mi trabajo. En esta parte se documenta todas las integrales más importantes que fundamentan todo el cálculo vectorial, siempre mostrando la mayor rigurosidad posible en cada una de las definiciones.

## Integrales de Trayectoria

Esta es el primer acercamiento a las integrales especiales, esta en particular relaciona los campos escalares con trayectorias parametrizadas.


### Definición
*La integral de trayectoria, o integral de $`f(x,y,z)`$ a lo largo de la trayectoria $`\sigma`$, está definida cuando $`\sigma:I=[a,b] \to \mathbb{R}^3`$ es de clase $`C^1`$ y cuando la función compuesta $`t \mapsto f(x(t),y(t),z(t))`$ es continua en $`I`$. Definimos esta integral por la ecuación*

```math 
\int_\sigma f \> ds = \int^b_a f(x(t),y(t),z(t))\>\|\sigma'(t)\|\>dt 
```

Es igual de válido denotar la integral por:

```math 
\int_\sigma f \> ds = \int^b_a f(\sigma(t))\>\|\sigma'(t)\|\>dt
```

Nótese que si la función que se integra es $`f = 1`$, se está hallando la longitud de arco de la trayectoria desde a hasta b.

## Integrales de Línea

Una de las más usadas de manera inconsciente, más incluso que la anterior. Si en el caso anterior se buscaba relacionar campos escalares a trayectorias, esta busca relacionar campos vectoriales. Por lo que podríamos pensar que esta integral suma los aportes de cada pequeño vector de la trayectoria en dirección del campo vectorial. Se puede ver la complicación, por que quiere decir que debemos relacionar el operador de producto punto (el cual a la final representa la proyección de un vector sobre otro) con una integral. Por suerte contamos con la siguiente definición.

### Definición
*Sea $`\vec{F}`$ un campo vectorial en $`\mathbb{R}^3`$ que sea continuo sobre la trayectoria $`C^1`$, $`\sigma:[a,b] \to \mathbb{R}^3`$. Definimos la integral de línea de $`\vec{F}`$ a lo largo de $`\sigma`$ por la ecuación*

```math
\int_\sigma \vec{F}\cdot d\vec{s} = \int_a^b \vec{F}(\sigma(t))\cdot\sigma'(t)\>dt
```

Para Feynman la notación vectorial resultaba más comoda en formato de pizarra como sigue:

```math
\int_\sigma \mathbb{F}\cdot d\mathbb{s} = \int_a^b \mathbb{F}(\sigma(t))\cdot\sigma'(t)\>dt
```

Nótese que la notación cambia y ahora el diferencial se vuelve a su vez un vector en dirección de la curva. Podemos justificar la deducción de esta ecuación como sigue. Conforme $t$ varía sobre un pequeño intervalo $t$ a $`t+\Delta t`$, la partícula de estudio se mueve de $`\sigma(t)`$ a $`\sigma(t+\Delta t)`$. Por lo tanto, el vector de desplazamiento será entonces $`\Delta s = \sigma(t+\Delta t) - \sigma(t)`$. Para $`\Delta t`$ pequeño obtenemos la siguiente expresión por la definición de derivada $`\Delta s \approx \sigma'(t)\Delta t`$. El "trabajo" realizado para ir de $`\sigma(t)`$ a $`\sigma(t+\Delta t)`$, es decir, la proyección del campo para un elemento pequeño de distancia es, aproximadamente:

```math
\vec{F}(\sigma(t))\cdot \Delta \vec{s} \approx \vec{F}(\sigma(t))\cdot \sigma'(t)\Delta t
```

Si subdividimos nuestro intervalo $[a,b]$ en $n$ partes iguales $`a = t_0 < t_1 < ... < t_n = b`$, con $`\Delta t = t_{i+1} - t_i`$, entonces el "trabajo" realizado por $`\vec{F}`$, es decir, el aporte de cada una de las $n$ proyecciones del campo sobre la curva, es aproximadamente:


```math
\sum _{i=0}^{n-1} \vec{F}(\sigma(t))\cdot \Delta \vec{s} \approx \sum _{i=0}^{n-1} \vec{F}(\sigma(t))\cdot \sigma'(t)\Delta t
```

Cuando $`n \to \infty`$, esta aproximación se vuelve cada vez mejor, de modo que es razonable definir trabajo como el límite de la suma anterior cuando $`n \to \infty`$. Este límite por definición de integral no conduce a la ecuación antes definida.

## Superficies Parametrizadas

La siguiente fase de estudio trata acerca de las integrales de superficies, pero primero debemos dar una definición formal sobre superficies. La superficie con la que debe estar acostumbrado el lector (o lectora) son las gráficas de funciones $`f(x,y)`$. Sin embargo, existen superficies que por su naturaleza no se pueden representar como la gráfica de una función, como la que se muestra a continuación:

![Superficie Parametrizada](/img/integration_theory/parameter_fun.png)

Claramente no se puede establecer esta superficie como una función debido que existen diferentes imagenes para el mismo punto. Estas observaciones nos impulsan a extender nuestra definición de superficie. Por lo tanto, vamos a plantear la siguiente definición:

### Definición
*Una superficie parametrizada es una función $`\Phi:D\subset\mathbb{R}^2\to\mathbb{R}^3`$, donde $`D`$ es algún dominio en $`\mathbb{R}^2`$. La superficie $`S`$ correspondiente a la función $`\Phi`$ es su imagen: $`S=\phi(D)`$. Podemos escribir*

```math
\Phi(u,v) = [x(u,v),y(u,v),z(u,v)]
```

*Si $`\Phi`$ es diferenciable o es de clase $`C^1`$ (que equivale a decir que $`x(u,v)`$, $`y(u,v)`$ y $`z(u,v)`$ son funciones diferenciables o $`C^1`$ de $`(u,v)`$), llamamos a $`S`$ superficie diferenciable o $`C^1`$.*

Podemos pensar que $`\Phi`$ tuerce o dobla la región $`D`$ en el plano para producir la superficie $`S`$. Así, cada punto $`(u,v)`$ en $`D`$ se convierte en un rótulo para un punto $`(x(u,v), y(u,v), z(u,v))`$ en $`S`$.

### Vectores Tangentes a Superficies Parametrizadas

Supongamos que $`\Phi`$ es diferenciable en $`(u_0,v_0)\in\mathbb{R}^2`$. Si fijamos $`u`$ en $`u_0`$ obtenemos una función $`\mathbb{R}\to\mathbb{R}^3`$ dada por $`t \mapsto \Phi(u_0, v)`$, es decir, acabamos de convertir la superficie parametrizada en una curva que pertenece a dicha superficie. Sabemos que el vector tangente a esta curva (Leer [Teoría de la Vectorización](/docs/Mathematics/vector_theory.md)) en el punto $`\Phi(u_0,v_0)`$ está dado por:

```math
\vec{T}_v = \frac{\partial x}{\partial v}(u_0,v_0)\hat{i} + \frac{\partial y}{\partial v}(u_0,v_0)\hat{j} + \frac{\partial z}{\partial v}(u_0,v_0)\hat{k}
```

De manera análoga podemos fijar $`v`$ en $`v_0`$, lo que nos daría la curva $`t \mapsto \Phi(u, v_0)`$. Si ahora hallamos el vector tangente a esta nueva curva en el punto $`\Phi(u_0,v_0)`$ resulta en:

```math
\vec{T}_u = \frac{\partial x}{\partial u}(u_0,v_0)\hat{i} + \frac{\partial y}{\partial u}(u_0,v_0)\hat{j} + \frac{\partial z}{\partial u}(u_0,v_0)\hat{k}
```

Dado que los vectores $`\vec{T}_u`$ y $`\vec{T}_v`$ son tangentes a las dos curvas sobre la superficie en un punto dado, el vector $`\vec{T}_u\times\vec{T}_v`$ debería ser normal a la superficie en dicho punto.

## Integral de Superficie sobre una Función Escalar

Una vez conocemos la definición de superficie estamos listos para la siguiente definición:

### Definición

*Si $`f(x,y,z)`$ es una función continua con valores reales definida en S, definimos la integral de $`f`$ sobre $`S`$ como*

```math
\iint_S{f(x,y,z)dS} = \iint_D{f(\Phi(u,v))\|\vec{T}_u\times\vec{T}_v\|}\,du\,dv
```

*Donde $`\vec{T}_u`$ y $`\vec{T}_v`$ son los vectores normales a la superficie definidos anteriormente.*

Otras notaciones validas para esta integral son:

```math
\iint_S{f(x,y,z)dS} = \iint_S{f\,dS} = \int_S{f\,dS}
```

Recordar que aunque se escriba una sola integral se está haciendo referencia a la integración bajo una superficie. Consulte con su docente encargado en caso de contradicción.

Si desarrollamos la definición llegamos a la siguiente expresión:

```math
\iint_S{f(x,y,z)dS} = \iint_D{f(x(u,v),y(u,v),z(u,v))\sqrt{\left[\frac{\partial(x,y)}{\partial(u,v)}\right]^2 + \left[\frac{\partial(y,z)}{\partial(u,v)}\right]^2 + \left[\frac{\partial(x,z)}{\partial(u,v)}\right]^2}}\,du\,dv
```

Nótese que si la función $`f=1`$ el resultado de la integral devolverá el area de la superficie.



## Referencias 

[1] A. J. Tromba y J. E. Marsden, Cálculo Vectorial, 3.ª ed. Addison-Wesley Iberoamericana, 1991.