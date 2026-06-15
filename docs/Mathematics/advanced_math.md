# `docs/Mathematics/advanced_math.md`

# Matemática Avanzada

Esta sección presenta quizá la parte más compleja y confusa de toda la documentación. En esta parte se tratan algunas nociones avanzadas de la matemática pura.

## Series de Fourier en $`\mathbb{T}`$

Vamos a denotar por $`\mathbb{R}`$ el conjunto aditivo de los números reales y por $`\mathbb{Z}`$ el subconjunto de los enteros. El conjunto $`\mathbb{T}`$ es definido como el cociente $`\mathbb{R}/2\pi\mathbb{Z}`$ donde, como lo indica la notación, $`2\pi\mathbb{Z}`$ es el grupo de los multiplos de $`2\pi`$. Esta relación indica un conjunto donde se ha tomado todo el conjunto real y se ha "cortado" en fragmentos de distancia $`2\pi`$. El nombre correcto para este conjunto es "*Todos los números de $`\mathbb{R}`$ de módulo $`2\pi`$ .*" Resulta evidente que existe una relación entre $`\mathbb{T}`$ y las funciones con periodo de $`2\pi`$ en $`\mathbb{R}`$, lo que permite definir nociones como continuidad, diferenciabilidad, etc. Lo que nos permite afirmar lo siguiente:

### Afirmación
*Una función $`f`$ es integrable en $`\mathbb{T}`$ si la función $`2\pi`$-periódica correspondiente, que denotamos nuevamente por $`f`$, es integrable en $`[0,2\pi)`$ y establecemos que:*

```math
\int_\mathbb{T}{f(t)\,dt} = \int_0^{2\pi}{f(x)\,dx}
```

En otras palabras, consideramos el intervalo $`[0, 2\pi)`$ como un modelo para $`\mathbb{T}`$.