# Advanced Pacing Calculator for JMeter 🚀

![JMeter Version](https://img.shields.io/badge/JMeter-5.0+-orange.svg)
![Type](https://img.shields.io/badge/Plugin-Listener-green.svg)

**Advanced Pacing Calculator** is a custom JMeter Listener designed to simplify workload modeling. It dynamically calculates the required pacing to achieve a target **Transactions Per Hour (TPH)** based on real-time response times, user counts, and hardcoded think times.

---

## 📖 Table of Contents
* [Overview](#-overview)
* [Core Features](#-core-features)
* [Mathematical Logic](#-mathematical-logic)
* [User Interface Guide](#-user-interface-guide)
* [Installation](#-installation)
* [Usage](#-usage)

---

## 🧐 Overview
In performance testing, maintaining a consistent throughput is difficult when response times fluctuate. This plugin removes the guesswork by calculating the necessary delay at the end of each iteration to keep your test on track.

## ✨ Core Features
* **Dynamic Pacing Calculation:** Adjusts pacing in real-time based on the last sample's response time.
* **Total Think Time Visibility:** Calculates cumulative think time across a transaction flow.
* **GUI Integration:** Displays live metrics directly within the JMeter interface.
* **Automated Injection:** One-click button to inject a `Constant Timer` pre-configured with the `${calculatedPacing}` variable.
* **Detailed Logging:** Logs Load Time, Pacing, and Total Think Time to the JMeter Log Viewer.

---

## 🧮 Mathematical Logic
The tool uses the following formulas to ensure high-precision throughput:

$$Target\ Cycle\ Time = \frac{Users \times 3600}{Target\ TPH / Transactions\ per\ Flow}$$

$$Total\ Think\ Time = (Transactions\ per\ Flow - 1) \times Hardcoded\ Think\ Time$$

$$Required\ Pacing = Target\ Cycle\ Time - (Load\ Time + Total\ Think\ Time)$$

---

## 🖥️ User Interface Guide

| Field | Description |
| :--- | :--- |
| **Target TPH** | Total transactions per hour you want to achieve. |
| **Number of Users** | Concurrent thread count in your Thread Group. |
| **Transactions per Flow** | Number of samplers/requests in one iteration. |
| **Hardcoded Think Time** | Manual delay (seconds) placed between transactions. |
| **Required Pacing (ms)** | **(Output)** Delay needed at the end of the iteration. |
| **Total Think Time (ms)** | **(Output)** Total time spent in manual delays. |

---

## 🛠️ Installation
1.  Download the `PacingCalc.jar`.
2.  Place the file into the `YOUR_JMETER_HOME/lib/ext` directory.
3.  Restart JMeter.

---

## 🚀 Usage
1.  **Add the Component:** Right-click **Thread Group** > **Add** > **Listener** > **Advanced Pacing Calculator**.
2.  **Configure Parameters:** Enter your Target TPH, Users, and Flow details.
3.  **Inject Timer:** * Click the **"Inject Constant Timer Below"** button.
    * Move the generated timer to the **end** of your transaction sequence.
4.  **Run & Monitor:** * Run the test. 
    * Open the **Log Viewer** (Yellow triangle top-right) to see real-time calculations.

---

## 📸 Screenshots
<p align="center">
  <img src="https://github.com/user-attachments/assets/36f16d76-d0f1-42dd-8605-c3442ffaa4a5" width="800" alt="Main Interface" />
  <br>
  <em>Figure 1: Main Plugin Interface</em>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/b33bfbc5-ded3-482b-95d6-064b7c4069b8" width="800" alt="Timer Injection" />
  <br>
  <em>Figure 2: Automated Timer Injection</em>
</p>

---

## 📄 License
Sri Satya Satti
