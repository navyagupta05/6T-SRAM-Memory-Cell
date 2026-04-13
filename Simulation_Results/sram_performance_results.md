# SRAM Performance Results

## Power Consumption
- **Pavg ≈ 57.1 µW**
- Negative sign indicates power drawn from VDD
- Value is within expected range for **180 nm design**

---

## Write Delay
- **t_write ≈ 10.46 ns**
- Time taken for Q to update after write operation
- Relatively higher → indicates scope for **write optimization**

---

## Read Delay
- **t_read ≈ 0.93 ns**
- Time for bitline/sense amplifier to detect stored data
- Faster than write, as expected

---

## Overall Analysis
- Read operation is faster than write (typical SRAM behavior)
- Power consumption is reasonable for given technology
- Write delay is the **limiting factor in performance**

---

## Conclusion
- The SRAM cell operates correctly in all modes
- Performance trade-off observed between:
  - **Stability (SNM)**
  - **Write Speed**
- Design can be further optimized for **faster write operation**
