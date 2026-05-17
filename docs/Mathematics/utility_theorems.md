# `docs/Mathematics/utility_theory.md`

# Teoremas y Relaciones de Utilidad

En esta sección se ilustra algunos teoremas y definiciones que resultan de utilidad conocerlos, le recomendamos al lector leerlos con detenimiento.

# Transformada de Laplace

Es una transformada integral, es decir, una transformación de la forma:

$$T(f(t))=\int_{t_1}^{t_2}{K(u,t)\cdot f(t)\>dt}= F(u)$$

donde la entrada en una función ($f(t)$), y la salida es otra función ($F(u)$) en términos de la variable $u$. $K(u,t)$ se le llama *núcleo* o *kernel*.

Para nuestro caso la Transformada de Laplace se define como:

$$F(s)=\int_{0}^{\infty}{e^{-st}\cdot f(t)\>dt}$$

Para todo $t>0$ siempre que la integral exista.

# Teorema del valor Final

Es un teorema que relaciona las expresiones del dominio de la frecuencia con el dominio del tiempo. El teorema dice que si $f(t)$ tiene transformada de Laplace el comportamiento de $f(t)$ es el mismo que el de su tranformada en el origen, es decir:

$$\lim_{t \to \infty} f(t)  = \lim_{s \to 0} s\cdot F(s)$$

Siempre y cuando los límites existan.

# Teorema del valor Inicial

Análogo al anterior, se establece que el comportamiento de $f(t)$ en el origen es el mismo que el de su transformada en el infinito, es decir:

$$\lim_{t \to 0} f(t)  = \lim_{s \to \infty} s\cdot F(s)$$

Siempre y cuando los límites existan.

# Espectro de Frecuencia de Señales

Es una caracterización de una señal obtenida por medio de la serie de Fourier (Acordarme de ponerla) y la tranformada de Fourier (Igual). Estas herramientas proporcionan los medios para representar una señal como la suma de ondas sinoidales de frecuencias y amplitudes diferentes. La serie de Fourier es útil para el caso especial de señales periódicas como la mostrada a continuación:

![Señal periodica](/img/utility_theorems/square_wave.svg)

Las frecuencias en estos casos están armónicamente relacionadas con una frecuencia natural, para este caso especifico la señal cuadrada se puede expresar como:

$$v(t) = \frac{4V}{\pi}(\sin(\omega_0t) + \frac{1}{3}\sin(3\omega_0t) + \frac{1}{5}\sin(5\omega_0t) + ...)$$

En este caso $\omega_0 = \frac{2\pi}{T}$. Las componentes sinoidales de la serie constituyen el *espectro de frecuencias* y se pueden representar gráficamente:


![espectro periodica](/img/utility_theorems/frequency_spectrum.svg)

La transformada de Fourier por su parte, es util para cualquier señal arbitraria no periódica.

![Señal arbitraria](/img/utility_theorems/vs_signal.svg)

A diferencia de las señales periódicas, donde su espectro está formado por frecuencias discretas ($\omega_0$ y sus armónicos), el espectro de unal señal no periódica contiene en general todas las frecuencias posibles, como una función continua en el tiempo.

![espectro arbitraria](/img/utility_theorems/fourier_transform.svg)




