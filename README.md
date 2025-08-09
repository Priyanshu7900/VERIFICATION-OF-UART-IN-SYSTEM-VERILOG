# Project Title

# Verification of the UART Protocol in SystemVerilog

## Project Overview

This project implements and verifies the Universal Asynchronous Receiver/Transmitter (UART) protocol using SystemVerilog. The design includes separate transmitter (`uart_tx`) and receiver (`uart_rx`) modules, integrated into a top-level system (`top.sv`), with a testbench (`top_tb.sv`) verifying end-to-end communication and functionality.

## Features

- Fully synthesizable UART transmitter and receiver modules  
- Top-level integration connecting `uart_tx` and `uart_rx`  
- Testbench that verifies functionality, logs results, and captures pass/fail status  
- `verification_results` providing simulation outputs and evidence of correct behavior

## Architecture
The project comprises modules including:
- **uart_tx.sv** – UART Transmitter module that serializes parallel input data and outputs it according to UART protocol timing.  
- **uart_rx.sv** – UART Receiver module that samples the serial input, deserializes it, and reconstructs the original parallel data.  
- **top.sv** – Top-level module instantiating both transmitter and receiver, wiring them together for end-to-end data flow.  
- **top_tb.sv** – Testbench that applies reset and clock, drives input data to the transmitter, and monitors receiver output to verify full communication path.  
- **verification_results/** – Contains logs, waveforms, or textual outputs confirming the transmitted data matches the received data, along with pass/fail indicators.

---

## Run Locally

Clone the project

```bash
git clone https://github.com/Priyanshu7900/VERIFICATION-OF-UART-IN-SYSTEM-VERILOG.git
```

Go to the project directory

```bash
cd VERIFICATION-OF-UART-IN-SYSTEM-VERILOG
```

Install a Verilog Simulator

```bash
Download (Free with Intel FPGA tools): https://www.intel.com/content/www/us/en/software-kit/705184/modelsim-intel-fpgas.html
```

How to check the results on ModelSim

```bash
. Open ModelSim and Create a Project
. vlib work
. vmap work work 
. vlog *.sv 
. vlog top_tb.sv
. vsim top_tb 
. run -all
```

---

## Run on EDA Playground

1. **Open** [EDA Playground](https://www.edaplayground.com/) .  
2. **Set language** to **SystemVerilog / Verilog** in the left sidebar.  
3. In the **Design pane** (right), click the **+** and add these files from your GitHub repo:  
   - `uart_tx.sv`  
   - `uart_rx.sv`  
   - `top.sv`  
4. In the **Testbench pane** (left), either:  
   - Paste your `top_tb.sv` code into the default testbench tab, **or**  
   - Create a new file `top_tb.sv` and paste it there.  
5. At the **very top** of your testbench file, add:

```verilog
`include "uart_tx.sv"
`include "uart_rx.sv"
`include "top.sv"
```
*(This ensures files are compiled in the correct order.)*

6. In the **Tools & Simulators** section:  
   - For full SystemVerilog features → select **Siemens Questa** or **Aldec Riviera**.  
   - For a lighter option → select **Icarus Verilog** (limited SV support).  
7. *(Optional)* Check **Open EPWave after run** to automatically open the waveform viewer.  
8. Click **Run** (or press `Ctrl+Enter`). 
