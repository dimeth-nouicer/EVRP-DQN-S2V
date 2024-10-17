# PowerTrip - Smart EV Fleet Management

**This code is dedicated to the smart control of Charging Points (CPs) in a given electric grid. It is the second module of our proposed smart EV fleet management software called "PowerTrip".**

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Output](#output)

## Overview

PowerTrip aims to optimize the charging of electric vehicles (EVs) and the control of photovoltaic (PV) systems in order to minimize the grid impacts, such as phase unbalance and voltage drops, while maximizing the usage of PV power. This module focuses on simulating the electric grid and applying a smart control strategy to Charging Points (CPs) and PV systems, helping prevent issues like power outages in extreme cases.

## Features

The main features of this implementation are:

- Simulate a full power distribution system (electric grid) using the open-source simulator "OpenDSS" based on real-world data provided by [ENWL](https://www.enwl.co.uk/future-energy/innovation/smaller-projects/low-carbon-networks-fund/low-voltage-network-solutions/).
- Optimize the charging power of Charging Points (CPs) and the Photovoltaic (PV) systems to:
  - Reduce grid impacts, such as phase unbalance and voltage drops.
  - Maximize the usage of PV power produced by the PV systems.
- Employ a multi-objective optimization framework using the Pymoo package in Python to find the trade-off between minimizing grid impacts and maximizing PV power usage.

## Installation

### Prerequisites

1. Install OpenDSS software from [here](https://sourceforge.net/projects/electricdss/).
2. We recommend creating a virtual environment before installing the required packages from the `requirements.txt` file. Run the following commands in your command prompt:

```bash
# Create a virtual environment
python -m venv myenv

# Activate the virtual environment
myenv\Scripts\activate

# Install the required dependencies
pip install -r requirements.txt
```

## Usage

### 1. Simulation without Control
Run the notebook named `1_simulation_without_control.ipynb` located in the `2_Charging_Control` folder to simulate the behavior of the grid without any smart control of the CPs and PV systems. This simulation assumes that:
- EVs receive their power requirements without any limitations.
- PV power is injected into the grid without restrictions, which may lead to grid problems (e.g., power outages in extreme cases).

### 2. Smart Control Simulation
Run the notebook named `2_smart_control.ipynb` in the `2_Charging_Control` folder to apply smart control and optimize two objectives:
- **Objective 1 (Grid Impact Minimization)**: Minimize the Phasing Unbalance Index (PUI) at the buses where CPs are installed:
    $$
    \underset{\underset{1 \leq i \leq 3,\ 1 \leq p \leq 12}{P_{\mathrm{CP}_i}(t),\ P_{\mathrm{PV}_{p}}(t)}}{min} \sum_{i=1}^{3} \mathrm{PUI}_{\mathrm{bus\_CP}_i}^2(t)
    $$
- **Objective 2 (PV Power Maximization)**: Minimize the curtailment of available PV power:
    $$
    \underset{\underset{1 \leq p \leq 12}{\ P_{\mathrm{PV}_{p}}(t)}}{min} \sum_{p=1}^{12} \left[P_{\mathrm{PV}_{\mathrm{actual}}}(t) - P_{\mathrm{PV}_p}(t)\right]^2
    $$

These objectives are conflicting, producing a set of Pareto-optimal solutions. We select a solution that balances minimizing the grid impact of EV charging and maximizing PV power usage.

## Output

Both notebooks provide comparison graphs that visualize the results with and without smart control. These include:
- Power Unbalance Index (PUI)
- Voltage drop across the grid
- PV power usage efficiency
