

<h1 align="center">
    <a href="#">
    <img width="60%" src="/img/pulse_power/P.E.M. Original Logo 4K.jpg"/>
    </a>
</h1>

<p align="center">
  <i align="center">Proyecto de investigación enfocado en el diseño y construcción de pulsos electromagnéticos</i>
</p>


## Introducción

Proyecto de investigación enfocado en el diseño y construcción de una fuente de alta tensión y un generador de Marx. Incluye simulación, implementación experimental, análisis eléctrico, control de costos y documentación continua para aplicaciones académicas en ingeniería eléctrica.

<details open>
<summary>
 Features
</summary> <br />

<p align="center">
    <img width="49%" src="/img/readme/2d.png" alt="2d"/>
&nbsp;
    <img width="49%" src="/img/readme/3d.png" alt="3d"/>
</p>

<p align="center">
    <img width="49%" src="/img/readme/Soladadura 004.jpg" alt="sold"/>
&nbsp;
    <img width="49%" src="/img/readme/electro circuits.jpeg" alt="electro"/>
</p> 
    

</details>

---

## 🧠 Arquitectura del sistema

```mermaid
flowchart LR
A[Fuente 12V CC] --> B[Conmutación ZVS]
B --> C[Transformación Flyback]
C --> D[Rectificación HV]
D --> E[Generador Marx]
E --> F[Pulso ≈13kV]
```

---

## Tabla de Contenidos

- **Documentación**
  - **Componentes**
    - **MOSFET**-
      - [Introducción (En proceso  :) yei)](./docs/Components/MOSFET/Introduction.md)
      - [Polarización](./docs/Components/MOSFET/polarize.md)
      - [Comportamiento en AC (En proceso)](./docs/Components/MOSFET/ac.md)
    - [Circuito Oscilador 555](./docs/Components/555.md)
  - **Electrónica**
    - [Flip Flop](./docs/Electronic/Flip%20Flop.md)
  - **Matemáticas**
    - [Matemática Avanzada](./docs/Mathematics/advanced_math.md)
    - [Teoría de la Integración](./docs/Mathematics/integration_theory.md)
    - [Teoremas de Utilidad](./docs/Mathematics/utility_theorems.md)
    - [Teoría de la Vectorización](./docs/Mathematics/vector_theory.md)
  - **Física**
    - [Ecuaciones de Maxwell](./docs/Physics/maxwell_eqs.md)
    - [Semiconductores](./docs/Physics/semiconductors.md)
  - **Electrónica de Potencia**
    - [Conversión CC-CC](./docs/Power%20Electronic/Regulation/CC%20-%20CC.md)
    - **Zero Voltage Switching**
      - [Introducción al ZVS](./docs/Power%20Electronic/Zero%20Voltage%20Conmutation/Introduction.md)
  
  - **Simulaciones**
   - [Conmutación Tradicional](./docs/Simulations/traditional_conmutation.md)

---

## 🔬 Simulación
Disponibles en la carpeta [./sim](./sim/), con la siguiente Tabla de Contenidos:

- **sim**
  - **img**
  - **models**
    - [IRF640.model](./sim/models/IRF640.model)
  - **schematics**
    - **Conmutation**
      - **555**
        - [Flyback 555.asc](./sim/schematics/Conmutation/555/Flyback%20555.asc)
        - [Flyback 555.sch](./sim/schematics/Conmutation/555/Flyback%20555.sch)
        - [Flyback 555.txt](./sim/schematics/Conmutation/555/Flyback%20555.txt)
      - **Traditional**
    - [zvs.asc](./sim/schematics/zvs.asc)

---


---


## 📚 Bibliografía

Ver:
Esto no es bibliografia, ni siquiera existe el archivo, me voy a quejar con el admin

📄 `referencias/bibliografia.md`

---

## 👥 Integrantes

* William A. Bohorquez
* Diego L. Mahecha
* Heidy G. Morales
* Jorge A. Torres
---

