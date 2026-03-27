# Quantum Hackathon 🚀

This repository contains projects developed during the **Q-Hack Quantum Computing Hackathon**, which was structured as a **multi-level challenge**. Each level focused on progressively deeper concepts in quantum computing and circuit design.

---

## 📌 Level 1: Design of a 4-bit Ripple Carry Adder using Quantum Circuits

### 🧠 Objective

The goal of Level 1 was to **translate a classical digital circuit (4-bit ripple carry adder)** into a **reversible quantum circuit** using quantum gates.

Unlike classical circuits, quantum circuits must:

* Preserve information (reversibility)
* Avoid overwriting inputs
* Use additional qubits (ancilla) for intermediate computations

---

## ⚙️ What We Built

We implemented a **4-bit Ripple Carry Adder** using:

* **CNOT (CX) gates** → for XOR operations
* **Toffoli (CCX) gates** → for AND (carry generation)

Each bit addition is handled using a **quantum full adder block**, and carry propagates from one stage to the next — forming a ripple carry structure.

---

## 🔢 Qubit Mapping

| Register | Qubits  | Description                         |
| -------- | ------- | ----------------------------------- |
| A        | q0–q3   | First 4-bit input                   |
| B        | q4–q7   | Second 4-bit input                  |
| Sum      | q8–q11  | Output sum                          |
| Carry    | q12–q16 | Carry propagation                   |
| Temp     | q17–q20 | Ancilla qubits for intermediate XOR |

---

## 🔁 Working Principle

Each full adder computes:

* **Sum**:
  S = A ⊕ B ⊕ Cin

* **Carry**:
  Cout = (A · B) ⊕ (Cin · (A ⊕ B))

### Steps:

1. Compute intermediate XOR (A ⊕ B) using CNOT gates
2. Compute sum using XOR with carry-in
3. Generate carry using Toffoli gates
4. Propagate carry to the next stage
5. Uncompute temporary qubits to maintain reversibility

---

## 🧪 Example

### Input:

```
A = 1011 (11)
B = 0110 (6)
```

### Expected Output:

```
Sum = 10001 (17)
```

---

## 🛠️ Tools & Technologies

* **Qiskit** – Quantum circuit design and simulation
* **Qiskit Aer Simulator** – Local simulation of quantum circuits
* **Google Colab** – Development environment

---

## 📊 Results

* Successfully designed a reversible quantum ripple carry adder
* Verified circuit behavior using simulation
* Demonstrated carry propagation across multiple qubits

---

## 💡 Key Learnings

* Difference between classical and quantum circuit design
* Importance of **reversibility** in quantum computing
* Use of **ancilla qubits** for intermediate computations
* Implementation of arithmetic logic using quantum gates

---


## 👨‍💻 Author

* Developed as part of Q-Hack Hackathon Level 1

---

## ⭐ Note

This project focuses on **conceptual understanding and implementation of reversible arithmetic circuits**, which form the foundation for more advanced quantum algorithms and hardware design.

---

## 📌 Level 2: Smart City Emergency Priority System using Multiplexer (MUX)

---

### 🧠 Problem Statement

In a smart city environment, multiple sensors continuously monitor critical emergency conditions such as:

*  Fire Detection
*  Gas Leakage
*  Intrusion Detection
*  Medical Emergency

Due to **limited communication bandwidth**, only **one signal can be transmitted at a time** to the central control unit.

The objective was to design a system that:

* Selects **only one signal**
* Prioritizes **more critical emergencies over others**

---

## ⚙️ Approach

We implemented the solution in two ways:

### 1️⃣ Classical Priority MUX

A priority-based combinational logic was implemented where:

| Priority | Signal         |
| -------- | -------------- |
| Highest  | Fire (s3)      |
| High     | Gas (s2)       |
| Medium   | Intrusion (s1) |
| Low      | Medical (s0)   |

### Logic:

```text
If Fire → select Fire  
Else if Gas → select Gas  
Else if Intrusion → select Intrusion  
Else if Medical → select Medical  
Else → No signal
```

This ensures that **only the highest priority active signal is transmitted**.

---

## ⚛️ Quantum Implementation

To extend the idea into quantum computing, we designed a **reversible priority MUX circuit** using quantum gates.

---

### 🔢 Qubit Mapping

| Qubit | Signal         |
| ----- | -------------- |
| q0    | Medical (s0)   |
| q1    | Intrusion (s1) |
| q2    | Gas (s2)       |
| q3    | Fire (s3)      |
| q4    | Output         |

---

### ⚙️ Circuit Design Logic

The circuit uses:

* **CNOT (CX)** → for conditional activation
* **Toffoli (CCX)** → for controlled AND operations
* **Multi-controlled gates (MCX)** → for enforcing priority conditions

---

### 🔁 Priority Implementation

The logic is encoded as follows:

1. **Fire (Highest Priority)**

   * Directly sets output if active
   * `CX(q3 → q4)`

2. **Gas (Second Priority)**

   * Activated only if Fire = 0
   * Uses inverted Fire + Toffoli gate

3. **Intrusion (Third Priority)**

   * Activated only if Fire = 0 AND Gas = 0
   * Uses multi-controlled gate

4. **Medical (Lowest Priority)**

   * Activated only if all higher signals are 0
   * Uses 4-controlled gate

---

## 🧪 Superposition Testing

To demonstrate quantum behavior:

```text
All inputs were placed in superposition using Hadamard gates
```

This allows:

* Simultaneous evaluation of **all 16 input combinations**
* Verification of correct priority selection probabilistically

---

## 📊 Results

* Histogram shows distribution of output states (0 or 1)
* Expected behavior:

  * Output = 1 for 15 cases (any emergency present)
  * Output = 0 only when all inputs are 0

### Observations:

* Output closely matches expected probability distribution
* Accuracy calculated based on deviation from ideal results

---

## 🔍 Verification

Two validation methods were used:

### ✔ Deterministic Testing

* All 16 input combinations tested individually
* Verified correct priority selection

### ✔ Probabilistic Testing

* Superposition-based simulation
* Compared expected vs observed output distribution

---

## 💡 Key Learnings

* Implementation of **priority logic using reversible quantum gates**
* Use of **multi-controlled gates (MCX)** for complex conditions
* Understanding of **quantum parallelism via superposition**
* Bridging classical digital logic with quantum circuit design

---

## 🚀 Future Improvements

* Optimize circuit depth and gate count
* Implement noise-aware execution on real quantum hardware
* Extend to multi-output emergency classification
* Integrate with real-time IoT sensor simulation

---

## 🎯 Conclusion

This project demonstrates how a **classical priority-based multiplexer** can be translated into a **quantum circuit**, preserving logical correctness while leveraging quantum principles like superposition and reversibility.

It highlights the potential of quantum computing in **intelligent decision-making systems for smart city infrastructure**.

---

