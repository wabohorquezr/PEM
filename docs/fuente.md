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
###  Lista de Piezas - Fuente Alta

### 🔽 Componentes

---

<details>
<summary><b>Cobre 14 AWG</b></summary>

| 🖼️ Imagen                                    | 📄 Descripción                              |
| --------------------------------------------- | ------------------------------------------- |
| ![](/docs/Piezas_fuente_alta/Cobre-14AWG.png)  | **Tipo:** Cable de cobre esmaltado / sólido |
| **Calibre:** 14 AWG                           |                                             |
| **Diámetro:** ~1.63 mm                        |                                             |
| **Uso:** Bobinados (ZVS, inductores, flyback) |                                             |

</details>

---

<details>
<summary><b>Condensador 1 µF</b></summary>

| 🖼️ Imagen                                      | 📄 Descripción         |
| ----------------------------------------------- | ---------------------- |
| ![](/docs/Piezas_fuente_alta/Condensador1uf.png) | **Capacitancia:** 1 µF |
| **Tipo:** Poliéster / MKP                       |                        |
| **Voltaje típico:** 100V+                       |                        |
| **Uso:** Resonancia, filtrado                   |                        |

</details>

---

<details>
<summary><b>Condensador 2 µF</b></summary>

| 🖼️ Imagen                                       | 📄 Descripción         |
| ------------------------------------------------ | ---------------------- |
| ![](/docs/Piezas_fuente_alta/Condensador2uFZ.png) | **Capacitancia:** 2 µF |
| **Tipo:** Película                               |                        |
| **Uso:** Banco resonante (ZVS)                   |                        |

</details>

---

<details>
<summary><b>Condensador 4.7 µF</b></summary>

| 🖼️ Imagen                                      | 📄 Descripción           |
| ----------------------------------------------- | ------------------------ |
| ![](/docs/Piezas_fuente_alta/Condensador4U7.png) | **Capacitancia:** 4.7 µF |
| **Tipo:** MKP recomendado                       |                          |
| **Voltaje:** 100V–400V                          |                          |
| **Uso:** Tanque resonante                       |                          |

</details>

---

<details>
<summary><b>Diodo 1N5817</b></summary>

| 🖼️ Imagen                                      | 📄 Descripción     |
| ----------------------------------------------- | ------------------ |
| ![](/docs/Piezas_fuente_alta/Diodo%201N5817.png) | **Tipo:** Schottky |
| **Corriente:** 1A                               |                    |
| **Voltaje inverso:** 20V                        |                    |
| **Uso:** Rectificación rápida                   |                    |

</details>

---

<details>
<summary><b>Fuente Conmutada</b></summary>

| 🖼️ Imagen                                       | 📄 Descripción           |
| ------------------------------------------------ | ------------------------ |
| ![](/docs/Piezas_fuente_alta/FuenteConmutada.png) | **Entrada:** 110–220V AC |
| **Salida:** 12V DC                               |                          |
| **Uso:** Alimentación del driver ZVS             |                          |

</details>

---

<details>
<summary><b>Toroide de Ferrita</b></summary>

| 🖼️ Imagen                                      | 📄 Descripción        |
| ----------------------------------------------- | --------------------- |
| ![](/docs/Piezas_fuente_alta/toroideFerrita.jpg) | **Material:** Ferrita |
| **Inductancia típica:** 100–220 µH              |                       |
| **Uso:** Inductor del circuito ZVS              |                       |

</details>

---

<details>
<summary><b>Transformador Flyback</b></summary>

| 🖼️ Imagen                                            | 📄 Descripción         |
| ----------------------------------------------------- | ---------------------- |
| ![](/docs/Piezas_fuente_alta/TransformadorFlyback.png) | **Tipo:** Alta tensión |
| **Salida:** kV                                        |                        |
| **Uso:** Generación de alto voltaje para el Marx      |                        |

</details>

---

<details>
<summary><b>Transistor IRF640N</b></summary>

| 🖼️ Imagen                                          | 📄 Descripción   |
| --------------------------------------------------- | ---------------- |
| ![](/docs/Piezas_fuente_alta/TransistoirIRF640N.jpg) | **Tipo:** MOSFET |
| **Voltaje:** 200V                                   |                  |
| **Corriente:** 18A                                  |                  |
| **Uso:** Etapa de potencia ZVS                      |                  |

</details>

---

<details>
<summary><b>Transistor 2N7000</b></summary>

| 🖼️ Imagen                                         | 📄 Descripción           |
| -------------------------------------------------- | ------------------------ |
| ![](/docs/Piezas_fuente_alta/Transistor-2n7000.png) | **Tipo:** MOSFET pequeño |
| **Voltaje:** 60V                                   |                          |
| **Uso:** Control / driver                          |                          |

</details>

---
