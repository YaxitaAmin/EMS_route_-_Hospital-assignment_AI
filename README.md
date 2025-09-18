# Emergency Response Routing Optimization Model

A data-driven optimization system for routing emergency incidents to hospital facilities, designed to minimize response times while balancing hospital capacity loads across NYC.
## Overview

This project develops an intelligent routing system for emergency medical services that optimally assigns emergency incidents to hospital emergency rooms. The system uses statistical modeling and mathematical optimization to ensure efficient resource utilization while minimizing patient travel times.

## Motivation

- **Uncertainty-Aware Planning**: Handle unpredictable emergency patterns
- **Save Lives**: Minimize critical response times
- **Balance Load**: Prevent hospital overcrowding
- **Crisis Resilience**: Maintain system performance during high-demand periods
- **Intelligent Systems**: Data-driven decision making
- **Policy Impact**: Support emergency services planning

## Problem Statement

Emergency incidents occur unpredictably across urban regions, each characterized by:
- **Type of emergency** (e.g., cardiac arrest, general illness)
- **Geographic location** (ZIP code level)
- **Random demand patterns** (modeled using Poisson distributions)

**Objective**: Route emergency demands to hospital ERs such that:
- Total load does not exceed ER capacity constraints
- Travel time is minimized across all incidents
- All demand is served with high probability

## Dataset

- **EMS Data**: 100,000 emergency incidents across New York City
- **Hospital Data**: 83 NYC-area hospitals with capacity information
- **Geographic Coverage**: ZIP code level spatial resolution

## Methodology

### Data Pipeline
1. **Data Cleaning & Standardization**
   - Preprocessing of EMS incident records
   - Hospital capacity data validation
   
2. **Feature Engineering**
   - Location-emergency-time combinations
   - Incident rate calculations

3. **Spatial Integration**
   - Travel time matrix computation
   - Geographic distance calculations

### Statistical Modeling
- **Poisson Distribution Parameters**: Generated lambda (λ) values for incident rates by location and emergency type
- **Demand Forecasting**: Probabilistic modeling of emergency patterns

## Mathematical Formulation

### Decision Variables
- **x_{ijk}**: Fraction of emergencies of type j at location k routed to ER i

### Parameters
- **I**: Set of emergency rooms (ERs), indexed by i
- **J**: Set of emergency types, indexed by j  
- **K**: Set of incident locations (ZIP codes), indexed by k
- **C_i**: Capacity of ER i
- **λ_{jk}**: Incident rate (Poisson) for type j at location k
- **t_{ik}**: Travel time from ER i to location k
- **a_{ij}**: Binary indicator if ER i can handle emergency type j

### Objective Function
Minimize total weighted travel time across all emergency routing decisions.

### Constraints
- **Capacity Constraints**: Ensure hospital ER capacities are not exceeded
- **Demand Satisfaction**: All emergency demand must be routed
- **Compatibility**: Emergencies only routed to capable facilities
- **Non-negativity**: All routing fractions must be non-negative

## Key Results

### Routing Optimization
The model provides specific routing percentages for each emergency type by location:
- **Example**: Route 36% of GENERAL ILLNESS_2 incidents in ZIP 10005 to hospital 20211206 (Travel time: 8.93 minutes)

### Hospital Utilization
Tracks capacity utilization across all facilities:
- **Example**: Hospital 118910021 operates at 18.4% capacity (20.4/111 utilization ratio)

## Features

- **Real-time Routing**: Optimal assignment of incidents to ERs
- **Capacity Management**: Prevents hospital overcrowding
- **Multi-objective Optimization**: Balances time and load constraints
- **Scalable Architecture**: Handles large-scale urban emergency systems
- **Probabilistic Modeling**: Accounts for demand uncertainty

## Applications

- **Emergency Medical Services**: Optimize ambulance routing decisions
- **Hospital Administration**: Capacity planning and resource allocation
- **Public Health Policy**: Evidence-based emergency response planning
- **Urban Planning**: Emergency services infrastructure development

## Project Structure

```
emergency-routing-optimization/
├── data/
│   ├── ems_incidents.csv
│   ├── hospitals.csv

## Dependencies

- Python 3.8+
- NumPy
- Pandas
- SciPy (optimization)
- Matplotlib/Seaborn (visualization)
- Geopandas (spatial analysis)
- PuLP/Gurobi (mathematical optimization)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- NYC Emergency Medical Services for providing incident data
- Hospital systems for capacity and capability information
- Urban planning research community for methodological insights

---

**Note**: This system is designed for research and planning purposes. Implementation in actual emergency response systems requires additional validation and regulatory compliance.
