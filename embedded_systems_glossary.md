# Embedded Systems Glossary

**EmbeddedSystemsLab**\
*Measure it. Build it. Test it. Document it.*

A working reference of electronics, microcontrollers, embedded systems,
programming, and communication terminology.

------------------------------------------------------------------------

### A

**ACK (Acknowledgment)** -- A response indicating that data or a message
has been received successfully at a protocol-defined level. In I²C, for
example, an ACK is communicated by the receiver pulling the SDA line LOW
during the acknowledgment clock pulse.

**Active-High** -- A signal that is considered asserted or logically
true when its voltage is at Logic HIGH.

**Active-Low** -- A signal that is considered asserted or logically true
when its voltage is at Logic LOW. Often indicated by a bar over a signal
name, a leading `n`, or a trailing `_N`. Common in pull-up and
button-to-ground arrangements.

**Actuator** -- A device that converts an electrical control signal into
a physical action, such as movement, rotation, switching, or the
production of sound or light. Examples include motors, relays,
solenoids, and servos.

**Analog Sensor** -- A sensor that produces a continuously varying
electrical output, typically a voltage or current, corresponding to a
measured physical quantity such as temperature, light intensity, or
pressure.

**Analog-to-Digital Converter (ADC)** -- An electronic circuit that
converts a continuous analog signal into a discrete digital
representation. An ADC samples an analog voltage and represents its
measured level as a digital number.

**Arbitration** -- A process used to determine which device may transmit
when multiple devices attempt to communicate over a shared bus. CAN uses
message identifiers to determine transmission priority.

**Arduino** -- An open-source electronics platform combining
microcontroller-based development boards, software tools, and
programming libraries that simplify the development of interactive
electronic and embedded systems.

-   **Hardware:** Arduino boards contain a microcontroller that executes
    programs and interfaces with external components such as sensors,
    LEDs, motors, displays, and communication devices.
-   **Software:** The Arduino Integrated Development Environment (IDE)
    provides tools for writing, compiling, and uploading programs,
    called sketches, to compatible boards.
-   **Programming:** Arduino programming is based primarily on C++, with
    a simplified programming framework and libraries that abstract many
    low-level hardware operations.
-   **Common Applications:**
    -   Reading analog and digital sensors.
    -   Controlling LEDs, motors, and actuators.
    -   Implementing serial communications.
    -   Developing prototypes and embedded control systems.
    -   Building interactive electronic devices.
-   **Example:** An Arduino Uno reads an analog voltage from a TMP36
    temperature sensor, converts the measurement into a temperature
    value, and transmits the result through its serial interface.
-   **Key Distinction:** Arduino is not a microcontroller or a
    programming language. It is an integrated hardware and software
    development platform built around microcontrollers.
-   **Related Terms:** Microcontroller · GPIO · ADC · PWM · IDE · Sketch
    · Embedded System

**Asynchronous Communication** -- Communication that does not use a
shared clock signal to coordinate data transmission. Devices must agree
on timing parameters, such as baud rate and data format, to communicate
reliably.

------------------------------------------------------------------------

### B

**Baud Rate** -- The number of signal symbols transmitted per second. In
a typical binary UART connection, one symbol represents one bit, so baud
rate and bit rate are usually equal. They are not necessarily equal in
other encoding schemes.

**Bit Rate** -- The number of data bits transmitted per second, commonly
expressed in bits per second (bps).

------------------------------------------------------------------------

### C

**Callback** -- A function passed to another function or subsystem for
execution when a specified event or condition occurs.

**CAN (Controller Area Network)** -- A communication protocol designed
to allow multiple electronic control units (ECUs) to communicate over a
shared network without requiring a separate communication wire for every
pair of devices. CAN uses differential signaling, message identifiers,
and arbitration to manage communication.

**Chip Select (CS/SS)** -- A control signal used in SPI communication to
select a specific peripheral. The selected device responds to
communication on the shared SPI bus. SS stands for Slave Select in
traditional SPI terminology.

**Closed Circuit** -- An electrical path that is complete and provides a
continuous route for current to flow.

**Contact Group** -- A set of switch terminals that are electrically
connected in a particular switch position or configuration.

**Contact Resistance** -- The small electrical resistance present
between two contacts when a switch or other mechanical contact is
closed.

**Continuity** -- The presence of an electrically conductive path
between two points.

**Continuity Test** -- A multimeter test used to determine whether an
electrical path exists between two points. Many meters produce an
audible beep when resistance falls below a threshold determined by the
instrument.

**Cross-Compiler** -- A compiler that runs on one computing platform,
called the host, but generates executable machine code intended to run
on a different platform, called the target. Cross-compilers are commonly
used in embedded development because the target microcontroller often
lacks the resources to compile its own software.

