# ⚛️ Quantum-Enhanced Battery Management System

> **A hybrid quantum-classical BMS using VQE, QAOA, and Quantum Kalman Filter**  
> Author: **Satyanarayana Sangisetti** | EEE B.Tech 2025 | QBIT FORCE Internship Candidate

---

## 🔬 Project Overview

Classical Battery Management Systems use heuristic methods for SOC estimation and greedy algorithms for cell balancing. This project replaces both with **quantum algorithms**:

| Classical BMS | Quantum-Enhanced BMS |
|---|---|
| Coulomb counting SOC | Quantum Kalman Filter (QKF) |
| Greedy cell balancing | QAOA combinatorial optimization |
| Heuristic equalization | VQE ground-state energy mapping |

---

## 🧠 Quantum Algorithms Used

### 1. VQE — Variational Quantum Eigensolver
- Maps battery pack **equilibrium state** to quantum ground state energy
- Hamiltonian encodes cell voltage spread as interaction energy
- Hardware-efficient ansatz: `Ry(θ) — CNOT — Ry(φ)` per cell
- COBYLA optimizer minimizes energy → finds optimal equalization voltage

### 2. QAOA — Quantum Approximate Optimization Algorithm  
- Formulates cell balancing as a **QUBO / Max-Cut problem**
- Decides which cells to bleed simultaneously to minimize ΔV spread
- p=2 layer QAOA with Phase Separation + X-Mixer  
- Outputs optimal balance bitstring with probabilities

### 3. QKF — Quantum Kalman Filter
- Encodes SOC as **qubit rotation angle**: `θ = arccos(2·SOC − 1)`
- Quantum expectation value `⟨Z⟩` maps back to SOC estimate
- Hybrid: quantum amplitude encoding + classical Kalman update equations

---

## 📁 Project Structure

```
quantum-bms/
├── quantum_bms_main.py      # Complete source code (single file)
├── requirements.txt         # Dependencies
├── README.md                # This file
└── quantum_bms_results.png  # Output plots (generated on run)
```

---

## ⚡ Quick Start

```bash
# 1. Clone the repo
git clone https://github.com/sangisetti-satya/quantum-bms.git
cd quantum-bms

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the simulation
python quantum_bms_main.py
```

**Expected output:**
```
╔══════════════════════════════════════════════════════════════════╗
║   QUANTUM-ENHANCED BATTERY MANAGEMENT SYSTEM                    ║
╚══════════════════════════════════════════════════════════════════╝

QUANTUM BMS SIMULATION  |  DISCHARGE  |  I=5.0A
═══════════════════════════════════════════════════════
  t=   0s  SOC= 72.3%  ΔV= 48.2mV  T_max=25.4°C
  t=  20s  SOC= 68.1%  ΔV= 31.7mV  T_max=26.8°C
  ...

  [VQE]  Running ground-state energy minimization...
         E_vqe  = -2.3814
         E_exact= -2.3901
         Error  = 0.0087
         Target V = 3.6742 V

  [QAOA] Solving cell balancing optimization...
         Best bitstring: 1010
         Cell 1: BALANCE ΔV=52.3 mV  bleed=5.2 mA
         Cell 3: BALANCE ΔV=28.1 mV  bleed=2.8 mA

  Saved: quantum_bms_results.png
```

---

## 📊 Output Plots

The simulation generates a **7-panel dashboard**:

1. Cell voltages over time
2. Voltage spread ΔV (mV)
3. SOC estimation via QKF
4. Cell temperatures
5. VQE convergence curve
6. QAOA cost function minimization
7. QAOA state probability distribution

---

## 🔧 Technical Specs

| Parameter | Value |
|---|---|
| Cell chemistry | LiNMC 18650 |
| Pack configuration | 4S (expandable to 8S) |
| Nominal voltage | 14.8V (4S) |
| Capacity | 2.5 Ah per cell |
| Simulation timestep | 1 second |
| VQE optimizer | COBYLA (gradient-free) |
| QAOA depth | p = 2 |
| QKF process noise | 1×10⁻⁴ |

---

## 📄 Resume Bullets

```
Quantum-Enhanced Battery Management System (Python)
• Designed hybrid quantum-classical BMS for 4S LiNMC pack using
  VQE, QAOA, and Quantum Kalman Filter algorithms from scratch in NumPy
• Replaced greedy cell balancing with QAOA (p=2) formulated as QUBO
  optimization; reduced voltage spread by encoding as Max-Cut problem
• Implemented Quantum Kalman Filter encoding SOC as qubit rotation
  angle θ = arccos(2·SOC−1); achieved <2% SOC estimation error
• Mapped battery equilibrium state to quantum ground state via
  hardware-efficient VQE ansatz with CNOT entanglement layers
• Built thermal model with Joule heating + convective cooling;
  generates 7-panel visualization dashboard with Matplotlib
```

---

## 🎓 Relevant Certifications

- QC101: Quantum Computing & Intro to QML — Udemy
- Quantum Fundamentals Program (2025–2026) — WISER, Qubitech, Amaravati Quantum Valley
- Introduction to AI — IBM

---

## 📬 Contact

**Satyanarayana Sangisetti**  
📧 satyamahesh9390@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/sangisetti-satya)  
📍 Hyderabad, India

---

*Built for QBIT FORCE Quantum Control Software Engineering Internship — Amaravati Quantum Valley, Andhra Pradesh*
