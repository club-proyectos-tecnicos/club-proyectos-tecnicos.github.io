---
title: "Modelización browniana de precios financieros"
slug: "modelizacion-browniana-precios-financieros"
description: "Comparación empírica entre trayectorias reales de mercado y simulaciones basadas en movimiento browniano geométrico."
summary: "Proyecto teórico-computacional para conectar movimiento browniano, lema de Itō, simulación Monte Carlo y arquitectura software aplicada al análisis de precios financieros."
status: "Diseño teórico y arquitectura"
tags:
  - "Python"
  - "NumPy"
  - "pandas"
  - "Simulación"
  - "Procesos estocásticos"
  - "Finanzas cuantitativas"
  - "Monte Carlo"
  - "Data Analysis"
repo: ""
memory: "/documents/memoria-browniano-ito-arquitectura.pdf"
team: ""
image: ""
---

<div class="project-cta">
  <a class="button primary" href="/documents/memoria-browniano-ito-arquitectura.pdf" target="_blank" rel="noopener">Descargar memoria completa (PDF)</a>
</div>

## Resumen

**Modelización browniana de precios financieros** es un proyecto teórico-computacional orientado a comparar trayectorias reales de precios con simulaciones basadas en el **movimiento browniano geométrico**.

El objetivo es estudiar hasta qué punto un modelo clásico de matemáticas financieras puede reproducir la evolución de activos reales y, sobre todo, detectar dónde falla: colas pesadas, clustering de volatilidad, asimetría en los retornos o memoria temporal.

La memoria desarrolla la base matemática necesaria —variables aleatorias, procesos estocásticos, movimiento browniano, variación cuadrática y lema de Itō— y propone una arquitectura software modular para cargar datos de mercado, simular trayectorias, aplicar tests estadísticos y visualizar los resultados.

No se presenta como un sistema de trading ni como una herramienta de predicción financiera en producción. Es una primera arquitectura de investigación aplicada para conectar teoría matemática, simulación Monte Carlo y análisis empírico de mercados.

<div class="project-kpis">
  <div>
    <span>GBM</span>
    <p>modelo browniano geométrico como referencia matemática</p>
  </div>
  <div>
    <span>Itō</span>
    <p>base teórica para derivar la solución exacta del modelo</p>
  </div>
  <div>
    <span>5 módulos</span>
    <p>datos, simulación, tests, modelos avanzados y visualización</p>
  </div>
</div>

## Problema

Los precios financieros se mueven de forma irregular, con fluctuaciones que parecen aleatorias. El movimiento browniano geométrico es uno de los modelos clásicos para describir esa evolución, porque permite representar precios siempre positivos y retornos logarítmicos normalmente distribuidos.

Sin embargo, los mercados reales no siempre se comportan como predice el modelo. En la práctica aparecen fenómenos como eventos extremos más frecuentes de lo esperado, volatilidad agrupada en periodos de estrés, asimetría entre subidas y caídas, y posibles patrones de memoria temporal.

El problema del proyecto es analizar esa diferencia entre el modelo ideal y los datos reales: no basta con simular trayectorias que “se parezcan” a precios financieros, sino que hay que comprobar estadísticamente qué propiedades captura el modelo y cuáles quedan fuera.

## Objetivo

El objetivo principal es construir una base teórica y una arquitectura computacional para comparar empíricamente precios reales con trayectorias simuladas mediante movimiento browniano geométrico.

El proyecto busca:

- explicar la teoría matemática que justifica el modelo;
- derivar la solución del GBM mediante el lema de Itō;
- cargar series históricas de precios;
- estimar los parámetros de drift y volatilidad;
- simular trayectorias mediante Monte Carlo;
- comparar retornos reales y simulados;
- aplicar tests estadísticos sobre normalidad, autocorrelación y volatilidad;
- proponer extensiones como GARCH, Heston o análisis del exponente de Hurst;
- visualizar de forma clara las diferencias entre modelo y mercado real.

La idea central es usar el GBM como punto de partida, no como verdad definitiva.

## Enfoque

El proyecto parte de una construcción progresiva: primero se introduce la teoría probabilística elemental y después se avanza hacia procesos estocásticos, movimiento browniano, cálculo de Itō y simulación de precios.

