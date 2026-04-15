# 6T SRAM SNM Analysis

## Overview

Static Noise Margin (SNM) analysis was performed using butterfly curves derived from DC simulations of a 6T SRAM cell at **VDD = 1.8 V**.

---

## Hold SNM

* Condition: **Wordline OFF (Hold Mode)**
* Method: Butterfly curve analysis (maximum square fitting)

**Result:**

* Hold SNM ≈ **0.32 V**

**Observations:**

* Strong inverter symmetry
* Large noise margin
* Stable data retention

---

## Read SNM

* Condition: **Wordline ON (Read Mode)**
* Method: Numerical extraction from VTC data

**Result:**

* Read SNM ≈ **0.19 V**

**Observations:**

* Reduced stability due to access transistor loading
* Read disturb effect present
* Typical degradation for 6T SRAM

---

## Comparison

| Metric   | Value  |
| -------- | ------ |
| Hold SNM | 0.32 V |
| Read SNM | 0.19 V |

* Read SNM is ~40% lower than Hold SNM
* Indicates moderate read stability degradation

---

## Conclusion

The designed 6T SRAM cell demonstrates:

* Strong hold stability
* Acceptable read stability
* Expected 6T SRAM behavior

---

## Possible Improvements

* Increase pull-down NMOS strength (β ratio)
* Reduce access transistor strength
* Apply assist techniques:

  * Wordline underdrive
  * Bitline boosting

---
