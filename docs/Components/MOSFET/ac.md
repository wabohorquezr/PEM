# `docs/Components/MOSFET/ac.md`

# Comportamiento en AC del MOSFET

## ¿Por qué estudiar el comportamiento en AC?

Hasta este momento el MOSFET se ha analizado utilizando únicamente tensiones y corrientes de corriente continua (DC). Este análisis permitió establecer un punto de operación estable mediante la polarización. Sin embargo, un amplificador no trabaja con señales constantes, sino con señales variables en el tiempo.

La tensión aplicada al transistor puede escribirse como

```math
v_{GS}(t)=V_{GS}+v_{gs}(t)
```

donde `VGS` corresponde a la polarización DC y `vgs(t)` representa la pequeña señal.

---

## Separación entre DC y AC

El análisis se realiza en dos etapas:

1. Se determina el punto Q mediante el análisis DC.
2. Se reemplazan las fuentes DC por tierra para el análisis AC.
3. Los capacitores de acople y bypass se consideran cortocircuitos en banda media.

---

## Modelo de pequeña señal

En saturación,

```math
I_D=k(V_{GS}-V_{TH})^2
```

Si la señal es pequeña, la curva puede aproximarse por una recta alrededor del punto Q.

La pendiente de esa recta define la **transconductancia**

```math
g_m=\frac{dI_D}{dV_{GS}}
```

obteniéndose

```math
g_m=2k(V_{GS}-V_{TH})
```

o equivalentemente

```math
g_m=\frac{2I_D}{V_{OV}}
```

```math
g_m=\sqrt{2kI_D}
```

con

```math
V_{OV}=V_{GS}-V_{TH}
```

La corriente incremental viene dada por

```math
i_d=g_mv_{gs}
```

---

# Resistencia de salida

Debido a la modulación de longitud de canal, el MOSFET presenta una resistencia de salida finita

```math
r_o=\frac{1}{\lambda I_D}
```

Si λ≈0 entonces

```math
r_o\rightarrow\infty
```

---

# Modelo \pi (Pi)

El modelo \pi es el modelo de pequeña señal más utilizado para analizar amplificadores MOSFET.

Está conformado por:

- Una fuente de corriente controlada de valor `gm·vgs`.
- Una resistencia `ro` entre Drain y Source.
- El terminal Gate permanece abierto debido a que la corriente de Gate es prácticamente cero.

Las ecuaciones fundamentales son

```math
i_d=g_mv_{gs}
```

```math
r_o=\frac{1}{\lambda I_D}
```

Cuando \lambda puede despreciarse, el modelo \pi se simplifica eliminando `r_o`.

---

# Modelo T

El modelo T es completamente equivalente al modelo \pi y produce exactamente los mismos resultados.

La diferencia radica únicamente en la representación del elemento controlado.

La resistencia equivalente del modelo T viene dada por

```math
\frac{1}{g_m}
```

Este modelo suele facilitar el análisis cuando existe una resistencia en Source o cuando se utilizan técnicas de realimentación.

---

# Amplificador Source Común

La configuración Source Común es la más utilizada para obtener ganancia de tensión.

Su ganancia ideal es

```math
A_v=-g_mR_D
```

Considerando la resistencia de salida,

```math
A_v=-g_m(R_D||r_o)
```

El signo negativo indica una inversión de fase de 180° entre la entrada y la salida.

---

# Resistencia de entrada

Como el terminal Gate está aislado por una capa de óxido,

```math
i_G\approx0
```

Por tanto, la resistencia de entrada es extremadamente alta.

Si existe un divisor de polarización,

```math
R_{in}\approx R_1||R_2
```

---

# Resistencia de salida

En un amplificador Source Común,

```math
R_{out}\approx R_D||r_o
```

Si `r_o` es muy grande,

```math
R_{out}\approx R_D
```

---

# Capacitores

**Capacitor de entrada:** aísla la polarización DC de la etapa anterior.

**Capacitor de salida:** elimina la componente DC presente en el terminal Drain.

**Capacitor de bypass:** colocado en paralelo con `R_S`, elimina la degeneración en Source para señales AC y aumenta la ganancia.

---

# Respuesta en frecuencia

A bajas frecuencias la ganancia disminuye debido a los capacitores de acople.

```math
f_c=\frac{1}{2\pi RC}
```

A altas frecuencias aparecen las capacitancias parásitas:

- `Cgs`
- `Cgd`
- `Cdb`

La capacitancia `Cgd` produce el efecto Miller.

---

# Resumen

| Parámetro | Expresión |
|-----------|-----------|
| Corriente incremental | `id = gm·vgs` |
| Transconductancia | `gm = 2ID/VOV` |
| Resistencia de salida | `ro = 1/(λID)` |
| Modelo T | `1/gm` |
| Ganancia | `Av = -gmRD` |
| Ganancia completa | `Av = -gm(RD||ro)` |
| Rin | Muy alta |
| Rout | `RD||ro` |

## Referencias

[1] Sedra & Smith, *Microelectronic Circuits*.

[2] Razavi, *Fundamentals of Microelectronics*.
