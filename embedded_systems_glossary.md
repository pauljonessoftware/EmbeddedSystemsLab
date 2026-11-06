# The Embedded Systems Engineering Glossary

**Active-high** - A signal that is considered "true" or "asserted" when it is at Logic HIGH.

**Active-low** - A signal that is considered "true" when it is at Logic LOW (very common with pull-up + button-to-ground arrangements).

**Analog to Digital Converter (ADC)** - An electronic device that transforms continuous analog signals (such as sound, temperature, light, or voltage) into discrete digital numbers (binary code of 1s and 0s).

**Contact Group** - A set of switch terminals that are electrically connected together.

**Contact Resistance** - The small resistance of a closed contact.

**Controller Area Network (CAN)** - A communication protocol designed to let multiple electronic control units (ECUs) communicate over a shared network, without requiring a separate communication wire for every pair of devices.

**Continuity** - The presence of an electrically conductive path between two points.

**Continuity Test** - A low-resistance check, where the meter beeps below a threshold that varies by meter.

**Cross Compiler** - A compiler that runs on one computing platform (the host) but generates executable machine code intended to run on a different computing platform (the target). Cross-compilers are commonly used in embedded development because the target microcontroller often lacks the resources to compile its own software.

**Current Limiting Resistor** - A resistor used to control the amount of current flowing through a component such as an LED.

**Digital to Analog Converter (DAC)** - An electronic device or integrated circuit that translates digital data (represented as binary sequences of 0s and 1s) into a continuous analog signal (such as a voltage, current, or sound wave).

**Digital Multimeter (DMM)** - An instrument used to measure electrical quantities such as voltage, current, and resistance, and to test continuity.

**Duty Cycle** - The percentage of one complete signal period during which a digital signal remains in its active (typically HIGH) state. Duty cycle is commonly used in Pulse Width Modulation (PWM) to control the average power delivered to a device.

**Floating Input** - A digital input whose voltage is not driven to a defined HIGH or LOW state. Floating inputs may produce unpredictable behavior.

**General Purpose Input Output (GPIO)** - Configurable microcontroller pins that can be programmed to function as digital inputs or outputs. GPIO pins are commonly used to interface with switches, LEDs, sensors, and other external hardware.

**Heap** - A region of memory used for dynamic memory allocation. Memory is requested at runtime and released when no longer needed.

**High-Impedance (Hi-Z)** - An electrical state where a pin presents extremely high resistance, effectively floating unless anchored by a pull-up or pull-down resistor.

**ifndef** - Preprocessor directive meaning "if not defined." Commonly used with #define and #endif to create include guards that prevent a header file from being included multiple times within a compilation unit.

**Input Flapping** - The rapid, unintended oscillation of a digital input between HIGH and LOW states due to noise, bouncing, or a floating pin.

**Interrupt** - A hardware signal that tells the CPU to stop what it's currently doing, immediately handle a specific event, and then go back to exactly where it left off. On the Arduino Uno, there are three types: External, Pin change and Timer.

**Interrupt Service Routine (ISR)** - A function executed in response to an interrupt request. An ISR temporarily takes control of CPU execution to service the event that triggered the interrupt, after which normal program execution resumes.

**Junction** - A point at which conductors or circuit elements are electrically connected.

**Logic HIGH** - A voltage interpreted by a digital system as binary 1.

**Logic LOW** - A voltage interpreted by a digital system as binary 0.

**Memory Fragmentation** - A condition where free heap memory becomes divided into many small blocks that cannot easily be reused.

**Momentary Switch** - A switch that changes state only while being actuated and returns to its normal state when released.

**Normally Open (NO)** - A switch configuration in which the contacts are electrically disconnected in the default state and become connected when actuated.

**Normally Closed (NC)** - A switch configuration in which the contacts are electrically connected in the default state and become disconnected when actuated.

**Pointer** - A variable that stores the memory address of another variable rather than the value itself.

**Poles and Throws (SPST, SPDT)** - The formal way to describe switch configurations.
*   **SPST (Single Pole, Single Throw):** A simple on/off switch.
*   **SPDT (Single Pole, Double Throw):** A switch that routes one input to one of two outputs.

**Polling** - Repeatedly checking whether something has happened.

**Pull-Up & Pull-Down Circuits** - Electrical configurations that use resistors to establish a default HIGH (pull-up) or LOW (pull-down) voltage level on a digital input when no other device is actively driving that input. They prevent inputs from floating between logic states.

**Pulse Width Modulation (PWM)** - A technique used to simulate analog output using digital signals.

**Real-Time Operating System (RTOS)** - A specialized operating system designed to process data and handle events with predictable, deterministic scheduling so tasks can meet defined timing constraints.

**Resource-Constrained Environment** - A computing environment in which critical resources such as memory, processing power, storage, bandwidth, or electrical power are limited and must be carefully managed. Resource-constrained environments are common in embedded systems, microcontrollers, IoT devices, and battery-powered electronics.

**Short circuit** - An unintended low-resistance path, as in a switch wired straight across a battery.

**Stack** - A region of memory used to store local variables, function parameters, and function return information. The stack grows and shrinks automatically as functions are called and return.

**Stack Overflow** - A condition that occurs when a program consumes more stack memory than is available.

**Switch** - An electromechanical device used to open or close an electrical circuit.

**Tactile Switch** - A momentary push-button switch designed to provide physical feedback when pressed.

**Voltage Divider** - A circuit composed of two or more resistors that produces an output voltage that is a fraction of the input voltage.