El primer bloque establece la base matemática: variables aleatorias, espacios de probabilidad y procesos estocásticos. A partir de ahí se presenta el movimiento browniano como proceso continuo de estado continuo, con incrementos independientes, incrementos gaussianos y varianza creciente linealmente con el tiempo.

Después se introduce una idea clave: la **variación cuadrática**. A diferencia de una función diferenciable clásica, el movimiento browniano no tiene derivada ordinaria, pero sí una variación cuadrática finita. Esta propiedad explica por qué en cálculo estocástico aparece la regla informal:

```text
(dW_t)^2 = dt
```

Esa diferencia lleva al **lema de Itō**, que permite calcular la diferencial de funciones aplicadas a procesos estocásticos. En el caso del movimiento browniano geométrico, el lema de Itō permite derivar la solución:

```text
S_t = S_0 · exp[(μ - 1/2 σ²)t + σ W_t]
```

La corrección `-1/2 σ²` es esencial: representa el efecto de la volatilidad sobre el crecimiento logarítmico del precio y evita sobreestimar la evolución esperada del activo.

## Arquitectura del sistema

La memoria propone una arquitectura software modular para convertir la teoría en un pipeline de análisis empírico.

El sistema se organiza en cinco módulos principales:

### 1. Carga y limpieza de datos

El módulo `data_loader` se encarga de obtener datos históricos de mercado, limpiar la serie temporal y calcular retornos logarítmicos. También estima parámetros básicos como el precio inicial, el drift anualizado y la volatilidad anualizada.

### 2. Simulación browniana

El módulo `gbm_engine` genera trayectorias Monte Carlo del movimiento browniano geométrico. La simulación se plantea usando la discretización exacta derivada del lema de Itō:

```text
S_{t+Δt} = S_t · exp[(μ - 1/2 σ²)Δt + σ√Δt Z]
```

Esto evita el error de discretización que aparecería con una aproximación de Euler simple.

### 3. Tests estadísticos

El módulo `statistical_tests` compara los retornos reales con los retornos simulados o teóricos. Incluye pruebas como Jarque-Bera, Kolmogorov-Smirnov, Anderson-Darling, Ljung-Box, ARCH-LM y ADF.

Estas pruebas permiten detectar desviaciones respecto al GBM: falta de normalidad, autocorrelación, heterocedasticidad, clustering de volatilidad o no estacionariedad.

### 4. Modelos avanzados

El módulo `advanced_models` se plantea como extensión para estudiar modelos que capturan fenómenos que el GBM clásico no reproduce bien. Entre ellos aparecen GARCH(1,1), el modelo de Heston y el análisis del exponente de Hurst.

### 5. Visualización

El módulo `visualization` genera figuras para interpretar los resultados: fan charts, histogramas de retornos, QQ-plots, autocorrelaciones, volatilidad condicional y análisis de Hurst.

La arquitectura completa está pensada como un pipeline unidireccional: datos reales → estimación de parámetros → simulación GBM → contraste estadístico → modelos avanzados → visualización.

## Datos y archivos revisados

La memoria revisada es un documento de teoría y arquitectura del proyecto. Define la base matemática y la estructura de software prevista, pero no presenta todavía una implementación completa ni resultados empíricos finales.

La estructura propuesta para el proyecto es:

- `src/data_loader.py`: carga de datos financieros y cálculo de retornos.
- `src/gbm_engine.py`: simulación Monte Carlo del movimiento browniano geométrico.
- `src/statistical_tests.py`: batería de tests estadísticos.
- `src/advanced_models.py`: modelos como GARCH, Heston y Hurst.
- `src/visualization.py`: generación de figuras y visualizaciones.
- `notebooks/`: exploración de datos, simulación, análisis estadístico y modelos avanzados.
- `dashboard/app.py`: posible dashboard en Streamlit.
- `validation/validate_R.R`: validación cruzada en R.
- `outputs/figures/`: figuras generadas.
- `outputs/results/`: resultados exportados.
- `config.yaml`: configuración del análisis.
- `requirements.txt`: dependencias del proyecto.

También se proponen activos de referencia como SPY, AAPL o BTC-USD para el análisis comparativo, aunque la memoria se centra principalmente en la teoría y en la arquitectura del sistema.

