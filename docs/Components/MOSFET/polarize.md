
# `docs/Components/MOSFET/polarize.md`

# Polarización del MOSFET

## ¿Por qué polarizar un MOSFET?

Después de estudiar el funcionamiento del MOSFET surge una pregunta natural: ¿cómo hacemos para que el transistor trabaje exactamente en la región que nos interesa?

La respuesta es la **polarización**.

Polarizar un transistor consiste en fijar las tensiones y corrientes de corriente continua (DC) de tal manera que el dispositivo opere en un punto específico llamado **Punto de Operación** o **Punto Q (Quiescent Point)**.

En aplicaciones de conmutación normalmente interesa que el transistor esté completamente apagado o completamente encendido. Sin embargo, en amplificadores la situación cambia completamente: el MOSFET debe permanecer en la **región de saturación**, pues únicamente allí la corriente depende principalmente de la tensión de compuerta.

---

## El punto de operación (Q)

El punto Q representa los valores de corriente y tensión cuando no existe señal de entrada.

Generalmente está definido por:

- Corriente de drenador: `I_D`
- Tensión drenador-fuente: `V_DS`
- Tensión compuerta-fuente: `V_GS`

La señal de entrada hará oscilar al transistor alrededor de este punto.

Si el punto Q está mal elegido, la señal sufrirá recortes (clipping) y aparecerá distorsión.

---

## Regiones de operación

Para un MOSFET de enriquecimiento NMOS:

### Corte

```math
V_{GS}<V_{TH}
```

No existe canal.

```math
I_D\approx0
```

---

### Región Tríodo

```math
V_{GS}>V_{TH}
```

y

```math
V_{DS}<V_{GS}-V_{TH}
```

La corriente viene dada por

```math
I_D=k\left[2(V_{GS}-V_{TH})V_{DS}-V_{DS}^2\right]
```

Aquí el transistor se comporta aproximadamente como una resistencia controlada por tensión.

---

### Saturación

```math
V_{GS}>V_{TH}
```

y

```math
V_{DS}\ge V_{GS}-V_{TH}
```

Entonces

```math
I_D=k(V_{GS}-V_{TH})^2
```

Esta es la región utilizada para amplificación.

---

# Polarización fija

Es la configuración más sencilla.

El terminal Gate recibe una tensión fija mediante una fuente independiente.

La ecuación principal es

```math
V_{GS}=V_G
```

Luego,

```math
I_D=k(V_{GS}-V_{TH})^2
```

y

```math
V_{DS}=V_{DD}-I_DR_D
```

## Ventajas

- Muy simple.
- Fácil de analizar.

## Desventajas

- Muy sensible a cambios de temperatura.
- Depende fuertemente de la dispersión del parámetro VTH.

---

# Polarización con resistencia en Source (Self Bias)

Al añadir una resistencia en la fuente aparece un fenómeno muy importante llamado **realimentación negativa**.

Cuando la corriente aumenta:

- aumenta la caída de tensión en RS;
- aumenta VS;
- disminuye VGS;
- disminuye ID.

El circuito se estabiliza automáticamente.

Las ecuaciones son

```math
V_S=I_DR_S
```

```math
V_{GS}=V_G-I_DR_S
```

```math
I_D=k(V_G-I_DR_S-V_{TH})^2
```

Este circuito es muchísimo más estable que la polarización fija.

---

# Polarización mediante divisor de tensión

Es probablemente la configuración más utilizada en amplificadores discretos.

La tensión de compuerta se fija mediante dos resistencias.

```math
V_G=V_{DD}\frac{R_2}{R_1+R_2}
```

Posteriormente

```math
V_{GS}=V_G-I_DR_S
```

Finalmente

```math
V_{DS}=V_{DD}-I_DR_D-I_DR_S
```

## Ventajas

- Excelente estabilidad.
- Poco sensible a cambios del transistor.
- Muy utilizada en diseño práctico.

---

# Polarización mediante fuente de corriente

En circuitos integrados es muy común reemplazar la resistencia de Source por una fuente de corriente.

Esto permite mantener prácticamente constante la corriente del transistor incluso cuando existen variaciones de temperatura.

Es la técnica más estable, aunque también la más compleja.

---

# Comparación

| Método | Estabilidad | Complejidad | Aplicación |
|---------|------------|------------|------------|
| Polarización fija | Baja | Muy baja | Laboratorio |
| Self Bias | Buena | Baja | Amplificadores |
| Divisor de tensión | Muy buena | Media | Diseño general |
| Fuente de corriente | Excelente | Alta | Circuitos integrados |

---

# Procedimiento de diseño

1. Elegir la corriente ID.
2. Elegir VDS aproximadamente igual a VDD/2.
3. Calcular RD.
4. Calcular RS.
5. Diseñar el divisor de tensión.
6. Verificar que

```math
V_{DS}>V_{GS}-V_{TH}
```

para garantizar la región de saturación.

---

# Comentario final

La polarización constituye el primer paso en el diseño de cualquier amplificador MOSFET. Un circuito correctamente polarizado mantiene un punto de operación estable frente a variaciones de temperatura, tolerancias de fabricación y cambios en los parámetros del dispositivo, garantizando así un funcionamiento lineal y una menor distorsión de la señal.

## Referencias

[1] Sedra & Smith, *Microelectronic Circuits*.

[2] Boylestad, *Electronic Devices and Circuit Theory*.

[3] Razavi, *Fundamentals of Microelectronics*.
