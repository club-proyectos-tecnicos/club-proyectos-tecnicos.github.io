---
title: "Intelligent airport queue and access optimization"
date: 2026-05-18
projectNumber: 2
slug: "airport-queue-optimization"
description: "A simulation and decision-support prototype that estimates passenger congestion in airports and recommends operational reinforcement using queueing theory."
summary: "A simulation and decision-support prototype that estimates passenger congestion in airports and recommends operational reinforcement using queueing theory."
status: "Functional prototype"
tags:
  - "Python"
  - "pandas"
  - "Simulation"
  - "Queueing theory"
  - "Streamlit"
  - "Dashboard"
  - "YOLO"
  - "Data Analysis"
  - "Operations Research"
repo: "https://github.com/javiergonzalvez07-star/Optimizacion-Inteligente-Colas-Aeropuertos"
memory: "/proyectos/airport-queue-optimization/memoria.pdf"
team: "Javier Gonzálvez, Luis Gonzalez, Matthew Puente-Villegas and María Macías"
image: "/proyectos/airport-queue-optimization/imagenes/dashboard-operativo.png"
---

## Summary

**Intelligent airport queue and access optimization** is a functional prototype for analyzing passenger flows in an airport terminal and generating operational recommendations from simulated data.

The system represents several airport areas—check-in, bag drop, security, passport control and boarding—and turns occupancy readings into metrics such as congestion, estimated waiting times and potential bottlenecks.

Its main validation uses simulation to compare a baseline scenario without recommendations against another in which the system proposes actions such as adding resources or opening new service lines. The goal is not to present a finished industrial product, but to demonstrate how simulation, computer vision and queueing theory can be combined into a decision-support tool.

<div class="project-kpis">
  <div>
    <span>19.09 min → 5.32 min</span>
    <p>cumulative waiting time in the report's comparison</p>
  </div>
  <div>
    <span>72.1%</span>
    <p>relative improvement reported in that simulation</p>
  </div>
  <div>
    <span>5 areas</span>
    <p>check-in, bag drop, security, passport control and boarding</p>
  </div>
</div>

<figure>
  <img src="/proyectos/airport-queue-optimization/imagenes/esquema-conceptual-sistema.png" width="1448" height="1086" loading="lazy" decoding="async" alt="Conceptual system diagram from videos and simulation to the dashboard">
  <figcaption>Flow documented in the report: synthetic data or visual counts, a CSV of readings, the queue engine and the recommendation dashboard.</figcaption>
</figure>

## Problem

Congestion in an airport rarely occurs in isolation. An excessive check-in queue may later move to security; a buildup at passport control may affect boarding; and poor resource allocation can turn a temporary incident into an operational bottleneck.

The challenge is not merely to **count how many people are in an area**, but to turn those counts into useful information: estimate whether the available capacity is sufficient, detect which areas are approaching saturation and decide where opening an additional line or assigning more staff would have the greatest impact.

This project starts from that idea: moving from reactive management, where action is taken only once a queue already exists, toward a more proactive model based on data, simulation and operational metrics.

## Goal

The project aims to develop a prototype capable of:

* representing different airport areas as queueing systems;
* generating synthetic occupancy readings for each area;
* processing those readings in CSV files;
* estimating congestion levels and waiting times;
* identifying potential bottlenecks;
* comparing scenarios with and without recommendations;
* displaying the system's status in a dashboard;
* demonstrating how YOLO could obtain person counts from synthetic video.

The result is a first iteration of a decision-support system for airport environments, focused on improving passenger flows through simple and explainable operational recommendations.

## Approach

The project was developed by combining simulation, data analysis and queueing theory.

First, the main airport areas were defined: check-in, bag drop, security, passport control and boarding. Synthetic occupancy readings were then generated to simulate how passenger numbers in each area change over time.

Using those readings, the queue engine estimates each area's load, available capacity and associated waiting time. When an area approaches saturation, the system can generate an operational recommendation, such as opening additional servers or reinforcing a specific service point.

YOLO was also incorporated as a proof of concept for counting people in synthetic video. This shows how data could be obtained from cameras or visual sources in a more advanced environment. In this prototype, however, the primary validation uses synthetic and simulated data.

The process was:

1. Define the airport areas and structure.
2. Generate synthetic passenger readings.
3. Process data in CSV files.
4. Conduct experimental counting with YOLO on synthetic video.
5. Build a simplified queueing-theory model.
6. Estimate congestion and waiting time for each area.
7. Generate operational recommendations.
8. Compare the baseline scenario with the scenario using recommendations.
9. Visualize the results in Streamlit.

## System architecture

The system is organized into four main layers: data input, analysis engine, recommendation system and visualization.

The **data input** consists of occupancy readings for each area. These readings can be generated by simulation or, experimentally, from synthetic videos processed with YOLO. Each CSV row represents a point in time, and each column records the status of an airport area.

The **analysis engine** transforms these readings into operational indicators. For each area, it calculates estimated demand, available capacity, congestion level and approximate waiting time. Its logic draws on queueing models, where congestion depends on the relationship between passenger arrivals, the service rate and the number of active servers.

