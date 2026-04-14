# QUANTUM-ENHANCED-BATTERY-MANAGEMENT-SYSTEM
Classical Battery Management Systems (BMS) rely on heuristic State-of-Charge (SOC) estimation and greedy cell-balancing strategies. This project replaces both with quantum-inspired algorithms running on classical hardware, delivering more optimal cell equalization and higher-accuracy SOC tracking for a 4-cell LiNMC 18650 battery pack.
Battery Cell Model (BatteryCell class)
Realistic LiNMC electrochemistry: piecewise OCV-SOC curve, RC equivalent circuit, Joule heating, SOH degradation.
Coulomb counting + terminal voltage calculation.
Quantum Optimization Phase (run at the end of simulation)
VQE: Builds a problem Hamiltonian from cell voltage deviations, uses hardware-efficient Ry + CNOT ansatz + COBYLA optimizer.
QAOA: Formulates balancing as a cost Hamiltonian (pairwise voltage imbalance), uses X-mixer, p=2 layers, and samples the best bitstring to generate a concrete balancing plan (cell ID, ΔV, recommended bleed current).
Real-Time Quantum Kalman Filter
Every 5 simulation steps: predict via Coulomb counting, then quantum-encoded update using qubit rotation encoding + expectation value ⟨Z⟩.
Full Pack Simulation
80-second discharge (5 A) with live logging of voltages, SOC, ΔV, temperatures.
Automatic quantum optimization at the end with printed balancing recommendations.
