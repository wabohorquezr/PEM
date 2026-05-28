

<h1 align="center">
    <a href="#">
    <img src="/img/LOGO_PEM.jpg">
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
    - [MOSFET.md](./docs/Components/MOSFET.md)
  - **Matemáticas**
    - [integration_theory.md](./docs/Mathematics/integration_theory.md)
    - [utility_theorems.md](./docs/Mathematics/utility_theorems.md)
  - **Física**
    - [maxwell_eqs.md](./docs/Physics/maxwell_eqs.md)
  - [fuente.md](./docs/fuente.md)
  - [generador_marx.md](./docs/generador_marx.md)
  - [Potencia Pulsada.md](./docs/Potencia%20Pulsada.md)
  - [teoria.md](./docs/teoria.md)

---

## 🔬 Simulación

* [Archivo LTspice circuito ZVS](simulaciones/zvs.asc)

---


---


## 📚 Bibliografía

Ver:

📄 `referencias/bibliografia.md`

---

## 👥 Integrantes

* William A. Bohorquez
* Kevin A. Buitrago
* Diego L. Mahecha
* Heidy G. Morales
* Jorge A. Torres
---

