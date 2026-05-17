# `docs/Mathematics/integration_theory.md`

# Teoría de la Integración

Personalmente esta parte de la documentación representa la gran totalidad de mi trabajo. En esta parte se documenta todas las integrales más importantes que fundamentan todo el cálculo vectorial, siempre mostrando la mayor rigurosidad posible en cada una de las definiciones.

## Integrales de Trayectoria

Esta es el primer acercamiento a las integrales especiales, esta en particular relaciona los campos escalares con trayectorias parametrizadas.


### Definición
*La integral de trayectoria, o integral de $f(x,y,z)$ a lo largo de la trayectoria $\sigma$, está definida cuando $\sigma:I=[a,b] \to \mathbb{R}^3$ es de clase $C^1$ y cuando la función compuesta $t \mapsto f(x(t),y(t),z(t))$ es continua en $I$. Definimos esta integral por la ecuación*

$$ \int_\sigma f \> ds = \int^b_a f(x(t),y(t),z(t))\>||\sigma'(t)||\>dt$$

Es igual de válido denotar la integral por:

$$ \int_\sigma f \> ds = \int^b_a f(\sigma(t))\>||\sigma'(t)||\>dt $$

Nótese que si la función que se integra es $f = 1$, se está hallando la longitud de arco de la trayectoria desde a hasta b.

## Integrales de Línea

Una de las más usadas de manera inconsciente, más incluso que la anterior. Si en el caso anterior se buscaba relacionar campos escalares a trayectorias, esta busca relacionar campos vectoriales. Por lo que podríamos pensar que esta integral suma los aportes de cada pequeño vector de la trayectoria en dirección del campo vectorial. Se puede ver la complicación, por que quiere decir que debemos relacionar el operador de producto punto (el cual a la final representa la proyección de un vector sobre otro) con una integral. Por suerte contamos con la siguiente definición.

### Definición
*Sea $\vec{F}$ un campo vectorial en $\mathbb{R}^3$ que sea continuo sobre la trayectoria $C^1$, $\sigma:[a,b] \to \mathbb{R}^3$. Definimos la integral de línea de $\vec{F}$ a lo largo de $\sigma$ por la ecuación*

$$ \int_\sigma \vec{F}\cdot d\vec{s} = \int_a^b \vec{F}(\sigma(t))\cdot\sigma'(t)\>dt$$

Para Feynman la notación vectorial resultaba más comoda en formato de pizarra como sigue:

$$ \int_\sigma \mathbb{F}\cdot d\mathbb{s} = \int_a^b \mathbb{F}(\sigma(t))\cdot\sigma'(t)\>dt$$

Nótese que la notación cambia y ahora el diferencial se vuelve a su vez un vector en dirección de la curva. Podemos justificar la deducción de esta ecuación como sigue. Conforme $t$ varía sobre un pequeño intervalo $t$ a $t+\Delta t$, la partícula de estudio se mueve de $\sigma(t)$ a $\sigma(t+\Delta t)$. Por lo tanto, el vector de desplazamiento será entonces $\Delta s = \sigma(t+\Delta t) - \sigma(t)$. Para $\Delta t$ pequeño obtenemos la siguiente expresión por la definición de derivada $\Delta s \approx \sigma'(t)\Delta t$. El "trabajo" realizado para ir de $\sigma(t)$ a $\sigma(t+\Delta t)$, es decir, la proyección del campo para un elemento pequeño de distancia es, aproximadamente:

$$\vec{F}(\sigma(t))\cdot \Delta \vec{s} \approx \vec{F}(\sigma(t))\cdot \sigma'(t)\Delta t$$

Si subdividimos nuestro intervalo $[a,b]$ en $n$ partes iguales $a = t_0 < t_1 < ... < t_n = b$, con $\Delta t = t_{i+1} - t_i$, entonces el "trabajo" realizado por $\vec{F}$, es decir, el aporte de cada una de las $n$ proyecciones del campo sobre la curva, es aproximadamente:

$$\sum _{i=0}^{n-1} \vec{F}(\sigma(t))\cdot \Delta \vec{s} \approx \sum _{i=0}^{n-1} \vec{F}(\sigma(t))\cdot \sigma'(t)\Delta t$$

Cuando $n \to \infty$, esta aproximación se vuelve cada vez mejor, de modo que es razonable definir trabajo como el límite de la suma anterior cuando $n \to \infty$. Este límite por definición de integral no conduce a la ecuación antes definida.

## Superficies Parametrizadas