**Current-Limiting Resistor** -- A resistor used to control the amount
of current flowing through a component, such as an LED, to prevent
excessive current and potential damage.

------------------------------------------------------------------------

### D

**DAC (Digital-to-Analog Converter)** -- An electronic circuit or
integrated circuit that converts digital data into a corresponding
analog output, such as a voltage or current.

**Differential Signaling** -- A method of transmitting information using
the voltage difference between two signal wires rather than the voltage
of one signal wire relative to ground. It provides improved noise
resistance in many applications. CAN is an example.

**Digital Multimeter (DMM)** -- An electronic instrument used to measure
electrical quantities such as voltage, current, and resistance, and to
perform tests such as continuity and diode checks.

**Duty Cycle** -- The percentage of one complete signal period during
which a digital signal remains in its active state. In a typical
active-HIGH PWM signal, it represents the percentage of time the signal
is HIGH.

------------------------------------------------------------------------

### E

**Electronic Control Unit (ECU)** -- An embedded computer system that
manages and controls specific electrical systems or subsystems. ECUs are
commonly found in modern vehicles, industrial machinery, and aerospace
equipment.

**Embedded System** -- A computer-based system designed to perform one
or more specific functions as part of a larger electronic or mechanical
device. It combines hardware and software to monitor inputs, process
information, and control outputs.

-   **Hardware:** Typically includes a microcontroller or
    microprocessor, memory, input/output interfaces, and supporting
    electronic components.
-   **Software:** Embedded software, often called firmware, provides the
    instructions that govern the system's operation and interaction with
    connected hardware.
-   **Inputs:** Sensors, switches, communication interfaces, and other
    sources of external information.
-   **Outputs:** LEDs, displays, motors, relays, actuators,
    communication interfaces, and other controlled devices.
-   **Common Applications:**
    -   Automotive engine management and control systems.
    -   Medical monitoring and diagnostic equipment.
    -   Industrial automation and process control.
    -   Consumer electronics and appliances.
    -   Robotics and autonomous devices.
    -   Environmental monitoring and sensor networks.
-   **Example:** A temperature-monitoring system uses a TMP36 sensor to
    measure temperature, an Arduino microcontroller to process the
    analog voltage, and an LED or display to communicate the result.
-   **Key Distinction:** Unlike a general-purpose computer designed to
    run many different applications, an embedded system is designed
    around a particular function or set of related functions. It may
    operate independently or as part of a larger system.
-   **Related Terms:** Microcontroller · Microprocessor · Firmware ·
    GPIO · Sensor · Actuator · Real-Time System · Arduino

------------------------------------------------------------------------

### F

**Firmware** -- Software stored in non-volatile memory that provides
low-level instructions for operating and controlling electronic
hardware. Firmware is commonly found in microcontrollers, embedded
devices, and other electronic equipment.

**Flash Memory** -- A type of non-volatile memory that retains stored
information when power is removed. In microcontroller systems, flash
memory commonly stores program code and may also store bootloader
instructions.

**Floating Input** -- A digital input whose voltage is not driven to a
defined Logic HIGH or Logic LOW state. Floating inputs can respond
unpredictably to electrical noise and nearby signals.

**Full Duplex** -- A communication method that allows two devices to
transmit and receive data simultaneously.

------------------------------------------------------------------------

### G

**General-Purpose Input/Output (GPIO)** -- Configurable microcontroller
pins that can be programmed to function as digital inputs or outputs.
GPIO pins are commonly used to interface with switches, LEDs, sensors,
and other external hardware.

------------------------------------------------------------------------

### H

**Half Duplex** -- A communication method that allows data to travel in
both directions, but not simultaneously. Devices take turns transmitting
and receiving.

**Heap** -- A region of memory used for dynamic memory allocation.
Memory is requested at runtime and released when no longer needed.

**High-Impedance (Hi-Z)** -- An electrical state in which a pin presents
very high impedance, allowing very little current to flow through it.
The pin is effectively disconnected from actively driving the circuit
and may behave like a floating input unless an external circuit
establishes its voltage.

------------------------------------------------------------------------

### I

**I²C (Inter-Integrated Circuit)** -- A synchronous, serial
communication protocol that allows multiple integrated circuits to
communicate over a shared two-wire bus. The two signal lines are SDA
(data) and SCL (clock). Devices are typically identified by addresses,
and communication includes acknowledgment signals.

**IDE (Integrated Development Environment)** -- A software application
that provides tools for writing, editing, compiling, debugging, and
uploading programs. The Arduino IDE is one example.

