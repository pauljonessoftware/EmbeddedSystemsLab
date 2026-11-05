# Embedded Systems Glossary & Reference Manual

A specialized, evolving reference guide for embedded systems engineering, covering foundational electronics, digital logic, and firmware control concepts.

---

### **Analog-to-Digital Converter (ADC)**
An electronic device or peripheral that transforms continuous analog signals (such as sound, temperature, light, or voltage) into discrete digital numbers (binary sequences of 0s and 1s).

### **Controller Area Network (CAN)**
A robust communication protocol designed to let multiple electronic control units (ECUs) communicate over a shared two-wire network without requiring a dedicated communication line for every pair of devices.

### **Cross-Compiler**
A compiler that runs on one computing platform (the host) but generates executable machine code intended to run on a different computing platform (the target). Cross-compilers are essential in embedded development because target microcontrollers often lack the memory or processing resources to compile their own software.

### **Digital-to-Analog Converter (DAC)**
An electronic device or integrated circuit that translates digital data (represented as binary sequences) into a continuous analog signal (such as a voltage, current, or audio waveform).

### **Duty Cycle**
The percentage of one complete signal period during which a digital signal remains in its active (typically HIGH) state. Duty cycle is commonly used in Pulse Width Modulation (PWM) to control the average power delivered to a load or component.

### **Floating Input**
A digital input pin whose voltage is not actively driven to a defined HIGH or LOW state. Floating inputs act like antennas, picking up electromagnetic noise that leads to unpredictable logic readings.

### **General Purpose Input/Output (GPIO)**
Configurable microcontroller pins that can be dynamically programmed as digital inputs or outputs to interface with switches, LEDs, sensors, relays, and external hardware.

### **`#ifndef`**
A C/C++ preprocessor directive meaning "if not defined." Commonly combined with `#define` and `#endif` to form **include guards**, which prevent header files from being included multiple times within a single compilation unit.

### **Input Flapping**
The rapid, unintended oscillation of a digital input between HIGH and LOW states caused by electrical noise, contact bouncing, or an unbuffered floating pin.

### **Interrupt**
A hardware signal that tells the CPU to temporarily halt its current execution thread, immediately handle a high-priority event via a designated routine, and then return seamlessly to where it left off. (e.g., ATmega328P supports External, Pin Change, and Timer interrupts).

### **Interrupt Service Routine (ISR)**
A specialized callback function executed in response to an interrupt request. An ISR temporarily takes control of CPU execution to service the triggering event before returning control back to the main loop.

### **Logic HIGH**
A voltage level interpreted by a digital system or microcontroller as a binary `1` (typically near $V_{CC}$).

### **Logic LOW**
A voltage level interpreted by a digital system or microcontroller as a binary `0` (typically near $0\text{V}$ Ground).

### **Polling**
A firmware control technique where the CPU continuously loops and repeatedly queries the status of a peripheral or input pin to detect a state change.

### **Pull-Up & Pull-Down Circuits**
Electrical configurations using resistors to establish a deterministic default HIGH (pull-up) or LOW (pull-down) voltage level on a digital input when no active driver is connected. They prevent high-impedance inputs from floating.

### **Pulse Width Modulation (PWM)**
A technique used to simulate an analog output signal using high-speed digital switching by varying the ratio of ON time (duty cycle) to OFF time.

### **Resource-Constrained Environment (RCE)**
A computing domain in which critical operational parameters—such as RAM, Flash memory, CPU clock speed, bandwidth, or power budget—are strictly limited and must be carefully managed.

### **Real-Time Operating System (RTOS)**
A specialized operating system designed to process data and schedule tasks with strict, deterministic timing constraints, ensuring critical operations complete within predefined deadlines.

### **Voltage Divider**
A fundamental linear circuit composed of two or more resistors in series that produces an output voltage ($V_{OUT}$) that is a precise fraction of its input voltage ($V_{IN}$).