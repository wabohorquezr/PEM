# Funcionamiento del Generador de Marx y sus Ecuaciones Fundamentales

Este repositorio detalla el funcionamiento técnico del **Generador de Marx**, basado en principios de potencia pulsada para la generación de pulsos de alta tensión.

##  Funcionamiento Básico
El generador opera bajo el principio de **carga en paralelo y descarga en serie**.
- **Carga:** Una fuente de tensión $U_0$ carga $n$ capacitores a través de una red de resistencias $R_L$ [1].
- **Erección (Disparo):** Al cerrarse los interruptores (spark gaps), los capacitores se conectan en serie, sumando sus tensiones casi instantáneamente [1].

---

##  Ecuaciones de Diseño y Operación

### A. Tensión de Salida
En un generador ideal de $n$ etapas, la tensión máxima de salida ($U_{out}$) es:
$$U_{out} = n \cdot U_0$$

###  Tiempo de Carga entre Etapas
Debido a la conexión resistiva, cada etapa se carga a una velocidad distinta. La constante de tiempo para la etapa $n$ es [2]:
$$\tau_n = R_L \cdot C_0 \cdot n^2$$

La diferencia de tensión ($\Delta U_0$) entre la primera y la última etapa tras un tiempo $t$ se calcula como [3]:
$$\frac{\Delta U_0}{U_0} = \frac{R_L \cdot C_0 \cdot n^2}{t}$$

###  Sobretensión en los Gaps (Erección)
Para garantizar que todos los interruptores se cierren, es necesaria una sobretensión ($\Delta U$). Considerando la capacitancia de la brecha ($C_g$) y la parásita a tierra ($C_s$), la tensión en el segundo gap es [4]:
$$\Delta U = \frac{2U_0}{1 + C_g / C_s}$$

Si se disparan simultáneamente las primeras $k$ etapas, la sobretensión en la etapa $k+1$ es [4]:
$$\Delta U = k \cdot U_0 \frac{2}{1 + \sqrt{1 + 4 C_g / C_s}}$$

---

##  Parámetros de Almacenamiento de Energía
- **Energía Almacenada ($W_C$):** $\frac{1}{2} C U^2$ [5].
- **Corriente Pico ($I_p$):** Está limitada por la inductancia $L$ del sistema: $I_p = U \sqrt{C/L}$ [6].


# Diseño Técnico: Generador de Marx de 4 Etapas (20 kV)

Este documento detalla el diseño y los cálculos fundamentales para un **Generador de Marx** configurado para una salida de alta tensión, optimizado para producir arcos eléctricos funcionales.

## 1. Parámetros de las Etapas y Tensión de Carga

El principio fundamental de este generador, patentado por Erwin Marx en 1923, consiste en cargar capacitores en paralelo para luego conmutarlos a una configuración en serie durante la descarga [1].

*   **Voltaje de salida deseado ($U_{out}$):** 20 kV
*   **Número de etapas ($n$):** 4
*   **Capacitancia por etapa ($C_0$):** 2 nF
*   **Cálculo del voltaje de carga ($U_0$):**
    $$U_0 = \frac{U_{out}}{n} = \frac{20\text{ kV}}{4} = \mathbf{5\text{ kV}}$$

Cada capacitor debe cargarse a un potencial de **5 kV** mientras los interruptores permanecen abiertos [1].

##  Cálculo de las Resistencias de Carga ($R_L$)

Debido a que los capacitores se cargan a través de una cadena serie de resistencias, cada etapa se carga a una velocidad distinta [2]. La constante de tiempo de carga para la **etapa $n$** es:
$$\tau_n = R_L C_0 n^2$$

### Determinación del valor óhmico para 1 Hz
Para una operación repetitiva estable (aprox. 1 disparo por segundo), calculamos el valor de $R_L$ asumiendo una diferencia de tensión tolerable ($\Delta U_0/U_0$) del **2% (0.02)** entre el primer y el último capacitor [3]:

$$R_L = \frac{t \cdot 0.02}{C_0 \cdot n^2} = \frac{1\text{ s} \cdot 0.02}{(2 \times 10^{-9}\text{ F}) \cdot 16} = \mathbf{625\text{ k}\Omega}$$

**Recomendación:** Utilizar resistencias de **680 k$\Omega$ o 1 M$\Omega$** de alta tensión (composición de carbón o cerámicas) [2, 4].

##  Energía y Dinámica del Pulso

*   **Energía Almacenada ($W_M$):** La energía total disponible en el arco es la suma de la energía de cada capacitor ($W_C = \frac{1}{2} C U^2$) [5]:
    $$W_M = 4 \cdot \left( \frac{1}{2} \cdot 2\text{ nF} \cdot (5\text{ kV})^2 \right) = \mathbf{0.1\text{ Julios}}$$
*   **Corriente Pico ($I_{max}$):** Está limitada por la inductancia interna ($L$) y la resistencia ($R$) del sistema erigido [6]:
    $$I_{max} \approx \frac{U_0}{(L/C)^{1/2} + 0.8 R}$$
*   **Tiempo de Erección:** El proceso completo de conexión en serie ocurre normalmente en el orden de un **microsegundo** [1].

