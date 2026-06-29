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

**Nota** : Requiere tener un Toroide que comercialmete no se consiguio con el alambrado correspondeiente por lo que la  mejor opcion podria ser el calculo del mismo:

suponiendo un μr≈800

serian 13 vueltas 
y o.5 m de el alambre (14AWG)

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
## Lista de Piezas - Fuente Alta

### 🔽 Componentes

---

<details>
<summary><b>Cobre 14 AWG</b></summary>

| 🖼️ Imagen                                   | 📄 Descripción           |
| -------------------------------------------- | ------------------------ |
| ![](/docs/Piezas_fuente_alta/Cobre-14AWG.png) | **Tipo:** Cable de cobre |
| **Calibre:** 14 AWG                          |                          |
| **Diámetro conductor:** ~1.63 mm             |                          |
| **Diámetro con esmalte:** ~1.7–1.8 mm        |                          |
| **Uso:** Bobinados                           |                          |

</details>

---

<details>
<summary><b>Condensador 1 µF</b></summary>

| 🖼️ Imagen                                      | 📄 Descripción         |
| ----------------------------------------------- | ---------------------- |
| ![](/docs/Piezas_fuente_alta/Condensador1uf.png) | **Capacitancia:** 1 µF |
| **Tipo:** Poliéster                             |                        |
| **Dimensiones:** ~10 × 6 × 12 mm                |                        |
| **Pitch:** ~5 mm                                |                        |
| **Uso:** Filtrado                               |                        |

</details>

---

<details>
<summary><b>Condensador 2 µF</b></summary>

| 🖼️ Imagen                                       | 📄 Descripción         |
| ------------------------------------------------ | ---------------------- |
| ![](/docs/Piezas_fuente_alta/Condensador2uFZ.png) | **Capacitancia:** 2 µF |
| **Tipo:** Película                               |                        |
| **Dimensiones:** ~18 × 8 × 14 mm                 |                        |
| **Pitch:** ~10 mm                                |                        |
| **Uso:** Resonancia                              |                        |

</details>

---

<details>
<summary><b>Condensador 4.7 µF</b></summary>

| 🖼️ Imagen                                      | 📄 Descripción           |
| ----------------------------------------------- | ------------------------ |
| ![](/docs/Piezas_fuente_alta/Condensador4U7.png) | **Capacitancia:** 4.7 µF |
| **Tipo:** MKP                                   |                          |
| **Dimensiones:** ~26 × 12 × 18 mm               |                          |
| **Pitch:** ~15–22.5 mm                          |                          |
| **Uso:** Tanque resonante                       |                          |

</details>

---

<details>
<summary><b>Diodo 1N5817</b></summary>

| 🖼️ Imagen                                      | 📄 Descripción     |
| ----------------------------------------------- | ------------------ |
| ![](/docs/Piezas_fuente_alta/Diodo%201N5817.png) | **Tipo:** Schottky |
| **Encapsulado:** DO-41                          |                    |
| **Longitud:** ~5.2 mm                           |                    |
| **Diámetro:** ~2.7 mm                           |                    |
| **Uso:** Rectificación                          |                    |

</details>

---

<details>
<summary><b>Fuente Conmutada</b></summary>

| 🖼️ Imagen                                       | 📄 Descripción           |
| ------------------------------------------------ | ------------------------ |
| ![](/docs/Piezas_fuente_alta/FuenteConmutada.png) | **Entrada:** 110–220V AC |
| **Salida:** 12V DC                               |                          |
| **Dimensiones:** ~110 × 78 × 36 mm               |                          |
| **Uso:** Alimentación                            |                          |

</details>

---

<details>
<summary><b>Toroide de Ferrita</b></summary>

| 🖼️ Imagen                                      | 📄 Descripción        |
| ----------------------------------------------- | --------------------- |
| ![](/docs/Piezas_fuente_alta/toroideFerrita.jpg) | **Material:** Ferrita |
| **Diámetro exterior:** ~30–50 mm                |                       |
| **Diámetro interior:** ~15–25 mm                |                       |
| **Altura:** ~10–20 mm                           |                       |
| **Uso:** Inductor                               |                       |

</details>

---

<details>
<summary><b>Transformador Flyback</b></summary>

| 🖼️ Imagen                                            | 📄 Descripción         |
| ----------------------------------------------------- | ---------------------- |
| ![](/docs/Piezas_fuente_alta/TransformadorFlyback.png) | **Tipo:** Alta tensión |
| **Dimensiones:** ~60 × 40 × 30 mm                     |                        |
| **Uso:** Generación de kV                             |                        |

</details>

---

<details>
<summary><b>Transistor IRF640N</b></summary>

| 🖼️ Imagen                                          | 📄 Descripción   |
| --------------------------------------------------- | ---------------- |
| ![](/docs/Piezas_fuente_alta/TransistoirIRF640N.jpg) | **Tipo:** MOSFET |
| **Encapsulado:** TO-220                             |                  |
| **Altura:** ~15 mm                                  |                  |
| **Ancho:** ~10 mm                                   |                  |
| **Uso:** Potencia                                   |                  |

</details>

---

<details>
<summary><b>Transistor 2N7000</b></summary>

| 🖼️ Imagen                                         | 📄 Descripción   |
| -------------------------------------------------- | ---------------- |
| ![](/docs/Piezas_fuente_alta/Transistor-2n7000.png) | **Tipo:** MOSFET |
| **Encapsulado:** TO-92                             |                  |
| **Altura:** ~5 mm                                  |                  |
| **Ancho:** ~4 mm                                   |                  |
| **Uso:** Control                                   |                  |

</details>



---
