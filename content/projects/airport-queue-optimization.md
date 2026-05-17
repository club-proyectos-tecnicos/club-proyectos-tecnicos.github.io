---
title: "Optimización inteligente de colas y accesos en aeropuertos"
description: "Prototipo de simulación y apoyo a la decisión para estimar saturación de pasajeros en aeropuertos y recomendar refuerzos operativos mediante teoría de colas."
summary: "Prototipo de simulación y apoyo a la decisión para estimar saturación de pasajeros en aeropuertos y recomendar refuerzos operativos mediante teoría de colas."
status: "Prototipo funcional"
tags:
  - "Python"
  - "pandas"
  - "Simulación"
  - "Teoría de colas"
  - "Streamlit"
  - "Dashboard"
  - "YOLO"
  - "Data Analysis"
  - "Operations Research"
repo: ""
memory: "/documents/memoria-optimizacion-colas-aeropuertos.pdf"
team: "Javier Gonzálvez, Luis González, María Macías y Matthew Puente-Villegas"
image: "/images/projects/airport-queue-optimization/dashboard-operativo.png"
---

<div class="project-cta">
  <a class="button primary" href="/documents/memoria-optimizacion-colas-aeropuertos.pdf" target="_blank" rel="noopener">Descargar memoria completa (PDF)</a>
</div>

## Resumen

**Optimización inteligente de colas y accesos en aeropuertos** es un prototipo funcional para analizar el flujo de pasajeros en una terminal aeroportuaria y generar recomendaciones operativas a partir de datos simulados.

El sistema representa varias zonas del aeropuerto —check-in, bag drop, seguridad, pasaportes y embarque— y transforma lecturas de ocupación en métricas como saturación, tiempos de espera estimados y posibles cuellos de botella.

La validación principal se realiza mediante simulación, comparando un escenario base sin recomendaciones frente a otro en el que el sistema propone acciones como reforzar recursos o abrir nuevas líneas. El objetivo no es presentar un producto industrial terminado, sino demostrar cómo la combinación de simulación, visión artificial y teoría de colas puede servir como herramienta de apoyo a la toma de decisiones.

<div class="project-kpis">
  <div>
    <span>19,09 min → 5,32 min</span>
    <p>espera acumulada en la comparación de la memoria</p>
  </div>
  <div>
    <span>72,1%</span>
    <p>mejora relativa reportada en esa simulación</p>
  </div>
  <div>
    <span>5 zonas</span>
    <p>check-in, bag drop, seguridad, pasaportes y embarque</p>
  </div>
</div>

<figure>
  <img src="/images/projects/airport-queue-optimization/esquema-conceptual-sistema.png" alt="Esquema conceptual del sistema desde vídeos y simulación hasta dashboard">
  <figcaption>Flujo documentado en la memoria: datos sintéticos o conteos visuales, CSV de lecturas, motor de colas y dashboard de recomendaciones.</figcaption>
</figure>

## Problema

En un aeropuerto, la congestión rara vez aparece de forma aislada. Una cola excesiva en check-in puede trasladarse después a seguridad; una acumulación en pasaportes puede afectar al embarque; y una mala distribución de recursos puede convertir una incidencia puntual en un cuello de botella operativo.

El problema no consiste únicamente en **contar cuántas personas hay en una zona**, sino en convertir esos conteos en información útil: estimar si la capacidad disponible es suficiente, detectar qué zonas se están acercando a la saturación y decidir dónde tendría más impacto abrir una línea adicional o reforzar el personal.

Este proyecto parte de esa idea: pasar de una gestión reactiva, donde se actúa cuando la cola ya existe, a un modelo más anticipativo basado en datos, simulación y métricas operativas.

## Objetivo

El objetivo del proyecto es desarrollar un prototipo capaz de:

* representar distintas zonas de un aeropuerto como sistemas de espera;
* generar lecturas sintéticas de ocupación por zona;
* procesar esas lecturas en archivos CSV;
* estimar niveles de saturación y tiempos de espera;
* identificar posibles cuellos de botella;
* comparar escenarios sin recomendaciones y con recomendaciones;
* visualizar el estado del sistema en un dashboard;
* demostrar cómo YOLO podría utilizarse para obtener conteos de personas desde vídeo sintético.

El resultado es una primera iteración de un sistema de apoyo a la decisión para entornos aeroportuarios, centrado en la mejora del flujo de pasajeros mediante recomendaciones operativas simples y explicables.