## Resultados principales

Este proyecto no presenta resultados empíricos cerrados, sino una base teórica y una arquitectura preparada para producirlos.

Los principales resultados de esta fase son:

- desarrollo de una explicación completa del movimiento browniano y su conexión con modelos financieros;
- derivación de la solución del movimiento browniano geométrico mediante el lema de Itō;
- justificación de la corrección `-1/2 σ²`, clave para no sobreestimar el crecimiento logarítmico;
- diseño de una arquitectura modular para comparar datos reales y simulaciones;
- definición de una batería de tests para evaluar normalidad, colas pesadas, autocorrelación y volatilidad;
- identificación de extensiones naturales cuando el GBM no capture correctamente el comportamiento real del mercado.

El valor principal del proyecto está en conectar matemáticas avanzadas con una aplicación computacional clara: usar el GBM como modelo base, contrastarlo contra datos reales y justificar cuándo hacen falta modelos más sofisticados.

## Tecnologías utilizadas

La arquitectura propuesta utiliza herramientas habituales en análisis cuantitativo y ciencia de datos:

- **Python** como lenguaje principal.
- **NumPy** para simulación numérica y vectorización.
- **pandas** para series temporales financieras.
- **SciPy** para tests estadísticos.
- **matplotlib** para visualización.
- **yfinance** para descarga de datos de mercado.
- **arch** para modelos GARCH.
- **statsmodels** para tests como ADF, Ljung-Box y ACF.
- **Streamlit** como posible dashboard interactivo.
- **R** para validación cruzada.
- **Hugo** para la publicación web del proyecto.

A nivel matemático, el proyecto se apoya en procesos estocásticos, movimiento browniano, lema de Itō, simulación Monte Carlo y modelos de volatilidad.

## Limitaciones

La limitación principal es que la memoria actual desarrolla sobre todo la teoría y la arquitectura, pero no incluye todavía una validación empírica completa con resultados finales sobre activos concretos.

Además, el movimiento browniano geométrico es un modelo simplificado. Supone retornos logarítmicos normales, volatilidad constante e independencia temporal, hipótesis que suelen fallar en mercados reales.

También hay que tener cuidado con la interpretación financiera: el proyecto no pretende predecir precios ni construir una estrategia de inversión. Su finalidad es analítica y educativa: entender qué captura el modelo, qué no captura y cómo se puede comprobar de forma estadística.

Por último, los modelos avanzados como GARCH, Heston o movimiento browniano fraccionario se plantean como extensiones naturales, pero requerirían implementación, calibración y validación adicional para formar parte de una comparación completa.

## Líneas futuras

Las siguientes fases del proyecto deberían centrarse en implementar y validar la arquitectura propuesta.

Una primera línea sería construir el pipeline completo en Python: descarga de datos, estimación de parámetros, simulación Monte Carlo y comparación estadística.

Después, se podrían analizar distintos activos con comportamientos diferentes, por ejemplo un ETF amplio como SPY, una acción individual como AAPL y un activo más volátil como BTC-USD. Esto permitiría estudiar cómo cambia la adecuación del GBM según el tipo de mercado.

También sería interesante generar visualizaciones comparativas: fan charts de trayectorias simuladas, histogramas de retornos, QQ-plots, autocorrelación de retornos al cuadrado y evolución de la volatilidad.

Otra línea futura sería implementar GARCH(1,1), Heston o análisis del exponente de Hurst para comparar el GBM con modelos que capturan clustering de volatilidad, volatilidad estocástica o memoria temporal.

Finalmente, el proyecto podría cerrarse con un dashboard en Streamlit que permita seleccionar activo, rango temporal, número de simulaciones y visualizar de forma interactiva las diferencias entre modelo y mercado real.

## Memoria completa

La memoria completa desarrolla el fundamento matemático del proyecto y la arquitectura software propuesta: variables aleatorias, procesos estocásticos, movimiento browniano, variación cuadrática, lema de Itō, solución del movimiento browniano geométrico y diseño modular del sistema de análisis.

<div class="project-cta">
  <a class="button primary" href="/documents/memoria-browniano-ito-arquitectura.pdf" target="_blank" rel="noopener">Descargar memoria completa (PDF)</a>
</div>
