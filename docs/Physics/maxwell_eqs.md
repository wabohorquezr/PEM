# `docs/Physics/maxwell_eqs.md`

# Ecuaciones de Maxwell

Se recomienda leer primero [Efectos Electromagnéticos]() y [Teoría de la Vectorización](/docs/Mathematics/vector_theory.md).

## Primera Ecuación de Maxwell   
También conocida como la Ley de Gauss para el campo eléctrico, nos dice que una carga eléctrica genera un campo eléctrico.  

```math
\nabla\cdot\vec{E}=\frac{q}{\epsilon_{0}}
```

Siendo un poco más técnico se puede afirmar que la divergencia del campo eléctrico ($`\nabla\cdot\vec{E}`$) es igual a la carga $q$ entre la permitividad dieléctrica absoluta del vacío.

## Segunda Ecuación de Maxwell
También conocida como la Ley de Gauss para el campo magnético, nos dice que un campo magnético siempre tiene dos polos y se cierra sobre sí mismo.  

```math
\nabla\cdot\vec{B}=0
```  

Es correcto afirmar que al no poseer fuentes ni sumideros la divergencia del campo magnético es cero.  

## Tercera Ecuación de Maxwell
También conocida como la Ley de Faraday-Lenz, nos dice que un campo magnético variable genera un campo eléctrico.  

```math
\nabla\times\vec{E}=-\frac{\partial\vec{B}}{\partial t}
```

Lo que nos dice esta ecuación es que el rotacional del campo eléctrico es igual a la derivada parcial del campo magnético con respecto al tiempo. Esto significa que la variación del campo magnético genera un campo eléctrico, demostrando que se puede generar un voltaje a través de esta variación.  

## Cuarta Ecuación de Maxwell

También conocida como la Ley de Ampère-Maxwell nos dice que un “campo eléctrico que varía con el tiempo produce un campo magnético” [1].  

```math
\nabla \times \vec{B} = \mu_{0}\vec{J} + \mu_{0}\epsilon_{0}\frac{\partial\vec{E}}{\partial t}
```

Esta ecuación nos dice que un campo magnético puede ser generado “por la corriente eléctrica que fluye por un alambre conductor” [2], o por la variación del campo eléctrico.  


## Referencias

[1] E. Coimbra, "6.1 Ecuaciones de Maxwell," SlideShare, feb. 21, 2011. [En línea]. Disponible en: https://es.slideshare.net/edisoncoimbra/61-ecuacion-maxwell.

[2] Colaboradores de Wikipedia, "Ecuaciones de Maxwell," Wikipedia, nov. 19, 2024. [En línea]. Disponible en: https://es.wikipedia.org/wiki/Ecuaciones_de_Maxwell.

[3] R. Resnick y D. Halliday, Física. Compañía Editorial Continental, S. A., 1960.