## Enfoque

El proyecto se desarrolló combinando simulación, análisis de datos y teoría de colas.

Primero se definieron las zonas principales del aeropuerto: check-in, bag drop, seguridad, pasaportes y embarque. Después se generaron lecturas sintéticas de ocupación para simular cómo evoluciona el número de pasajeros en cada zona a lo largo del tiempo.

A partir de esas lecturas, el motor de colas estima la carga de cada zona, su capacidad disponible y el tiempo de espera asociado. Cuando una zona se aproxima a la saturación, el sistema puede generar una recomendación operativa, como abrir servidores adicionales o reforzar un punto concreto.

También se incorporó YOLO como prueba de concepto para el conteo de personas en vídeo sintético. Esta parte permite mostrar cómo, en un entorno más avanzado, los datos podrían provenir de cámaras o fuentes visuales. En este prototipo, sin embargo, la validación principal se realiza con datos sintéticos y simulados.

El flujo seguido fue:

1. Definición de zonas y estructura del aeropuerto.
2. Generación de lecturas sintéticas de pasajeros.
3. Procesamiento de datos en CSV.
4. Conteo experimental con YOLO sobre vídeo sintético.
5. Modelado simplificado mediante teoría de colas.
6. Estimación de saturación y espera por zona.
7. Generación de recomendaciones operativas.
8. Comparación entre escenario base y escenario con recomendaciones.
9. Visualización de resultados en Streamlit.

## Arquitectura del sistema

El sistema se organiza en cuatro capas principales: entrada de datos, motor de análisis, sistema de recomendación y visualización.

La **entrada de datos** se basa en lecturas de ocupación por zona. Estas lecturas pueden generarse mediante simulación o, de forma experimental, a partir de vídeos sintéticos procesados con YOLO. Cada fila del CSV representa un instante temporal y cada columna recoge el estado de una zona del aeropuerto.

El **motor de análisis** transforma esas lecturas en indicadores operativos. Para cada zona, calcula la demanda estimada, la capacidad disponible, el nivel de saturación y el tiempo de espera aproximado. La lógica se inspira en modelos de teoría de colas, donde la saturación depende de la relación entre la llegada de pasajeros, la tasa de servicio y el número de servidores activos.

El **sistema de recomendación** compara el estado de las distintas zonas y propone acciones cuando detecta riesgo de congestión. La idea es priorizar las zonas donde reforzar recursos tendría mayor impacto, evitando tratar cada cola como un problema aislado.

Por último, el **dashboard en Streamlit** permite visualizar el estado del sistema de forma clara: métricas por zona, niveles de saturación, alertas y recomendaciones principales.

## Datos y archivos revisados

La demo trabaja principalmente con datos sintéticos generados por simulación. Estos datos permiten probar el comportamiento del sistema sin depender de imágenes reales de aeropuertos, que presentan restricciones importantes de privacidad y seguridad.

Los principales archivos técnicos del proyecto son:

* `colas/simulador_lecturas_aeropuerto.py`: genera lecturas sintéticas de ocupación por zona.
* `colas/queue_engine.py`: implementa el motor de análisis basado en teoría de colas.
* `colas/comparador_escenarios.py`: compara el escenario base frente al escenario con recomendaciones.
* `outputs/lecturas_aeropuerto.csv`: contiene las lecturas generadas para las zonas del aeropuerto.
* `outputs/informe_colas.csv`: recoge métricas calculadas por el motor de colas.
* `outputs/comparacion_escenarios.csv`: almacena la comparación entre escenarios.
* `outputs/resumen_comparacion_escenarios.csv`: resume las métricas principales de la comparación.
* `aeropuerto_yolo/detectar_personas.py`: prueba de detección de personas con YOLO.
* `aeropuerto_yolo/escaneo_aeropuerto.py`: flujo experimental para escanear zonas mediante visión artificial.

Estos archivos conectan la parte de simulación, el análisis de colas, la comparación de escenarios y la demostración visual con YOLO.

## Resultados principales

La comparación más relevante del proyecto enfrenta dos escenarios sobre las mismas condiciones simuladas: uno sin recomendaciones y otro en el que el sistema aplica acciones operativas.

En esa simulación, la espera total acumulada baja de **19,09 minutos** a **5,32 minutos**, lo que supone una mejora relativa del **72,1%**. También se reduce el pico de espera agregado, que pasa de **1,70 minutos** a **0,75 minutos**.

