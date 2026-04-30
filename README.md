# PEM
Proyecto de investigación enfocado en el diseño y construcción de una fuente de alta tensión y un generador de Marx. Incluye simulación, implementación experimental, análisis eléctrico, control de costos y documentación continua para aplicaciones académicas en ingeniería eléctrica.

# ⚡ Sistema de Generación de Pulsos de Alta Tensión (≈13 kV)

## 📌 Descripción

Proyecto de investigación orientado al diseño y construcción de una fuente de alta tensión como etapa base para un generador de Marx. El sistema permite generar pulsos de alto voltaje mediante la conversión, elevación y almacenamiento de energía eléctrica.

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

## 📂 Documentación técnica

Toda la documentación detallada está organizada en la carpeta `docs/`:

* 🔌 [Fuente de alta tensión](docs/fuente.md)
* ⚡ [Generador de Marx](docs/generador_marx.md)
* 📘 [Fundamentos teóricos](docs/teoria.md)

---

## 🔬 Simulación

* [Archivo LTspice circuito ZVS](simulaciones/zvs.asc)

---

## 📓 Bitácora del proyecto

### Estado actual

* Desarrollo de la fuente de alta tensión

### Tareas pendientes


---

## 💰 Control de costos

El registro de componentes y gastos se encuentra en:

📄 `costos/costos.csv`

---

## 📚 Bibliografía

Ver:

📄 `referencias/bibliografia.md`

---

## 👥 Integrantes

* William A. Bohorquez
* (Agregar integrantes)

---

## ⚠️ Seguridad

Este proyecto trabaja con **alta tensión (kV)**, lo cual implica riesgos graves.

* No manipular energizado
* Usar aislamiento adecuado
* Realizar pruebas en condiciones controladas

---

## 🚀 Estado del proyecto

🟡 En desarrollo — etapa de fuente de alta tensión
