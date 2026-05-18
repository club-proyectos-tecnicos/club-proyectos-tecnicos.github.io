---
title: "Movimiento Browniano"
date: 2026-05-18
slug: "movimiento-browniano"
aliases:
  - "/projects/smart-rail-monitoring/"
  - "/projects/modelizacion-browniana-precios-financieros/"
description: "Comparacion empirica entre precios reales y simulaciones basadas en movimiento browniano geometrico."
summary: "Proyecto teorico-computacional para estudiar movimiento browniano, lema de Ito, simulacion GBM y contraste con activos reales."
status: "Analisis teorico y experimental"
tags:
  - "Python"
  - "NumPy"
  - "pandas"
  - "Simulacion"
  - "Procesos estocasticos"
  - "Finanzas cuantitativas"
  - "Monte Carlo"
team: "Giancarlo Vargas, Rafael Laria y Nikolai Ilin"
image: "/proyectos/movimiento-browniano/imagenes/results_SPY.png"
---

## Resumen

**Movimiento Browniano** es un proyecto teorico-computacional centrado en comparar trayectorias reales de precios financieros con simulaciones basadas en el **movimiento browniano geometrico**.

El objetivo es estudiar hasta que punto un modelo clasico de matematicas financieras puede reproducir la evolucion de activos reales y, sobre todo, detectar donde falla: colas pesadas, clustering de volatilidad, asimetria en los retornos o memoria temporal.

El proyecto trabaja con la base matematica del movimiento browniano, la variacion cuadratica y el lema de Ito, y la conecta con simulaciones y contrastes estadisticos sobre activos como SPY, BTC-USD y AAPL.

<div class="project-kpis">
  <div>
    <span>GBM</span>
    <p>modelo browniano geometrico como referencia matematica</p>
  </div>
  <div>
    <span>Ito</span>
    <p>base teorica para derivar la solucion exacta del modelo</p>
  </div>
  <div>
    <span>3 activos</span>
    <p>SPY, BTC-USD y AAPL como casos de comparacion</p>
  </div>
</div>

<figure>
  <img src="/proyectos/movimiento-browniano/imagenes/results_SPY.png" alt="Estudio GBM para SPY con simulacion, retornos, QQ-plot y autocorrelacion">
  <figcaption>Comparacion para SPY: precio real frente a banda de simulacion GBM y diagnosticos sobre retornos.</figcaption>
</figure>

## Problema

Los precios financieros se mueven de forma irregular, con fluctuaciones que parecen aleatorias. El movimiento browniano geometrico es uno de los modelos clasicos para describir esa evolucion, porque mantiene precios positivos y modela retornos logaritmicos mediante una distribucion normal.

En mercados reales aparecen fenomenos que el modelo ideal no recoge completamente: eventos extremos mas frecuentes, volatilidad agrupada en periodos de tension, asimetria entre subidas y caidas y posibles patrones de memoria temporal.

El problema del proyecto es analizar esa diferencia entre modelo y datos reales. No basta con generar trayectorias visualmente parecidas; hay que comprobar que propiedades captura el modelo y cuales quedan fuera.

## Objetivo

El proyecto busca construir una base teorica y experimental para:

- explicar el movimiento browniano y su papel en finanzas;
- derivar la solucion del movimiento browniano geometrico mediante el lema de Ito;
- simular trayectorias de precios con Monte Carlo;
- comparar trayectorias simuladas con precios reales;
- analizar retornos, colas, normalidad y volatilidad;
- interpretar las limitaciones del modelo GBM frente al mercado real.

## Enfoque

El trabajo parte de la teoria probabilistica elemental y avanza hacia procesos estocasticos, movimiento browniano, variacion cuadratica y calculo de Ito.

Una idea clave es que el movimiento browniano es continuo pero no diferenciable. Su variacion cuadratica no desaparece, y por eso en calculo estocastico aparece la regla informal:

```text
(dW_t)^2 = dt
```

Esa propiedad lleva al lema de Ito. Aplicado al movimiento browniano geometrico, permite obtener la solucion:

```text
S_t = S_0 * exp[(mu - 1/2 sigma^2)t + sigma W_t]
```

La correccion `-1/2 sigma^2` es esencial: representa el efecto de la volatilidad sobre el crecimiento logaritmico del precio.

## Resultados visuales

Las graficas del proyecto comparan el precio real con una banda de simulaciones GBM y muestran diagnosticos sobre los retornos: distribucion, QQ-plot y autocorrelacion de retornos al cuadrado.

<figure>
  <img src="/proyectos/movimiento-browniano/imagenes/results_BTC_USD.png" alt="Estudio GBM para BTC-USD con simulacion, retornos, QQ-plot y autocorrelacion">
  <figcaption>BTC-USD muestra un comportamiento mas volatil y con desviaciones visibles respecto a la normalidad ideal del modelo.</figcaption>
</figure>

<figure>
  <img src="/proyectos/movimiento-browniano/imagenes/results_AAPL.png" alt="Estudio GBM para AAPL con simulacion, retornos, QQ-plot y autocorrelacion">
  <figcaption>AAPL permite observar diferencias entre una accion individual y el comportamiento agregado de un ETF como SPY.</figcaption>
</figure>

## Tecnologias utilizadas

El proyecto utiliza herramientas habituales de analisis cuantitativo:

- **Python** como lenguaje principal;
- **NumPy** para simulacion numerica;
- **pandas** para series temporales;
- **matplotlib** para visualizacion;
- **yfinance** para obtener datos de mercado;
- tests estadisticos para estudiar normalidad, colas y volatilidad.

## Limitaciones

El movimiento browniano geometrico es un modelo simplificado. Supone retornos logaritmicos normales, volatilidad constante e independencia temporal, hipotesis que suelen fallar en mercados reales.

Por eso el proyecto no se presenta como herramienta de prediccion financiera ni como sistema de trading. Su valor esta en usar el modelo como referencia matematica, contrastarlo con datos reales y justificar cuando hacen falta modelos mas sofisticados.

## Archivos del proyecto

Las imagenes y graficas propias del proyecto se organizan en:

- `/proyectos/movimiento-browniano/imagenes/results_SPY.png`;
- `/proyectos/movimiento-browniano/imagenes/results_BTC_USD.png`;
- `/proyectos/movimiento-browniano/imagenes/results_AAPL.png`.

Este proyecto no tiene memoria PDF publicada por ahora.
