# Rift Valley Fever Clinical Trial Scheduling — MiniZinc

## Problem
Schedule treatment allocations across patient groups for a simulated Rift Valley Fever
clinical trial, balancing total treatment cost against scheduling feasibility.

## Objective
Multi-objective optimisation — minimise total treatment cost while satisfying all
scheduling and treatment constraints across patient groups.

## Constraints
- A1: Each vaccine must be delivered exactly twice
- A2: Each patient group must receive a unique vaccine set
- A3/A4: Treatment type and frequency limits per week
- A5: Minimum and maximum treatment frequency across weeks
- A6/A7/A8: Resource limits and patient grouping requirements
- C1: Cost diversity constraints across treatment options
- C2: Cost ratio between most and least expensive treatments must stay within 2:1

## Sensitivity Analysis
Tested across 9 datasets (rift0.dzn to rift8.dzn) by systematically removing each
of 10 constraint groups to measure impact on:
- Total treatment cost
- Solver runtime

### Key Findings
- **A1** was the single biggest cost driver across all datasets
- **C2** caused solver timeouts in high-complexity scenarios
- **A5** was the second most impactful constraint on solution cost

## Tools
- Language: MiniZinc
- Solver: HiGHS 1.9.0
- Time limit: 60 seconds per run

## How to Run
1. Install MiniZinc IDE from https://www.minizinc.org/
2. Open `rift.mzn`
3. Select a `.dzn` data file (rift0.dzn to rift8.dzn)
4. Click Run
