# Fuente de Alta Tensión

## Descripción

La fuente de alta tensión es la etapa encargada de generar el voltaje necesario para la carga del generador de Marx. Parte de una fuente de 12 V CC y, mediante conversión y elevación, alcanza niveles de alta tensión.

## Arquitectura
```mermaid
flowchart LR
A[Fuente 12V CC] --> B[Conmutación ZVS]
B --> C[Transformación Flyback]
C --> D[Rectificación HV]
```

---

##  Descripción por Etapas

### Fuente Primaria de Energía (12V CC)

| Parámetro | Valor típico |
|---|---|
| Tensión nominal | 12 V |
| Corriente recomendada | 5 A – 15 A |

**Función:** suministrar potencia de entrada al sistema.

### Etapa de Conmutación ZVS

| Parámetro | Valor típico |
|---|---|
| Topología | Resonante |
| Frecuencia | 20 kHz – 60 kHz |
| Dispositivos | MOSFETs |


![Esquematico del circuito zvs](Esquematicode-ZVS.png)

**Función:** convertir corriente continua en señal de alta frecuencia para excitar el transformador.
#### Simulación LTspice : [marx_generator.asc](./zns.asc)

###  Etapa Elevadora Flyback

| Parámetro | Descripción |
|---|---|
| Núcleo | Ferrita |
| Relación de espiras | Alta |
| Salida | Alta tensión pulsante |

**Función:** elevar el nivel de tensión mediante acoplamiento magnético.

###  Etapa Elevadora Flyback
---

### Rectificación de Alta Tensión


| Elemento | Función |
|---|---|
| Diodo HV | Rectificación |
| Capacitor HV | Filtrado opcional |

**Salida estimada:** 
![Datos Salida de el conjunto de Alta Tension](20260423_152109.png)

![Salida de el conjunto de Alta Tension](20260423_152220.png)
---

### Etapa de Carga del Generador Marx

- Resistencias limitadoras de corriente  
- Capacitores por etapa  
- Carga en paralelo  
- Descarga en serie

---

### Salida Pulsada

| Parámetro | Valor |
|---|---|
| Voltaje pico estimado | ≈13 kV |
| Duración | Corta |
| Naturaleza | Impulso |

---
