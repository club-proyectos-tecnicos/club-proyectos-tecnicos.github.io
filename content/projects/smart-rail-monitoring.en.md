---
title: "Brownian Motion"
date: 2026-05-18
slug: "brownian-motion"
description: "An empirical comparison between real prices and simulations based on geometric Brownian motion."
summary: "A theoretical and computational project exploring Brownian motion, Itô's lemma, GBM simulation and comparisons with real assets."
status: "Theoretical and experimental analysis"
tags:
  - "Python"
  - "NumPy"
  - "pandas"
  - "Simulation"
  - "Stochastic processes"
  - "Quantitative finance"
  - "Monte Carlo"
team: "Giancarlo Vargas, Rafael Laria and Nikolai Ilin"
image: "/proyectos/movimiento-browniano/imagenes/results_SPY.png"
---

## Summary

**Brownian Motion** is a theoretical and computational project focused on comparing real financial price paths with simulations based on **geometric Brownian motion**.

Its purpose is to study how well a classic mathematical finance model can reproduce the behavior of real assets and, above all, to identify where it fails: heavy tails, volatility clustering, return asymmetry or temporal dependence.

The project develops the mathematical foundations of Brownian motion, quadratic variation and Itô's lemma, then connects them to simulations and statistical tests on assets such as SPY, BTC-USD and AAPL.

<div class="project-kpis">
  <div>
    <span>GBM</span>
    <p>geometric Brownian model as a mathematical benchmark</p>
  </div>
  <div>
    <span>Itô</span>
    <p>the theoretical basis for deriving the model's exact solution</p>
  </div>
  <div>
    <span>3 assets</span>
    <p>SPY, BTC-USD and AAPL as comparison cases</p>
  </div>
</div>

<figure>
  <img src="/proyectos/movimiento-browniano/imagenes/results_SPY.png" alt="GBM study for SPY with simulation, returns, a QQ plot and autocorrelation">
  <figcaption>SPY comparison: real price versus a band of GBM simulations, with return diagnostics.</figcaption>
</figure>

## Problem

Financial prices move irregularly, with fluctuations that appear random. Geometric Brownian motion is one of the classic models used to describe this behavior because it keeps prices positive and models logarithmic returns with a normal distribution.

Real markets exhibit phenomena that the ideal model does not fully capture: more frequent extreme events, volatility clustered in periods of stress, asymmetry between gains and losses, and possible patterns of temporal dependence.

The project's problem is to analyze the gap between the model and real data. Generating paths that look similar is not enough; it is necessary to determine which properties the model captures and which remain outside it.

## Goal

The project aims to build a theoretical and experimental foundation for:

- explaining Brownian motion and its role in finance;
- deriving the solution to geometric Brownian motion using Itô's lemma;
- simulating price paths with Monte Carlo methods;
- comparing simulated paths with real prices;
- analyzing returns, tails, normality and volatility;
- interpreting the limitations of GBM when compared with real markets.

## Approach

The work starts with elementary probability theory and progresses through stochastic processes, Brownian motion, quadratic variation and Itô calculus.

A key idea is that Brownian motion is continuous but not differentiable. Its quadratic variation does not disappear, which gives rise to the informal rule used in stochastic calculus:

```text
(dW_t)^2 = dt
```

This property leads to Itô's lemma. When applied to geometric Brownian motion, it gives the solution:

```text
S_t = S_0 * exp[(mu - 1/2 sigma^2)t + sigma W_t]
```

The correction `-1/2 sigma^2` is essential: it represents the effect of volatility on the logarithmic growth of the price.

## Visual results

The project's charts compare the real price with a band of GBM simulations and show return diagnostics: the distribution, QQ plot and autocorrelation of squared returns.

<figure>
  <img src="/proyectos/movimiento-browniano/imagenes/results_BTC_USD.png" alt="GBM study for BTC-USD with simulation, returns, a QQ plot and autocorrelation">
  <figcaption>BTC-USD displays more volatile behavior and visible departures from the model's ideal normal distribution.</figcaption>
</figure>

<figure>
  <img src="/proyectos/movimiento-browniano/imagenes/results_AAPL.png" alt="GBM study for AAPL with simulation, returns, a QQ plot and autocorrelation">
  <figcaption>AAPL helps illustrate differences between an individual stock and the aggregate behavior of an ETF such as SPY.</figcaption>
</figure>

## Technologies used

The project uses common quantitative analysis tools:

- **Python** as the main language;
- **NumPy** for numerical simulation;
- **pandas** for time series;
- **matplotlib** for visualization;
- **yfinance** to obtain market data;
- statistical tests to study normality, tails and volatility.

## Limitations

Geometric Brownian motion is a simplified model. It assumes normally distributed logarithmic returns, constant volatility and temporal independence, assumptions that often fail in real markets.

The project is therefore not presented as a financial forecasting tool or trading system. Its value lies in using the model as a mathematical benchmark, testing it against real data and explaining when more sophisticated models are required.

## Project files

The project's original images and charts are organized at:

- `/proyectos/movimiento-browniano/imagenes/results_SPY.png`;
- `/proyectos/movimiento-browniano/imagenes/results_BTC_USD.png`;
- `/proyectos/movimiento-browniano/imagenes/results_AAPL.png`.

This project does not currently have a published PDF report.
