---
author: Vu Nam
marp: true
slide: true
theme: uncover
paginate: true
---

<div style="text-align: left; width: 100%">

### SonicBoom: 第三次アウトオブオーダプロセッサ

#### **Jerry Zhao, Ben Korpan, Abraham Gonzalez, Krste Asanovic**

##### 英語論文購読第２回　ヴハイナム

---

#### **Table of Content**  

1. Introduction
2. BOOM history
3. Instruction Fetch
4. Execute
5. Load-Store Unit and Data Cache
6. System support
7. Evaluation
8. What's next
9. Conclusion

---

# Introduction

* Deployment of high-performance superscalar, out-of-order (OOO) cores expanding into mobile and edge devices
* Security, power, performance, area need to be considered when evaluating new design
* An open-source hardware implementation of a superscalar, OOO core is invaluable

---

* Open source hardware implementation have numerous advantages over software models of high-performance cores
  * Demonstrate precise microarchitectural behaviors
  * Execute real applications for trillions of cycles
  * _Empirically_ provide power and area measurements
  * Point of comparison for new microarchitectural platform

---

* Most of the current open-source hardware development framework only support simple in-order cores
  * Rocket
  * Ariane
  * Black Parrot
  * PicoRV32  
* Modern mobile / server-class SOC is impossible without a full-featured, high performance implementation of a superscalar OOO core. 

---

**_Fastest_ open-source** core
![bg fit right:55% 85%](./P2_SonicBoom_Comp.png)

---

# BOOM history

---

* BOOM Version 1
  * Education tool for University
  * Based on microprocessor MIPS R10K 
  (A RISC implementation of MIPS IV ISA)
  * Not enough pipeline stages, thus  
  **not physically realisable**

---

![bg fit center:100% 100%](./P4_Boom1.png)

---

* BOOM Version 2
  * Add more pipeline to Front-end and Execution paths
  * Split floating-point register file and execution units to independent pipeline
  * Split issue queues to separate queues: 
  Int, Memory, Float operations

---

![bg fit center:100% 100%](./P4_Boom2.png)

---

* Sonic BOOM
  * Support more software stacks
  * Fix performance bottlenecks, keep physical realizability
    * IF
    * EX backend
    * Load / Store
  * Improved critical path delay

---

![bg fit center:100% 100%](./P4_SonicBoom.png)

---

* In short
  * If BOOMv1 was created for educational purpose 
  BOOMv3 (SonicBOOM) was created for research in hi-performance core design

---

# Instruction Fetch

* Support for 2-byte RVC instructions
* Implementation of TAGE branch predictor
* Multiple branch-resolution units

---

Support for 2-byte forms of common 4-byte instructions  

* Default RV-ISA subset for packaged Linux distributions (Fedora, Debian)
* New fetch-unit which decodes possible 2 / 4 bytes instruction for every 2 bytes

---


![bg fit right:45% 85%](./P1_SonicBoom.png)
