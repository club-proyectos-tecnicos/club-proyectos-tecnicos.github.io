---
title: "Sports trajectory prediction"
date: 2026-05-18
lastmod: 2026-11-04
projectNumber: 3
phase: first
slug: "sports-trajectory-prediction"
description: "A Streamlit app for exploring probabilities for different decision zones in one-on-one sports scenarios, using synthetic data."
summary: "A Streamlit app for exploring probabilities for different decision zones in one-on-one sports scenarios, using synthetic data."
portfolioQuestion: "How do time pressure and the score affect predicted choices in one-on-one sports scenarios?"
portfolioWork: "The team built a Streamlit app to explore modelled choices across six sports using synthetic scenarios."
status: "Documented prototype"
tags:
  - "Sports"
  - "Data"
  - "Prediction"
  - "Machine Learning"
  - "Python"
repo: "https://github.com/jairosdc/Prediccion-de-trayectoria-en-deportes"
memory: "/proyectos/deportes/memoria.pdf"
team: "Jairo Sanchez, Jose Ariza, Samuel Izquierdo, Marina Vicens and Manuel Fernandez"
image: ""
---

## Summary

The app shows how the predicted probabilities for different decision zones change as you adjust a one-on-one sports scenario. It covers six disciplines using synthetic data.

## Goal

How do time pressure, the score and other conditions change the zone a model predicts a player will choose? The project shows how to turn a scenario into model inputs and explore the resulting probabilities. The data are synthetic, so the evaluation measures how the model behaves under the assumptions of the scenario generator.

## Approach

A generator creates scenarios using controlled probability distributions. A weighted index describes pressure. A multinomial logistic regression model estimates probabilities by zone, and the Streamlit interface lets users vary the inputs. The evaluation measures performance on synthetic scenarios.

## Project files

The repository contains the generator, model and app. The technical report documents the assumptions, evaluation and instructions for running the app locally.

## Report and repository

[Technical report and reproducibility steps in Spanish](/proyectos/deportes/memoria.pdf) · [Project repository](https://github.com/jairosdc/Prediccion-de-trayectoria-en-deportes).
