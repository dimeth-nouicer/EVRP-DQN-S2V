
# PowerTrip: AI-Powered Smart Transportation Solutions

PowerTrip is a startup that specializes in providing intelligent transportation solutions, focusing on optimizing routes and managing electric vehicle (EV) charging. By leveraging artificial intelligence (AI), PowerTrip ensures seamless journeys, helps drivers and fleets save time, reduces costs, and minimizes environmental impact.

## Project Overview

This repository contains the core code for PowerTrip's AI-powered platform, which is divided into two key components:
1. **Electric Vehicle Routing**: AI-based algorithms to optimize routing, ensuring the most efficient paths for electric vehicles, accounting for charging needs and minimizing overall journey time and energy consumption.
2. **Smart Charging**: Intelligent management of EV charging to maximize efficiency and minimize energy consumption.

### Features

- **AI-Powered Route Optimization**: Dynamically adjusts routes based on real-time data to ensure efficient and eco-friendly travel.
- **Smart EV Charging Management**: Predicts optimal charging times and locations, balancing cost savings and travel time.
- **Energy Efficiency**: Focuses on reducing the overall environmental impact by optimizing routes and energy use.
- **Driver & Fleet Benefits**: Designed to help both individual drivers and fleet operators.

## Repository Structure

```
PowerTrip/
│
├── Routing_module/             # Core modules for solving EV Routing 
│   ├── dataset/                # Dataset used in test
│   ├── nets/                   # Model for route optimization
│   ├── pretrained/             # Pretrained models for routing algorithms
│   ├── utils/                  # Utility functions and helper scripts
│   └── evrp.ipynb              # Main Jupyter Notebook for EVRP implementation
│   └── ReadMe.md               # Additional documentation to run the routing module
│
├── Smart_Charging/             # Code for intelligent EV charging management
│   ├── 1_Grid_Model/           # Model to simulate a full power distribution system
│   ├── 2_Charging_Control/     # Control and optimization algorithms for smart charging
│   └── ReadMe.md               # Additional documentation to run the smart charging module
│
└── README.md                 # This README file
```

## Module Independence

The **Smart Charging** and **Routing** modules are designed to work independently. It is preferable that each module is tested separately, as they do not rely on one another for their core functionality.

For best results:
- Test the **Smart Charging** module for intelligent charging management.
- Test the **Routing** module directly through the Jupyter notebook (`evrp.ipynb`), which provides an interactive environment to run simulations and evaluate results.

### Installation

To get started with the PowerTrip project, follow these steps:

1. Clone this repository:

   ```bash
   git clone https://github.com/imenhbibi/Power_Trip.git
   cd Power_Trip
   ```

2. Each module has its own specific installation and setup instructions detailed in the respective `ReadMe.md` file located in:
   - **Smart Charging**: `Smart_Charging/ReadMe.md`
   - **EVRP**: `Routing module/ReadMe.md`

## Usage

- **Smart Charging**: Navigate to the `smart_charging/` folder for modules related to charging management.
- **Routing Solver**: Navigate to the `Routing_module/` folder to explore routing for electric vehicles.
