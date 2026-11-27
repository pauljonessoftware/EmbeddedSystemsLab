# Characterization of a TMP36 Temperature Sensor Using Arduino Measurements and C# Transfer Function Analysis

**Author:** Paul A. Jones, Jr.

*Senior Software & Embedded Systems Engineer*

*MSE Software Engineering, BS Electrical Engineering, BS Physics*

**Published:** November 26, 2026

**Report:** #10 — EmbeddedSystemsLab

**Professional Interests:** Embedded Systems · Arduino · C Programming · Electronics · .NET

**Contact:** [pauljonessoftware.com](https://pauljonessoftware.com) · `@paulajonesjr` · pauljonessoftware@gmail.com

## Abstract

The purpose of this experiment was to investigate the relationship between a TMP36 temperature sensor's analog output voltage, the resulting Arduino ADC reading, and the calculated temperature values derived from those measurements.

An Arduino-based test platform was first used to collect real-world sensor measurements. During evaluation of the collected data, several questions emerged regarding ADC resolution, sensor range utilization, and measurement precision. To investigate these questions, a custom C# console application was developed to model and analyze the transfer function of the measurement system.

The investigation demonstrated that a 10-bit ADC operating with a nominal $5\text{ V}$ reference provides a voltage resolution of approximately $4.88\text{ mV}$ per count. When used with a TMP36 sensor, this corresponds to a nominal temperature increment of approximately $0.49^\circ\text{C}$ per ADC count.

The study also demonstrated the effects of quantization and showed that the TMP36 utilizes only a portion of the available ADC range. Combining physical measurements with software analysis provided a deeper understanding of sensor behavior and measurement system limitations.

## 1. Objectives

The objectives of this experiment were:

* Measure temperature using a TMP36 sensor connected to an Arduino.

* Verify the relationship between ADC values, voltage, and temperature.

* Explore the operating characteristics of the TMP36 temperature sensor.

* Analyze ADC resolution and quantization effects.

* Compare theoretical sensor behavior with practical operating limits.

* Investigate the use of C# as an engineering analysis tool for electronics experimentation.

## 2. Background Theory

### 2.1 TMP36 Temperature Sensor

The TMP36 is a low-voltage analog temperature sensor with a linear output characteristic. Its output voltage is related to temperature by the following transfer equation:

$$
T_C = \frac{V_{\text{OUT}} - 500}{10}
$$

Where:

* $T_C$ = Temperature in degrees Celsius ($^\circ\text{C}$)

* $V_{\text{OUT}}$ = Sensor output voltage in millivolts ($\text{mV}$)

* $500$ = Nominal output voltage at $0^\circ\text{C}$, in millivolts

* $10$ = Sensor sensitivity, in millivolts per degree Celsius ($\text{mV}/^\circ\text{C}$)

Typical TMP36 operating points include:

| Temperature | Output Voltage | 
| ----- | ----- | 
| $-40^\circ\text{C}$ | $100\text{ mV}$ | 
| $0^\circ\text{C}$ | $500\text{ mV}$ | 
| $25^\circ\text{C}$ | $750\text{ mV}$ | 
| $100^\circ\text{C}$ | $1500\text{ mV}$ | 
| $125^\circ\text{C}$ | $1750\text{ mV}$ | 

### 2.2 Arduino ADC Resolution

The Arduino's 10-bit Analog-to-Digital Converter provides $1,024$ possible digital output values:

$$
0 \leq \text{ADC} \leq 1023
$$

Using a nominal $5\text{ V}$ reference:

$$
\text{Resolution} = \frac{5000\text{ mV}}{1024} = 4.8828125\text{ mV/count}
$$

Given the TMP36 sensitivity of $10\text{ mV}/^\circ\text{C}$, the corresponding nominal temperature increment is:

$$
\frac{4.8828125\text{ mV/count}}{10\text{ mV}/^\circ\text{C}} = 0.48828125^\circ\text{C/count}
$$

Therefore, each ADC count represents approximately $0.49^\circ\text{C}$ of temperature change under this configuration.

This value describes the nominal resolution of the measurement system. Actual measurement accuracy also depends on factors such as the ADC reference voltage, sensor characteristics, and electrical noise.

## 3. Equipment and Software

### Hardware

* Arduino microcontroller

* TMP36 temperature sensor

* Digital Multimeter

* Solderless Breadboard

* Jumper Wires

* USB connection

* Computer

### Software

* Arduino IDE

* C#

* Visual Studio

* .NET Console Application

## 4. Experimental Procedure

The experiment consisted of two complementary activities: physical measurement using an Arduino and software-assisted analysis using C#.

### 4.1 Part I — Hardware Measurement

A TMP36 temperature sensor was connected to an Arduino analog input (`A0`). The following sketch was developed to read the sensor, convert the resulting ADC value to voltage, calculate the temperature in Celsius and Fahrenheit, and report the results through the Serial Monitor:

```
int output;
float voltage;
float tempC;
float tempF;

void setup() {
  Serial.begin(9600);
}

void loop() {
  output = analogRead(A0);
  voltage = output * (5000.0 / 1024.0);
  tempC = (voltage - 500) / 10;
  tempF = (tempC * 9.0 / 5.0) + 32.0;

  Serial.print("Sensor Output: ");
  Serial.println(output);

  Serial.print("Voltage(mv): ");
  Serial.println(voltage);

  Serial.print("Temp (C): ");
  Serial.println(tempC);

  Serial.print("Temp (F): ");
  Serial.println(tempF);

  Serial.println();

  delay(5000);
}
```

Sensor readings were sampled every five seconds and displayed in both Celsius and Fahrenheit. The sketch provided a practical view of the complete measurement chain:

```
Physical Temperature
        |
        v
   TMP36 Sensor
        |
        v
  Output Voltage
        |
        v
    Arduino ADC
        |
        v
   Digital Value
        |
        v
Calculated Temperature
```

### 4.2 Part II — Identification of Questions

While reviewing the Arduino code and resulting measurements, additional questions emerged:

* What voltage corresponds to each ADC count?

* What temperature corresponds to each possible ADC value?

* How much temperature change does one ADC count represent?

* Can every temperature be measured exactly?

* What portion of the ADC range is actually used by the TMP36?

* What distinguishes the sensor's physical operating range from the mathematical limits of the conversion equation?

These questions motivated the development of a separate software analysis tool.

### 4.3 Part III — Software-Assisted Analysis

A C# console application was developed to model the behavior of the measurement system. Rather than work through the calculations manually, I wanted to generate the voltage and temperature associated with every possible ADC position and examine the resulting dataset.

The application implements three analysis modes:

1. **ADC-to-Voltage Characterization:** Generates the voltage corresponding to all $1,024$ possible ADC positions.

2. **Theoretical Temperature Characterization:** Calculates the theoretical temperature associated with every possible ADC value from $0$ through $1023$.

3. **Selected-Range Characterization:** Examines a selected range of ADC positions corresponding to the TMP36's operating region and extending beyond it.

The third mode uses ADC positions $20$ through $410$. This produces a calculated temperature range of approximately $-40^\circ\text{C}$ through $+150^\circ\text{C}$. The extended upper range allows examination of the mathematical conversion beyond the TMP36's specified operating range of approximately $-40^\circ\text{C}$ through $+125^\circ\text{C}$.

### 4.4 C# Software Analysis Tool

#### Development Environment

The application was developed using:

* C#

* Visual Studio

* .NET Console Application

The program was intended as an exploratory engineering tool. Its purpose was to investigate the behavior of the sensor and ADC conversion process, not to serve as a production application.

#### Complete Source Code

The following source code implements the three analysis modes described above:

```
using System;
using System.Collections.Generic;
using System.Text;

namespace Tmp36Sensor
{
    public class Program
    {
        public static void Main(string[] args)
        {
            //displayAllPossibleVoltageValues();
            //displayTheoreticalTmpRange();
            displayRealWorldTmpRange();
        }

        private static void displayRealWorldTmpRange()
        {
            Console.WriteLine("All Possible Temperature Values:\n");

            for (int position = 20; position < 411; position++)
            {
                double vOut = (5000.0 / 1024.0) * position;
                double tempC = (vOut - 500.0) / 10.0;
                string message = $"Position: {position} => Voltage: {vOut} mV => Temperature: {tempC} °C";
                Console.WriteLine(message);
            }
        }

        private static void displayTheoreticalTmpRange()
        {
            Console.WriteLine("All Theoretical Temperature Values:\n");

            for (int position = 0; position < 1024; position++)
            {
                double vOut = (5000.0 / 1024.0) * position;
                double tempC = (vOut - 500.0) / 10.0;
                string message = $"Position: {position} => Voltage: {vOut} mV => Temperature: {tempC} °C";
                Console.WriteLine(message);
            }
        }

        private static void displayAllPossibleVoltageValues()
        {
            // voltage / output = 5000 mv / 1024 possible values
            Console.WriteLine("All Possible Voltage Values:\n");

            for (int position = 0; position < 1024; position++)
            {
                double vOut = (5000.0 / 1024.0) * position;
                string message = $"Value: {position} => Voltage {vOut} mV";
                Console.WriteLine(message);
            }
        }
    }
}
```

#### Application Execution

The application can be executed as a standard .NET console application. The desired analysis mode is selected by uncommenting its corresponding method call in `Main()` and commenting out the other calls.

The three modes provide different views of the measurement system:

| Analysis Mode | Method | Purpose | 
| ----- | ----- | ----- | 
| **ADC-to-Voltage** | `displayAllPossibleVoltageValues()` | Examines all possible ADC-to-voltage conversions | 
| **Theoretical Temperature** | `displayTheoreticalTmpRange()` | Calculates temperatures across the complete ADC range | 
| **Selected Range** | `displayRealWorldTmpRange()` | Examines ADC positions $20$–$410$ | 

The C# application does not require an Arduino or a connected TMP36 sensor. It performs its calculations using the mathematical relationships established by the sensor's transfer function and the assumed ADC reference voltage. This makes it possible to investigate the theoretical behavior of the measurement system independently of the physical hardware.

The two programs serve complementary purposes:

* The Arduino reads the actual sensor and reports measured values.

* The C# application models the conversion process and explores the system's theoretical behavior.

Together, they provide both an experimental and analytical view of the same measurement system.

## 5. Experimental Results

### 5.1 Representative Data

The C# application generated the following representative values:

| ADC Value | Voltage ($\text{mV}$) | Temperature ($^\circ\text{C}$) | 
| ----- | ----- | ----- | 
| $20$ | $97.66$ | $-40.23$ | 
| $50$ | $244.14$ | $-25.59$ | 
| $102$ | $498.05$ | $-0.20$ | 
| $103$ | $502.93$ | $0.29$ | 
| $154$ | $751.95$ | $25.20$ | 
| $205$ | $1000.98$ | $50.10$ | 
| $307$ | $1499.02$ | $99.90$ | 
| $358$ | $1748.05$ | $124.80$ | 

### 5.2 ADC Resolution

The analysis verified that each ADC count represents approximately:

$$
4.8828125\text{ mV}
$$

of voltage change.

### 5.3 Temperature Resolution

The corresponding nominal temperature increment was calculated as:

$$
0.48828125^\circ\text{C}
$$

per ADC count. This represents the temperature difference between adjacent ADC readings under the assumed $5\text{ V}$ reference configuration.

### 5.4 Quantization Effects

The generated dataset demonstrated that many temperature values cannot be represented exactly by the ADC. For example:

| ADC Value | Calculated Temperature | 
| ----- | ----- | 
| $102$ | $-0.195^\circ\text{C}$ | 
| $103$ | $0.293^\circ\text{C}$ | 

Neither ADC value corresponds exactly to $0.000^\circ\text{C}$. This illustrates the quantization effects inherent in digital measurement systems. The analog signal is converted into one of a finite number of digital values, limiting the resolution of the resulting measurement.

### 5.5 Sensor Operating Range

The TMP36's specified operating range is approximately $-40^\circ\text{C}$ through $+125^\circ\text{C}$. Using the assumed $5\text{ V}$ ADC reference, these temperatures correspond approximately to:

* **ADC** $20$ at $-40^\circ\text{C}$

* **ADC** $358$ at $+125^\circ\text{C}$

The sensor's operating range therefore occupies approximately $338$ ADC count intervals out of the available $1,024$.

### 5.6 ADC Utilization

The approximate ADC utilization is:

$$
\frac{358 - 20}{1024} \times 100 \approx 33.0\%
$$

The TMP36 therefore uses approximately one-third of the available ADC range when connected to an Arduino operating with a nominal $5\text{ V}$ reference.

## 6. Analysis and Discussion

The initial Arduino experiment provided individual measurements of temperature and voltage. While these observations confirmed the sensor's operation, they also raised broader questions concerning system behavior and measurement limitations.

The subsequent C# analysis transformed the investigation from a measurement exercise into a characterization exercise. Instead of evaluating individual samples, the software generated ADC states and their associated voltage and temperature values.

Several important observations emerged:

1. The TMP36 temperature equation can be evaluated mathematically across a much wider range than the sensor can physically produce.

2. The Arduino ADC introduces quantization effects that limit measurement resolution.

3. A single ADC count corresponds to approximately $0.49^\circ\text{C}$ of temperature change.

4. The TMP36 utilizes only about one-third of the ADC's available range when operating with a $5\text{ V}$ reference.

5. Software can reveal system-level behavior that is difficult to observe through isolated measurements.

An unexpected outcome of the experiment was the realization that programming can serve as a powerful laboratory tool. The same software development skills typically used for application development can also be applied to analyze circuits, characterize sensors, generate lookup tables, investigate transfer functions, and validate engineering assumptions.

The Arduino provided the physical measurements. The C# application provided a means to explore the underlying mathematical behavior of the measurement system.

## 7. Conclusion

The objectives of this experiment were successfully achieved.

A TMP36 sensor was connected to an Arduino and used to generate temperature measurements from real-world sensor data. During analysis of the results, questions regarding system behavior led to the development of a C# application capable of characterizing the measurement chain.

The combined hardware and software investigation quantified ADC resolution, demonstrated quantization effects, and identified the relationship between the sensor's operating range and the available ADC range. The experiment also highlighted the distinction between theoretical mathematical behavior and real-world device limitations.

Perhaps the most significant lesson learned is that software and electronics are complementary disciplines. Hardware measurements provide observations, while software analysis provides understanding. Together, they enable a deeper exploration of engineering systems than either approach alone.

## 8. Lessons Learned

* A 10-bit ADC with a nominal $5\text{ V}$ reference provides a resolution of approximately $4.88\text{ mV}$ per count.

* The TMP36 sensor produces approximately $10\text{ mV}$ per degree Celsius.

* Each ADC count represents approximately $0.49^\circ\text{C}$ under the assumed configuration.

* Quantization prevents exact representation of many temperature values.

* The TMP36 utilizes only a fraction of the available ADC range.

* Complete datasets reveal patterns that individual calculations often hide.

* C# can function as a valuable engineering analysis tool alongside traditional laboratory instruments.

## 9. Key Takeaway

> *The Arduino provided the measurements; the C# program revealed the system.*

## 10. Personal Reflection

This experiment produced an unexpected outcome. What began as a simple effort to read a TMP36 temperature sensor evolved into a much deeper exploration of measurement systems, ADC resolution, transfer functions, quantization, and software-assisted analysis.

The questions raised by a few lines of Arduino code ultimately led to the development of a separate C# application and a far more complete understanding of the sensor than originally anticipated.

Perhaps the most surprising aspect of this exercise is personal rather than technical. At nineteen years old, I was focused primarily on getting circuits to work, solving assigned problems, and completing laboratory exercises. I could not have imagined spending a Thanksgiving afternoon voluntarily investigating the mathematical behavior of a temperature sensor, generating hundreds of data points, writing analysis software, and enjoying every minute of the process. Yet that is exactly what happened.

What stands out most is the realization that learning has become its own reward. There was no assignment to complete, no examination to prepare for, and no grade attached to the outcome. The investigation was driven entirely by curiosity. A simple question about a sensor became an opportunity to connect electronics, programming, mathematics, and engineering analysis into a single learning experience.

Looking back, the younger version of myself might be surprised by the amount of enthusiasm devoted to what appears, on the surface, to be a humble temperature sensor. Looking forward, however, this experiment serves as evidence that genuine understanding is often found by following questions beyond their original scope.

In that respect, this Thanksgiving exercise was not merely a sensor lab. It was a reminder that the spirit of engineering is alive and well, and that learning remains one of the most rewarding journeys I have ever undertaken.

## 11. Embedded Systems Engineering Glossary

* **Quantization:** The process of mapping a continuous range of analog input values (such as a sensor's voltage output) into a finite set of discrete digital levels or integer steps during Analog-to-Digital Conversion (ADC). The step size between adjacent levels introduces a fundamental resolution limit—known as quantization error—where intermediate analog values are rounded to the nearest available digital count.

**End of Field Report #10**

**Status:** Successfully Completed

---

**Measure it. Build it. Test it. Document it.**