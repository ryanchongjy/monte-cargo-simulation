# GBM Monte Carlo Stock Price Simulator

An interactive tool for simulating stock price paths under geometric Brownian motion (GBM), built with `ipywidgets`. Lets a user adjust initial price, drift, volatility, simulation horizon, time-step frequency, and number of simulated paths, and immediately see the resulting price paths and terminal price distribution.

## Overview

The simulator implements the discretised GBM update equation directly:

```
S(t) = S(t-1) * exp((r - 0.5 * sigma^2) * dt + sigma * sqrt(dt) * Z)
```

where `Z` is a freshly drawn standard normal shock per simulated path at each time step, and `dt` is the time delta (in years) between steps.

## Features

- Interactive widget interface (text inputs, date pickers, frequency dropdown, action buttons)
- Live chart updates without re-running code
- Input validation (flags invalid volatility ranges, or an end date before the start date)
- Adjustable number of simulated paths and time-step frequency (weekly, monthly, yearly)

## Files

- `gbm_simulator.ipynb` — full notebook with the GBM simulation function and interactive widget interface

## Example Output

A run with S0=$100, drift=3%, volatility=25%, weekly steps over 2 years, 200 simulated paths produces a right-skewed terminal price distribution, as expected under GBM (log-normal terminal distribution), with simulated mean terminal price close to the theoretical expectation of `S0 * e^(r*T)`.

## Setup

```bash
pip install -r requirements.txt
jupyter notebook gbm_simulator.ipynb
```

