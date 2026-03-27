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
