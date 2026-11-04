---
title: "Predicción de trayectoria en deportes"
date: 2026-05-18
lastmod: 2026-11-04
projectNumber: 3
phase: first
slug: "deportes"
aliases:
  - "/projects/smart-plant-monitoring/"
description: "Aplicación de Streamlit para explorar probabilidades por zona de decisión en duelos deportivos, con datos sintéticos."
summary: "Aplicación de Streamlit para explorar probabilidades por zona de decisión en duelos deportivos, con datos sintéticos."
status: "Prototipo documentado"
tags:
  - "Deporte"
  - "Datos"
  - "Prediccion"
  - "Machine Learning"
  - "Python"
repo: "https://github.com/jairosdc/Prediccion-de-trayectoria-en-deportes"
memory: "/proyectos/deportes/memoria.pdf"
team: "Jairo Sanchez, Jose Ariza, Samuel Izquierdo, Marina Vicens y Manuel Fernandez"
image: ""
---

## Resumen

La aplicación muestra cómo cambian las probabilidades estimadas para cada zona de decisión al modificar un escenario deportivo de uno contra uno. Cubre seis disciplinas con datos sintéticos.

## Objetivo

¿Cómo cambia la elección que predice el modelo cuando varían la presión temporal, el marcador u otras condiciones? El proyecto muestra cómo convertir un escenario en variables del modelo y explorar las probabilidades resultantes. Los datos son sintéticos, así que la evaluación mide el comportamiento del modelo bajo los supuestos del generador de escenarios.

## Enfoque

Un generador crea escenarios con distribuciones de probabilidad controladas. Un índice ponderado describe la presión. Un modelo de regresión logística multinomial estima probabilidades por zona y la interfaz de Streamlit permite variar las entradas. La evaluación mide el rendimiento en escenarios sintéticos.

## Archivos del proyecto

El repositorio contiene el generador, el modelo y la aplicación. La memoria técnica documenta los supuestos, la evaluación y las instrucciones para ejecutar la aplicación en local.

## Memoria y repositorio

[Memoria técnica e instrucciones](/proyectos/deportes/memoria.pdf) · [Repositorio del proyecto](https://github.com/jairosdc/Prediccion-de-trayectoria-en-deportes).
