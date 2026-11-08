# Optimización del tamaño de paquete (MTU) en redes

Proyecto Final — Cálculo Diferencial, Universidad de La Salle (Tema 15).

**Autores:** Juan Andres Daza, Alejandro Garcia Vega , Juan David Espitia Gutiérrez

Este repositorio contiene el código que reproduce todos los resultados del artículo: el modelo de eficiencia
$E(S)$, el tamaño óptimo de paquete $S^*$ obtenido con $dE/dS = 0$, la simulación Monte Carlo con barras de
error y la propagación de la incertidumbre de la tasa de error de bit (BER).

## Cómo reproducir

**En Google Colab:** abrir `MTU_optimo.ipynb` y ejecutar *Entorno de ejecución → Ejecutar todas*.

**En local:**

```bash
pip install -r requirements.txt
jupyter notebook MTU_optimo.ipynb
```

La semilla aleatoria está fija (`SEED = 2026`), así que los números y las figuras salen idénticos en cada
ejecución.

## Contenido

| Archivo | Qué es |
|---|---|
| `MTU_optimo.ipynb` | Notebook con todo el análisis, ya ejecutado |
| `figuras/` | Las tres figuras del artículo (se regeneran al correr el notebook) |
| `resultados/tabla_optimos.csv` | $S^*$ por cuatro métodos para cada BER |
| `resultados/montecarlo.csv` | Eficiencia simulada (media y desviación) frente a la teórica |
| `requirements.txt` | Dependencias de Python |

## Modelo

Un paquete tiene $S$ bytes de datos y $H$ bytes de encabezado. Con tasa de error de bit $p$, el paquete
llega intacto con probabilidad $e^{-\beta(S+H)}$, donde $\beta = -8\ln(1-p)$. La eficiencia es

$$E(S) = \frac{S}{S+H}\, e^{-\beta(S+H)}$$

y el tamaño óptimo, de $dE/dS = 0$, es

$$S^* = \frac{-H + \sqrt{H^2 + 4H/\beta}}{2}.$$

## Uso de inteligencia artificial

El código de este repositorio se desarrolló con asistencia de una herramienta de inteligencia artificial
(Claude, de Anthropic), conforme a la Declaración de Uso de IA de la Universidad de La Salle
(Anexo ACA 018 de 2025). Los autores revisaron, ejecutaron y validaron todos los resultados.
