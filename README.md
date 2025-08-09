# Low Power ALU Design with Clock Gating

**Project Domain:** Low Power VLSI / Digital Design / Verilog HDL

---

## 1. Project Overview  
This project implements a **4-bit Arithmetic Logic Unit (ALU)** in Verilog, focusing on **low power consumption** through the use of **clock gating**.  

Two designs are presented:  
- **Unoptimized ALU** – Standard design without power-saving techniques.  
- **Optimized ALU** – Incorporates clock gating to reduce unnecessary switching and dynamic power consumption.  

The ALU performs eight core operations and is verified using **Cadence Genus** (synthesis), **Cadence SimVision** (simulation), and open-source tools like **Icarus Verilog** and **GTKWave** for additional analysis.  

---

## 2. Motivation  
In embedded systems, IoT devices, and battery-powered applications, **power efficiency** is a critical design factor.  
Conventional ALUs consume power continuously because their clock runs even when idle.  
By integrating **clock gating**, we can disable clock propagation to inactive blocks, reducing switching activity and conserving energy.  

---

## 3. ALU Features and Operations  

| **Feature** | **Details** |
|-------------|-------------|
| **Bit-width** | 4-bit ALU |
| **Number of Operations** | 8 |
| **Enable Signal** | Controls execution — when low, no operation is performed |
| **Clock Gating** | Implemented in optimized version to reduce power consumption |
| **Implementation Language** | Verilog HDL |
| **Simulation Tools** | Cadence SimVision, Icarus Verilog, GTKWave |
| **Synthesis Tool** | Cadence Genus |

**Supported Operations:**  

| **Opcode** | **Operation** | **Description** |
|------------|--------------|-----------------|
| `000` | ADD | Adds A and B |
| `001` | SUB | Subtracts B from A |
| `010` | AND | Bitwise AND |
| `011` | OR  | Bitwise OR |
| `100` | XOR | Bitwise XOR |
| `101` | SHL | Shift A left by 1 |
| `110` | SHR | Shift A right by 1 |
| `111` | NOT | Bitwise NOT of A |

---

## 4. Difference Between Unoptimized and Optimized Designs  

| Feature | Unoptimized ALU | Optimized ALU with Clock Gating |
|---------|----------------|--------------------------------|
| Clock Propagation | Always active | Controlled by enable signal |
| Power Consumption | Higher due to continuous switching | Reduced by avoiding unnecessary toggles |
| Input Register Clocking | On every clock edge | Only when enable is high |
| Area Overhead | Low | Slightly higher (gating logic added) |
| Complexity | Simple | Moderate |
| Suitability for Low Power | Poor | Excellent |

---

## 5. You can find the synthesis and simulation commands in the low_power_alu_gating folder under the same repository.

---

## 6. Expected Behavior
- Enable = 1: ALU processes inputs based on the opcode and updates outputs.
- Enable = 0:
  - Unoptimized ALU → Continues internal switching, wasting power.
  - Optimized ALU → Internal switching stops, conserving power.

---

## 7. Results and Observations
- Optimized ALU shows reduced switching activity during idle cycles.
- Both designs are functionally correct across all operations.
- Minimal area overhead for clock gating compared to substantial power savings.

---

## 8. Possible Improvements
- Replace manual gated clock logic with standard cell library clock gating cells during synthesis.
- Extend ALU to a parameterized N-bit version for scalability.
- Add more operations (e.g., multiplication, division).
- Integrate into a processor datapath for complete low-power CPU demonstration.

---

