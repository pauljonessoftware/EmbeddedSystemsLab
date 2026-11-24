# Empirical Validation of the TMP36 Analog Temperature Sensor

**Author:** Paul A. Jones, Jr.  
*Senior Software & Embedded Systems Engineer*  
*MSE Software Engineering, BS Electrical Engineering, BS Physics*

**Published:** November 20, 2026  
**Report:** #9 — EmbeddedSystemsLab  
**Professional Interests:** Embedded Systems · Arduino · C Programming · Electronics · .NET  
**Contact:** [pauljonessoftware.com](https://pauljonessoftware.com) · `@paulajonesjr` · pauljonessoftware@gmail.com

---

## Technical Infographic

![TMP36 Analog Temperature Sensor — Quick Reference Cheat Sheet](../images/TMP36Sensor.jpg)

---

## Equipment List

- **TMP36** (TO-92 package)
- **Arduino Uno** (5.0 V and 3.3 V power rails)
- **Digital multimeter**
- **Solderless breadboard**

## Objective

Validate the transfer function and dynamic thermal response of an active, solid-state analog temperature sensor (TMP36) using direct multimeter voltage measurements. Establish a physical measurement baseline before integrating the sensor with microcontroller Analog-to-Digital Conversion (ADC) and serial communications.

## Architecture & Transfer Function

Unlike passive resistive sensors such as an LDR, the TMP36 is an active, voltage-output temperature sensor. It requires external power and ground connections and produces an analog output voltage proportional to temperature.

Its low-output-impedance design allows it to interface directly with analog measurement circuitry.

The TMP36 transfer function is:

$$
V_{\text{out}} = 0.50\text{ V} +
(0.010\text{ V}/^\circ\text{C} \times T_{^\circ\text{C}})
$$

Solving for temperature in degrees Celsius:

$$
T_{^\circ\text{C}} =
\frac{V_{\text{out}}-0.50\text{ V}}{0.010\text{ V}/^\circ\text{C}}
$$

Key characteristics:

- **Offset (0.50 V at 0°C):** Allows measurement of sub-zero temperatures without requiring a negative supply voltage.
- **Scale factor (10 mV/°C):** Provides a nominal output change of 10 mV for every 1°C temperature change.
- **Operating range:** -40°C to +125°C.
- **Supply voltage:** 2.7 V to 5.5 V.

The nominal transfer function is independent of whether the sensor is powered from the Arduino's 3.3 V or 5.0 V rail, provided the supply remains within its specified operating limits.

### Pinout Reference (TO-92 Package)

With the flat face of the package toward the observer and the leads pointing downward:

- **Left pin (Vs):** Positive DC supply.
- **Center pin (Vout):** Analog voltage output.
- **Right pin (GND):** Ground reference.

## Experimental Procedure & Bench Diagnostics

### 1. Initial Circuit Topology Correction

My initial measurements were unexpectedly low. After reviewing the circuit, I discovered that I had reversed the TMP36's supply polarity.

I had carried over some of the wiring habits from the previous voltage-divider experiment and failed to verify the sensor's pin orientation before applying power.

I corrected the wiring, confirmed the pinout against the datasheet, and repeated the measurements. The sensor then produced output voltages consistent with its expected transfer function.

Fortunately, the sensor continued to operate normally after the wiring error.

### 2. Package Orientation & Polarity Verification

During subsequent testing, I encountered additional anomalous readings:

- 0.432 V with a 5.0 V supply.
- 0.380 V with a 3.3 V supply.

Further investigation pointed to an incorrect physical orientation of the sensor on the breadboard.

I rechecked the TO-92 package orientation against the datasheet, verified the flat-face reference, and reseated the leads. The discrepancy disappeared, and the sensor returned to producing expected output voltages.

This reinforced an important bench practice: verify component orientation and pin assignments before applying power.

### 3. Baseline & Dynamic Thermal Stimulus Testing

With the sensor powered from the Arduino's 5.0 V rail, I measured the output directly between Vout (center pin) and GND (right pin) using a digital multimeter.

I first recorded the ambient baseline, then applied a brief and sustained thermal stimulus by pinching the plastic sensor package between my fingers.

| Test Phase | Condition / Stimulus | Measured Vout | Calculated Temp (°C) | Calculated Temp (°F) | Notes |
|---|---|---:|---:|---:|---|
| **Baseline** | Unperturbed ambient room air | 0.733 V | 23.3°C | 73.9°F | Stable steady-state output |
| **Initial Stimulus** | Brief pinch on plastic package | 0.740 V | 24.0°C | 75.2°F | +7 mV initial rise |
| **Sustained Stimulus** | 15-second pinch on plastic body | 0.771 V | 27.1°C | 80.8°F | +38 mV rise from baseline |
| **Recovery** | Released to ambient air | → 0.733 V | → 23.3°C | → 73.9°F | Returned smoothly toward baseline |

The measurements demonstrated a clear relationship between applied thermal stimulus and output voltage. Following release, the output gradually returned toward its original ambient baseline.

## Key Engineering Takeaways

- **Active vs. Passive Topology:** Unlike a passive resistive sensor, the TMP36 contains active circuitry and requires a properly connected supply and ground. Its power connections should not be treated like a passive voltage-divider circuit.

- **Physical Package Verification:** Always verify the physical orientation of a component against its datasheet before applying power. Reversing the supply connections can expose internal circuitry to damaging reverse voltage.

- **Thermal Response:** The TO-92 package introduces thermal lag between the external stimulus and the internal sensing element. The difference between the brief and sustained contact measurements demonstrates that the sensor's output responds over time rather than instantaneously.

- **ADC Readiness:** Establishing the 0.733 V (23.3°C) and 0.771 V (27.1°C) measurement points with a digital multimeter provides useful reference values for validating `analogRead()` quantization, ADC resolution, and reference-voltage calculations in the next stage.

## Embedded Systems Engineering Glossary

As part of this report, I also made several updates to my [Embedded Systems Engineering Glossary](../embedded_systems_glossary.md):

- Added several new serial communications-related terms.
- Reorganized existing entries to make the glossary easier to navigate and search.
- Updated the glossary in GitHub.

---

**Measure it. Build it. Test it. Document it.**