**Input Flapping** -- The rapid, unintended oscillation of a digital
input between HIGH and LOW states due to electrical noise, switch
bouncing, or a floating input.

**Interrupt** -- A signal or event that causes the CPU to temporarily
suspend its normal program execution and respond to a specific event.
After servicing the event, the CPU returns to its previous execution
path and continues processing. On the Arduino Uno R3, the ATmega328P
supports external interrupts, pin-change interrupts, and timer
interrupts.

**Interrupt Service Routine (ISR)** -- A function executed in response
to an interrupt request. An ISR temporarily takes control of CPU
execution to service the event that triggered the interrupt, after which
normal program execution resumes. ISRs should generally be kept short
and avoid lengthy or blocking operations.

------------------------------------------------------------------------

### J

**Junction** -- A point at which two or more conductors or circuit
elements are electrically connected.

------------------------------------------------------------------------

### L

**Logic HIGH** -- A voltage level interpreted by a digital system as
binary 1. The actual voltage range recognized as HIGH depends on the
device's electrical specifications.

**Logic LOW** -- A voltage level interpreted by a digital system as
binary 0. The actual voltage range recognized as LOW depends on the
device's electrical specifications.

------------------------------------------------------------------------

### M

**Master In Slave Out (MISO)** -- One of the four standard signal lines
used in SPI communication. MISO carries data from the selected
peripheral to the controller. The traditional signal name remains in
common use, even as controller/peripheral terminology replaces
master/slave terminology.

**Master Out Slave In (MOSI)** -- One of the four standard signal lines
used in SPI communication. MOSI carries data from the controller to the
selected peripheral. The traditional signal name remains in common use.

**Memory Fragmentation** -- A condition in which available memory
becomes divided into smaller, separated blocks, making it difficult to
satisfy larger memory allocation requests. It is particularly relevant
to systems that use dynamic heap allocation.

**Microcontroller Unit (MCU)** -- A compact computer implemented on a
single integrated circuit. An MCU typically combines a CPU, memory, and
programmable input/output peripherals. Some systems may still require
external memory or supporting circuitry to perform their intended
functions.

**Microprocessor** -- A programmable processing unit that contains a CPU
on an integrated circuit. Unlike a typical microcontroller, a
microprocessor generally relies on external memory and peripheral
components to form a complete computing system.

**Momentary Switch** -- A switch that changes state only while being
actuated and returns to its normal state when released.

------------------------------------------------------------------------

### N

**Normally Closed (NC)** -- A switch configuration in which the contacts
are electrically connected in the default, unactuated state and become
disconnected when actuated.

**Normally Open (NO)** -- A switch configuration in which the contacts
are electrically disconnected in the default, unactuated state and
become connected when actuated.

------------------------------------------------------------------------

### O

**Open Circuit** -- An electrical path that is interrupted and does not
provide a continuous path for current to flow.

------------------------------------------------------------------------

### P

**Pinout** -- A diagram or description identifying the function of each
pin on an electronic component, integrated circuit, or connector. A
pinout identifies connections such as power, ground, signal input, and
signal output.

**Pointer** -- A variable that stores the memory address of another
variable or object rather than storing the referenced value itself.

**Poles and Throws (SPST, SPDT)** -- A method of describing switch
configurations based on the number of independent circuits controlled
and the number of connection paths available.

-   **SPST (Single Pole, Single Throw):** A simple on/off switch that
    controls one circuit. A common two-terminal switch is an example.
-   **SPDT (Single Pole, Double Throw):** A switch that connects one
    common terminal to one of two possible terminals.

**Polling** -- Repeatedly checking whether an event or condition has
occurred. A program may use polling to monitor a switch, sensor, or
hardware status register.

**Pull-Up and Pull-Down Circuits** -- Electrical configurations that use
resistors to establish a default HIGH (pull-up) or LOW (pull-down)
voltage level on a digital input when no other device is actively
driving that input. They prevent inputs from floating between logic
states.

**Pulse Width Modulation (PWM)** -- A technique that controls the
average power delivered to a load by rapidly switching a digital signal
between HIGH and LOW states and varying its duty cycle. PWM can simulate
an analog-like control effect, but the output remains a digital pulse
train unless additional filtering or circuitry is used.

------------------------------------------------------------------------

### Q

**Quantization** -- The process of mapping a continuous range of analog
values into a finite number of discrete digital levels. Quantization is
an inherent part of analog-to-digital conversion and introduces a small
measurement error known as quantization error.

------------------------------------------------------------------------

### R

**Real-Time Clock (RTC)** -- A dedicated, low-power integrated circuit
or hardware subsystem that maintains the current time and date, often
using a backup battery to preserve timekeeping when the main system is
powered off.