The **recommendation system** compares the status of the different areas and proposes actions when it detects a risk of congestion. The idea is to prioritize the areas where assigning additional resources would have the greatest impact, instead of treating each queue as an isolated problem.

Finally, the **Streamlit dashboard** clearly displays the system's status, including metrics by area, congestion levels, alerts and the main recommendations.

## Data and files reviewed

The demo works primarily with synthetic data generated through simulation. This makes it possible to test the system without relying on real airport imagery, which presents significant privacy and security constraints.

The project's main technical files are:

* `colas/simulador_lecturas_aeropuerto.py`: generates synthetic occupancy readings for each area.
* `colas/queue_engine.py`: implements the queueing-theory analysis engine.
* `colas/comparador_escenarios.py`: compares the baseline scenario against the scenario with recommendations.
* `outputs/lecturas_aeropuerto.csv`: contains the readings generated for the airport areas.
* `outputs/informe_colas.csv`: contains the metrics calculated by the queue engine.
* `outputs/comparacion_escenarios.csv`: stores the comparison between scenarios.
* `outputs/resumen_comparacion_escenarios.csv`: summarizes the comparison's main metrics.
* `aeropuerto_yolo/detectar_personas.py`: tests person detection with YOLO.
* `aeropuerto_yolo/escaneo_aeropuerto.py`: experimental workflow for scanning areas with computer vision.

These files connect the simulation, queue analysis, scenario comparison and visual YOLO demonstration.

## Main results

The project's most relevant comparison places two scenarios under the same simulated conditions: one without recommendations and another in which the system applies operational actions.

In that simulation, total cumulative waiting time falls from **19.09 minutes** to **5.32 minutes**, a relative improvement of **72.1%**. The aggregate peak waiting time also decreases from **1.70 minutes** to **0.75 minutes**.

<figure>
  <img src="/proyectos/airport-queue-optimization/imagenes/comparacion-espera-acumulada.png" width="1233" height="577" loading="lazy" decoding="async" alt="Comparison of cumulative waiting time without the system and with recommendations">
  <figcaption>Comparison included in the report: the baseline scenario versus the scenario with recommendations.</figcaption>
</figure>

Bottleneck events also decrease from **56 to 52**. This improvement is more modest than the reduction in total waiting time, but it shows that the system can both lower cumulative waiting and mitigate some critical episodes.

The project's main result is not a claim that the system is ready to operate in a real airport, but a demonstration that straightforward decision-support logic can improve the behavior of an airport-flow simulation.

Overall, the prototype is able to:

* generate structured readings by area;
* estimate congestion and waiting time with a queue engine;
* compare scenarios with and without recommendations;
* display the system's status in a dashboard;
* provide preliminary validation of the value of applying operational recommendations to passenger flows.

## Technologies used

The project uses a straightforward stack designed for rapid prototyping:

* **Python** as the main language.
* **pandas** for reading, transforming and analyzing data.
* **NumPy** for numerical calculations.
* **CSV** as the exchange format between the simulator, engine and comparator.
* **Queueing theory** to model congestion, capacity and waiting time.
* **Streamlit** to build the demonstration dashboard.
* **Ultralytics YOLO / YOLOv8** as a proof of concept for person detection.
* **OpenCV** for video processing.
* **Hugo** to publish the project page on the club website.

These tools make it possible to build a prototype that is understandable, easy to run and flexible enough to test different scenarios.

## Limitations

The system has several significant limitations.

First, it works primarily with **synthetic and simulated data**. This enables development and testing without compromising privacy, but it does not prove that the same results would hold in a real airport.

Second, YOLO is used as a **proof of concept**. It demonstrates that counts could be obtained from video, but it has not been validated as a robust computer-vision system under real conditions involving lighting changes, occlusion, multiple cameras or high crowd density.

The queue model also contains simplifications. Arrival and service rates depend on assumptions, and real passenger behavior can be much more complex than the simulation represents. A real environment would need to account for flight schedules, delays, staff availability, spatial distribution, incidents and operational constraints.

The results must therefore be interpreted as **preliminary validation through simulation**, not as a guarantee of production performance.

## Future work

The main future improvements would bring the prototype closer to a realistic environment.

One step would be to connect the system to real or semi-real data through cameras, sensors or anonymized historical records. This would make it possible to calibrate each area's arrival and service rates more accurately.

It would also be useful to integrate external information such as flight schedules, delays, weather or staff availability. These factors could change expected demand and improve the quality of the recommendations.

Another direction would be to replace the current logic with a more robust prediction and optimization model, capable of anticipating congestion earlier and evaluating several possible actions before recommending an intervention.

Finally, the dashboard could evolve into a more operational interface, with filters by area, scenario simulation, a recommendation history and a visual explanation of each decision's expected impact.

## Full report

The full report covers the project in greater detail: context, theoretical foundation, methodology, architecture, implementation, results, limitations and future work.

Project team: **Javier Gonzálvez, Luis Gonzalez, Matthew Puente-Villegas and María Macías**.
