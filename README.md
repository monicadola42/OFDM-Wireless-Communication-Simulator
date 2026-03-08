# OFDM Wireless Communication System Simulator

## Overview

This project implements a **simulation of an Orthogonal Frequency Division Multiplexing (OFDM) wireless communication system** using Python. The system models how digital data is transmitted over a wireless channel and analyzes the performance using **Bit Error Rate (BER) vs Signal-to-Noise Ratio (SNR)**.

OFDM is widely used in modern wireless communication technologies such as **WiFi, LTE, 4G, and 5G** because it efficiently handles multipath fading and improves spectral efficiency.

The simulator includes key communication system components such as **QPSK modulation, Rayleigh fading channel modeling, pilot-based channel estimation, and BER performance analysis**.

---

# Objectives

The main objectives of this project are:

* To simulate an **OFDM-based wireless communication system**
* To implement **QPSK modulation and demodulation**
* To model a **Rayleigh fading wireless channel**
* To implement **pilot-based channel estimation**
* To analyze system performance using **BER vs SNR curves**
* To visualize received signals using **constellation diagrams**

---

# Technologies Used

* **Python**
* **NumPy** – numerical computations
* **Matplotlib** – plotting graphs and visualizations

---

# System Architecture

The complete communication system follows the pipeline below:

```
Random Bits
     ↓
QPSK Modulation
     ↓
OFDM Modulation (IFFT)
     ↓
Cyclic Prefix Addition
     ↓
Wireless Channel (Rayleigh Fading + AWGN Noise)
     ↓
Cyclic Prefix Removal
     ↓
OFDM Demodulation (FFT)
     ↓
Pilot-Based Channel Estimation
     ↓
Channel Equalization
     ↓
QPSK Demodulation
     ↓
Bit Error Rate (BER) Calculation
```

---

# Key Concepts Implemented

## 1. Random Bit Generation

The system first generates a sequence of random binary bits representing digital data to be transmitted.

```
Example:
0 1 1 0 0 1 1 1 ...
```

---

## 2. QPSK Modulation

Quadrature Phase Shift Keying (QPSK) maps **2 bits into one complex symbol**.

| Bits | Symbol  |
| ---- | ------- |
| 00   | 1 + 1j  |
| 01   | -1 + 1j |
| 10   | 1 - 1j  |
| 11   | -1 - 1j |

This converts binary data into complex symbols suitable for transmission.

---

## 3. OFDM Modulation

OFDM divides the data into multiple **subcarriers**.

The symbols are converted from **frequency domain to time domain** using **Inverse Fast Fourier Transform (IFFT)**.

Advantages of OFDM:

* High spectral efficiency
* Robust against multipath fading
* Used in modern wireless systems

---

## 4. Cyclic Prefix

A **cyclic prefix (CP)** is added to each OFDM symbol.

Purpose:

* Reduces **Inter-Symbol Interference (ISI)**
* Maintains orthogonality between subcarriers

---

## 5. Rayleigh Fading Channel

Wireless signals experience multipath propagation due to reflections from buildings, objects, and terrain.

The **Rayleigh fading model** simulates this effect.

Channel model:

```
Received Signal = Transmitted Signal × Channel + Noise
```

---

## 6. AWGN Noise

Additive White Gaussian Noise (AWGN) represents random noise present in real communication systems.

Noise power is controlled using **Signal-to-Noise Ratio (SNR)**.

---

## 7. Pilot-Based Channel Estimation

Pilot symbols are inserted at known positions in the OFDM frame.

Since the receiver already knows the pilot values, it can estimate the channel response using:

```
Channel Estimate = Received Pilot / Transmitted Pilot
```

Interpolation is then used to estimate the channel for all subcarriers.

---

## 8. Channel Equalization

The estimated channel is used to remove channel distortion:

```
Equalized Symbol = Received Symbol / Estimated Channel
```

This helps recover the original transmitted symbols.

---

## 9. QPSK Demodulation

The equalized symbols are converted back into binary bits based on their position in the constellation diagram.

---

## 10. BER Calculation

The received bits are compared with the transmitted bits.

```
BER = Number of Error Bits / Total Bits
```

This measures system performance.

---

# Results

## BER vs SNR Plot

The system performance is evaluated by plotting **Bit Error Rate vs Signal-to-Noise Ratio**.

Expected behavior:

* As **SNR increases**, noise decreases
* **BER decreases**, meaning fewer transmission errors
  <img width="715" height="561" alt="image" src="https://github.com/user-attachments/assets/a02f77e1-baf5-42f3-a6fb-f6d190f96705" />


---

## Constellation Diagram

A constellation diagram visualizes received QPSK symbols.

Ideal QPSK constellation:

```
      ●       ●

      ●       ●

```
<img width="704" height="576" alt="image" src="https://github.com/user-attachments/assets/c337b9a4-005f-4be8-8da1-dc84ca4e8aff" />


Noise causes these points to spread around the ideal positions.

---

# Example Outputs

The simulator generates:

* **BER vs SNR performance graph**
* **Received QPSK constellation diagram**

These results help evaluate the reliability of the communication system.

---

# Project Structure

```
OFDM-Wireless-Communication-Simulator
│
├── ofdm_simulation.py
├── README.md
```

---

# Applications of OFDM

OFDM is used in many real-world technologies:

* WiFi (IEEE 802.11)
* 4G LTE
* 5G NR
* Digital TV broadcasting
* DSL broadband systems

---

# Conclusion

This project demonstrates how a complete **OFDM-based wireless communication system** can be simulated in Python. The system models real-world channel conditions and evaluates performance using BER analysis.

The implementation helps understand important communication concepts such as **modulation, multipath fading, channel estimation, and equalization**.

---
