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



