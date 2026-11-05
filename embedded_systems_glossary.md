# Embedded Systems Glossary & Reference Manual

A specialized, evolving reference guide for embedded systems engineering, covering foundational electronics, digital logic, C memory layouts, and firmware control concepts.

### **Analog-to-Digital Converter (ADC)**

An electronic device or peripheral that transforms continuous analog signals (such as sound, temperature, light, or voltage) into discrete digital numbers (binary sequences of 0s and 1s).

### **Controller Area Network (CAN)**

A robust communication protocol designed to let multiple electronic control units (ECUs) communicate over a shared two-wire network without requiring a dedicated communication line for every pair of devices.

### **Cross-Compiler**

A compiler that runs on one computing platform (the host) but generates executable machine code intended to run on a different computing platform (the target). Cross-compilers are essential in embedded development because target microcontrollers often lack the memory or processing resources to compile their own software.

### **Digital-to-Analog Converter (DAC)**

An electronic device or integrated circuit that translates digital data (represented as binary sequences of 0s and 1s) into a continuous analog signal (such as a voltage, current, or audio waveform).

### **Duty Cycle**

The percentage of one complete signal period during which a digital signal remains in its active (typically HIGH) state. Duty cycle is commonly used in Pulse Width Modulation (PWM) to control the average power delivered to a device or component.

### **Floating Input**

A digital input pin whose voltage is not actively driven to a defined HIGH or LOW state. Floating inputs act like antennas, picking up electromagnetic noise that leads to unpredictable logic readings.

### **General Purpose Input/Output (GPIO)**

Configurable microcontroller pins that can be dynamically programmed as digital inputs or outputs to interface with switches, LEDs, sensors, relays, and external hardware.

### **Heap**

A region of memory used for dynamic memory allocation. Memory is requested at runtime (e.g., via `malloc`) and must be manually released when no longer needed to prevent memory leaks or fragmentation in resource-constrained systems.

### **`#ifndef`**

A C/C++ preprocessor directive meaning "if not defined." Commonly combined with `#define` and `#endif` to form **include guards**, which prevent header files from being included multiple times within a single compilation unit.

### **Input Flapping**

The rapid, unintended oscillation of a digital input between HIGH and LOW states caused by electrical noise, contact bouncing, or an unbuffered floating pin.

### **Interrupt**

A hardware signal that tells the CPU to temporarily halt its current execution thread, immediately handle a high-priority event via a designated routine, and then return seamlessly to where it left off. (e.g., on the Arduino Uno, there are three types: External, Pin Change, and Timer).

### **Interrupt Service Routine (ISR)**

A specialized callback function executed in response to an interrupt request. An ISR temporarily takes control of CPU execution to service the triggering event before returning control back to normal program execution.

### **Logic HIGH**

A voltage level interpreted by a digital system as binary 1.

### **Logic LOW**

A voltage level interpreted by a digital system as binary 0.

### **Pointer**

A variable that stores the memory address of another variable rather than the value itself, enabling direct memory manipulation and dynamic data structures.

### **Polling**

A firmware control technique where the CPU repeatedly checks whether an event or state change has occurred.

### **Pull-Up & Pull-Down Circuits**

Electrical configurations that use resistors to establish a default HIGH (pull-up) or LOW (pull-down) voltage level on a digital input when no other device is actively driving that input. They prevent inputs from floating between logic states.

### **Pulse Width Modulation (PWM)**

A technique used to simulate analog output using digital signals by rapidly switching between HIGH and LOW states.

### **Resource-Constrained Environment (RCE)**

A computing environment in which critical resources such as memory, processing power, storage, bandwidth, or electrical power are limited and must be carefully managed. Common in embedded systems, microcontrollers, IoT devices, and battery-powered electronics.

### **Real-Time Operating System (RTOS)**

A specialized operating system designed to process data and handle events with predictable, deterministic scheduling so tasks can meet defined timing constraints.

### **Stack**

A region of memory used to store local variables, function parameters, and function return information. The stack grows and shrinks automatically in a last-in, first-out (LIFO) manner as functions are called and return.

### **Voltage Divider**

A circuit composed of two or more resistors that produces an output voltage that is a fraction of the input voltage.