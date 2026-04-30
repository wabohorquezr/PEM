
---

# 📁 `docs/generador_marx.md`

```md
# Generador de Marx

## Descripción

El generador de Marx es un circuito utilizado para generar pulsos de muy alta tensión a partir de una fuente de menor voltaje. Funciona mediante la carga en paralelo y descarga en serie de capacitores.

## Principio de funcionamiento

1. Los capacitores se cargan en paralelo.
2. Al activarse el sistema, se conectan en serie.
3. Se genera un pulso de alta tensión en la salida.

## Etapa de carga

- Resistencias limitadoras de corriente  
- Capacitores por etapa  
- Fuente de alta tensión  

## Etapa de descarga

- Conmutación (chispa o switch)  
- Descarga en serie  

## Parámetros esperados

| Parámetro | Valor |
|---|---|
| Voltaje de salida | ≈ 13 kV |
| Tipo de señal | Pulso |
| Duración | Corta |

## Aplicación en el proyecto

El generador de Marx será alimentado por la fuente de alta tensión desarrollada en este repositorio.