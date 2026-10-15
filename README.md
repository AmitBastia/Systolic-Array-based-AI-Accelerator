# Systolic-Array-based-AI-Accelerator

## Overview
This project implements a reconfigurable systolic array accelerator capable of performing both 2D convolution and matrix multiplication (3×3 and 9×9 configurations) for AI workloads.
It is targeted for deployment on the Xilinx Artix-7 FPGA, integrated with a MicroBlaze soft processor via the AXI4 interface.
The accelerator is optimized for low latency, high throughput, and efficient BRAM utilization, making it ideal for edge AI applications.

## Architecture
The system is based on:

* Systolic Array Core: 9×9 grid of Processing Elements (PEs), each capable of multiply-accumulate (MAC) operations.
* MicroBlaze Control Unit: Configures the accelerator, triggers operations, and handles interrupts.
* AXI4-Lite (Control): For register-based communication between CPU and accelerator.
* AXI4-Stream (Data): For high-speed data transfers.
* On-chip BRAM: Stores input matrices, filter weights, and output results.<br>

Data Flow:

* Input data & weights loaded into BRAM via AXI4.
* MicroBlaze triggers accelerator start signal.
* Systolic array performs computation in a pipelined fashion.
* Results stored back to BRAM and read by CPU.

## Features
* Dual Mode Operation: Supports both convolution and matrix multiplication.
* FSM-Based Control Logic: Efficient operation sequencing and synchronization.
* Interrupt Handling: MicroBlaze receives interrupts upon computation completion.
* High Throughput: Achieves up to 3.6 Gbps for matrix multiplication.
* Optimized Memory Usage: Balanced BRAM partitioning for parallel read/write.

## Tools & Technologies
* HDL: Verilog
* FPGA Toolchain: Xilinx Vivado 2023.1
* Embedded Processor: Xilinx MicroBlaze
* Communication Protocol: AXI4 (AXI4-Lite for control, AXI4-Stream for data)
* Hardware Platform: Xilinx Artix-7 (xc7a100t)
* Software Development: Xilinx SDK (for MicroBlaze programming)
* Simulation: Vivado Simulator

## Results & Performance
* Throughput: Achieved 3.6 Gbps in 9×9 matrix multiplication mode.
* Latency: Reduced compared to traditional sequential computation by ~70%.

## Simulation & Testing
* Verified functional correctness with testbenches in Vivado Simulator.
* Tested on FPGA board with pre-defined and random input matrices.
* Validated results against software-based matrix multiplication in C for accuracy.
## Applications
* Convolutional Neural Network (CNN) acceleration
* Real-time image processing
* Edge AI inference systems
* High-speed DSP computations

  
