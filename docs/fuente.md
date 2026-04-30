#  Fuente de Alta Tensión para Generador de Marx (≈13 kV)

##  Descripción

Este proyecto desarrolla una fuente de alta tensión basada en una entrada de 12 V CC, diseñada para alimentar un generador de Marx en etapas posteriores. El sistema convierte, eleva y rectifica la energía eléctrica hasta alcanzar niveles de kilovoltios.

---

##  Arquitectura del sistema

```mermaid
flowchart LR
A[Fuente 12V CC] --> B[Conmutación ZVS]
B --> C[Transformación Flyback]
C --> D[Rectificación HV]
D --> E[Salida HV]
```

---

##  Etapas del sistema

###  Fuente primaria (12 V CC)

| Parámetro             | Valor típico |
| --------------------- | ------------ |
| Tensión nominal       | 12 V         |
| Corriente recomendada | 5 A – 15 A   |

**Función:** suministrar potencia de entrada al sistema.

---

###  Conmutación ZVS

| Parámetro    | Valor típico    |
| ------------ | --------------- |
| Topología    | Resonante       |
| Frecuencia   | 20 kHz – 60 kHz |
| Dispositivos | MOSFETs         |

![Esquematico de una fuente zvs](/simulaciones/Esquematicode-ZVS.png)


**Función:** convertir corriente continua en señal de alta frecuencia para excitar el transformador.

**Simulación LTspice:** [zns.asc](/simulaciones/zvs.asc)

---

###  Transformador Flyback

| Parámetro           | Descripción           |
| ------------------- | --------------------- |
| Núcleo              | Ferrita               |
| Relación de espiras | Alta                  |
| Salida              | Alta tensión pulsante |

**Función:** elevar el nivel de tensión mediante acoplamiento magnético.

---

###  Rectificación de Alta Tensión

| Elemento     | Función           |
| ------------ | ----------------- |
| Diodo HV     | Rectificación     |
| Capacitor HV | Filtrado opcional |

**Función:** convertir la señal pulsante en una salida de alta tensión continua.

**Resultados experimentales:**

![Datos de salida](/simulaciones/20260423_152109.png)

![Salida de alta tensión](/simulaciones/20260423_152220.png)

---

##  Salida del sistema

| Parámetro        | Valor                  |
| ---------------- | ---------------------- |
| Voltaje estimado | ≈ 13 kV                |
| Tipo de señal    | Continua (rectificada) |

---

##  Simulación

* Archivo: `zns.asc`
* Herramienta: LTspice
* Análisis de la etapa ZVS y comportamiento del sistema

## Piezas 

### 📦 Lista de Piezas - Fuente Alta

### 🔽 Ver componentes

<details>
<summary>Cobre 14 AWG</summary>

![Cobre 14AWG](docs/Piezas_fuente_alta/Cobre-14AWG.png)

</details>

<details>
<summary>Condensador 1 µF</summary>

![Condensador 1uF](docs/Piezas_fuente_alta/Condensador1uf.png)

</details>

<details>
<summary>Condensador 2 µF</summary>

![Condensador 2uF](docs/Piezas_fuente_alta/Condensador2uFZ.png)

</details>

<details>
<summary>Condensador 4.7 µF</summary>

![Condensador 4u7](docs/Piezas_fuente_alta/Condensador4U7.png)

</details>

<details>
<summary>Diodo 1N5817</summary>

![Diodo 1N5817](docs/Piezas_fuente_alta/Diodo%201N5817.png)

</details>

<details>
<summary>Fuente Conmutada</summary>

![Fuente](docs/Piezas_fuente_alta/FuenteConmutada.png)

</details>

<details>
<summary>Toroide de Ferrita</summary>

![Toroide](docs/Piezas_fuente_alta/toroideFerrita.jpg)

</details>

<details>
<summary>Transformador Flyback</summary>

![Flyback](docs/Piezas_fuente_alta/TransformadorFlyback.png)

</details>

<details>
<summary>Transistor IRF640N</summary>

![IRF640N](docs/Piezas_fuente_alta/TransistoirIRF640N.jpg)

</details>

<details>
<summary>Transistor 2N7000</summary>

![2N7000](docs/Piezas_fuente_alta/Transistor-2n7000.png)

</details>

