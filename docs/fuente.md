# Fuente de Alta Tensión

## Descripción

La fuente de alta tensión es la etapa encargada de generar el voltaje necesario para la carga del generador de Marx. Parte de una fuente de 12 V CC y, mediante conversión y elevación, alcanza niveles de alta tensión.

## Arquitectura

```mermaid
flowchart LR
A[Fuente 12V CC] --> B[Conmutación ZVS]
B --> C[Transformación Flyback]
C --> D[Rectificación HV]