<figure>
  <img src="/images/projects/airport-queue-optimization/comparacion-espera-acumulada.png" alt="Comparación de espera acumulada sin sistema y con recomendaciones">
  <figcaption>Comparación recogida en la memoria: escenario base frente a escenario con recomendaciones.</figcaption>
</figure>

Además, los eventos de cuello de botella se reducen de **56 a 52**. Esta mejora es más moderada que la reducción de espera total, pero muestra que el sistema no solo baja el tiempo acumulado, sino que también puede suavizar algunos episodios críticos.

El resultado principal del proyecto no es afirmar que el sistema esté listo para operar en un aeropuerto real, sino demostrar que una lógica sencilla de apoyo a la decisión puede mejorar el comportamiento de una simulación de flujo aeroportuario.

En conjunto, el prototipo consigue:

* generar lecturas estructuradas por zona;
* estimar saturación y espera mediante un motor de colas;
* comparar escenarios con y sin recomendaciones;
* visualizar el estado del sistema en un dashboard;
* validar de forma preliminar el valor de aplicar recomendaciones operativas sobre el flujo de pasajeros.

## Tecnologías utilizadas

El proyecto utiliza un stack sencillo y orientado a prototipado rápido:

* **Python** como lenguaje principal.
* **pandas** para lectura, transformación y análisis de datos.
* **NumPy** para cálculos numéricos.
* **CSV** como formato de intercambio entre simulador, motor y comparador.
* **Teoría de colas** para modelar saturación, capacidad y espera.
* **Streamlit** para construir el dashboard demostrativo.
* **Ultralytics YOLO / YOLOv8** como prueba de concepto para detección de personas.
* **OpenCV** para procesamiento de vídeo.
* **Hugo** para publicar la ficha del proyecto en la web del club.

La elección de estas herramientas permite construir un prototipo comprensible, fácil de ejecutar y suficientemente flexible para experimentar con distintos escenarios.

## Limitaciones

El sistema tiene varias limitaciones importantes.

La primera es que trabaja principalmente con **datos sintéticos y simulados**. Esto permite desarrollar y probar la arquitectura sin comprometer privacidad, pero impide afirmar que los resultados se mantendrían igual en un aeropuerto real.

La segunda es que YOLO se utiliza como **prueba de concepto**. Sirve para demostrar que sería posible obtener conteos desde vídeo, pero no se ha validado como sistema robusto de visión artificial en condiciones reales de iluminación, oclusiones, cámaras múltiples o alta densidad de personas.

También existen simplificaciones en el modelo de colas. Las tasas de llegada y servicio dependen de supuestos, y el comportamiento real de los pasajeros puede ser mucho más complejo que el representado en la simulación. En un entorno real habría que considerar horarios de vuelos, retrasos, disponibilidad de personal, distribución espacial, incidencias y restricciones operativas.

Por tanto, los resultados deben interpretarse como una **validación preliminar por simulación**, no como una garantía de rendimiento en producción.

## Líneas futuras

Las principales mejoras futuras estarían orientadas a acercar el prototipo a un entorno más realista.

Una primera línea sería conectar el sistema con datos reales o semirreales, ya sea mediante cámaras, sensores o registros históricos anonimizados. Esto permitiría calibrar mejor las tasas de llegada y servicio de cada zona.

También sería útil integrar información externa, como horarios de vuelos, retrasos, meteorología o disponibilidad de personal. Estos factores podrían modificar la demanda esperada y mejorar la calidad de las recomendaciones.

Otra línea de trabajo sería sustituir la lógica actual por un modelo de predicción y optimización más robusto, capaz de anticipar saturaciones con mayor margen y evaluar varias acciones posibles antes de recomendar una intervención.

Finalmente, el dashboard podría evolucionar hacia una interfaz más operativa, con filtros por zona, simulación de escenarios, historial de recomendaciones y explicación visual del impacto esperado de cada decisión.

## Memoria completa

La memoria completa recoge el desarrollo del proyecto con más detalle: contexto, fundamento teórico, metodología, arquitectura, implementación, resultados, limitaciones y líneas futuras.

Equipo del proyecto: **Javier Gonzálvez, Luis González, María Macías y Matthew Puente-Villegas**.

<div class="project-cta">
  <a class="button primary" href="/documents/memoria-optimizacion-colas-aeropuertos.pdf" target="_blank" rel="noopener">Descargar memoria completa (PDF)</a>
</div>
