# SRAM Operations Explanation

## WRITE Operation (WRITE 0 / WRITE 1)
- **Write = HIGH, Word Line (WL) = HIGH**
- Access transistors turn ON → cell connects to bitline
- Input data **V(d)** is forced onto the bitline
- Internal node **Q** updates according to input data
- Cross-coupled inverters flip if needed and store new value

### Observation
- **Q changes state** during this region

### Bitline Behavior
- Bitline directly follows the input data
- Strong driver forces it → large, fast transitions

---

## HOLD Operation (HOLD 0 / HOLD 1)
- **Write = LOW, Word Line = LOW**
- Access transistors OFF → cell isolated from bitline
- No external influence on the cell

### Observation
- **Q remains constant** (data retained)

### Bitline Behavior
- Bitline remains mostly unchanged or floating
- Small variations may occur due to leakage or previous charge

---

## READ Operation (READ 0 / READ 1)
- **Write = LOW, Word Line = HIGH**
- Bitline is precharged to **VDD** before read
- **Sense Enable (SE) = HIGH** activates sense amplifier

### Operation
- Cell connects to bitline through access transistor
- Stored value at **Q** slightly pulls bitline up or down
- Sense amplifier detects this small voltage difference

### Observation
- **Q remains stable** (ideally no change)
- Sense signal provides output

### Bitline Behavior
- Bitline is first precharged to HIGH (≈ VDD)
- During read:
  - If **Q = 0** → bitline discharges slightly
  - If **Q = 1** → bitline remains near VDD
- Discharge is small (not full swing) because:
  - Cell is weaker than precharge circuitry
  - Prevents disturbance of stored data