**Real-Time Operating System (RTOS)** -- A specialized operating system
designed to schedule and execute tasks so that they can meet defined
timing constraints. Real-time systems emphasize predictable response
times and deterministic behavior rather than simply maximizing
processing throughput.

**Reference Voltage (Vref)** -- A known voltage used by an
analog-to-digital converter as a reference for determining the digital
representation of an analog input. The reference voltage establishes the
ADC's measurement range and affects its voltage resolution.

**Resource-Constrained Environment** -- A computing environment in which
resources such as memory, processing power, storage, bandwidth, or
electrical power are limited and must be carefully managed.
Resource-constrained environments are common in embedded systems,
microcontrollers, IoT devices, and battery-powered electronics.

------------------------------------------------------------------------

### S

**Saturation** -- An operating condition in which a transistor is driven
fully ON as a switch. In an NPN bipolar junction transistor, the
collector-emitter voltage is typically low when the transistor is in
saturation.

**Sensor** -- A device that detects or measures a physical condition,
such as temperature, light, pressure, or motion, and produces an
electrical signal representing that measurement.

**Sensor Calibration** -- The process of comparing a sensor's
measurements against a known reference and determining whether
adjustments or corrections are needed to improve measurement accuracy.

**Serial Clock (SCK)** -- The clock signal used in synchronous serial
communication. In SPI, SCK synchronizes data transmission between the
controller and peripheral.

**Serial Monitor** -- A software tool, commonly included in the Arduino
IDE, that displays serial data transmitted by a connected board and
allows the user to send data back to it. It is frequently used for
debugging, testing, and observing sensor measurements.

**Signal Conditioning** -- Electronic circuitry placed between a
sensor's output and a microcontroller's input to make the signal
suitable for reliable processing. Signal conditioning may include
amplification, filtering, voltage scaling, buffering, or level shifting.

**Sketch** -- The name commonly used for an Arduino program. A sketch is
written in the Arduino programming environment, compiled, and uploaded
to a compatible board.

**SPI (Serial Peripheral Interface)** -- A synchronous serial
communication protocol commonly used between microcontrollers and
peripheral devices such as sensors, displays, and memory devices. SPI
typically uses four signal lines: SCK, MOSI, MISO, and CS/SS. It
supports full-duplex communication and generally does not use device
addresses; peripherals are selected using chip-select signals.

**Stack** -- A region of memory used to store local variables, function
parameters, and function return information. The stack grows and shrinks
automatically as functions are called and return.

**Stack Overflow** -- A condition that occurs when a program consumes
more stack memory than is available. It can result in corrupted data,
unpredictable behavior, or program failure.

**Switch** -- An electromechanical or electronic device used to open,
close, or redirect an electrical circuit.

**Synchronous Communication** -- Communication coordinated by a shared
clock signal that establishes when data is transmitted and sampled.

------------------------------------------------------------------------

### T

**Tactile Switch** -- A momentary push-button switch designed to provide
physical feedback, commonly a noticeable click, when pressed. Many small
tactile switches contain four physical pins arranged as two internally
connected pairs.

**Transfer Function** -- A mathematical relationship describing how a
system's output relates to its input. For a sensor, a transfer function
may describe how an electrical output voltage changes in response to a
measured physical quantity. The TMP36, for example, has a nominal output
relationship of 10 mV per degree Celsius with a 500 mV offset.

------------------------------------------------------------------------

### U

**UART (Universal Asynchronous Receiver-Transmitter)** -- A hardware
circuit used to transmit and receive asynchronous serial data between
two devices. UART communication typically uses separate transmit (TX)
and receive (RX) lines, a common ground, and agreed-upon settings such
as baud rate, data bits, parity, and stop bits.

------------------------------------------------------------------------

### V

**Volatile** -- A C/C++ keyword that tells the compiler that a
variable's value may change unexpectedly outside the normal flow of
program execution. It prevents certain compiler optimizations that could
otherwise assume the value remains unchanged. It is commonly used with
variables accessed by interrupt service routines or hardware registers.
`volatile` does not, by itself, make an operation atomic or guarantee
thread safety.

**Voltage Divider** -- A circuit composed of two or more resistors
connected in series that produces an output voltage that is a fraction
of the input voltage. The output voltage depends on the resistor values
and where the output is measured.

------------------------------------------------------------------------

## Glossary Maintenance Notes

This is a working reference that will grow alongside the
EmbeddedSystemsLab experiments and field reports.

New terminology should be added as concepts are introduced, tested, and
documented. Definitions should favor practical understanding while
maintaining technical accuracy.

**EmbeddedSystemsLab**\
*Measure it. Build it. Test it. Document it.*
