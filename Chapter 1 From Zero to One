# Chapter 1 Reading Notes - From Zero to One

## 1.1 The Game Plan
*   **Goal**: Teach how to design and build a microprocessor
*   **Learning Path**: Logic Gates → Combinational Modules (e.g., adders) → Assembly Language → Microprocessor
*   **Major Theme**: Managing complexity

## 1.2 The Art of Managing Complexity

### Abstraction
* Hiding details when not important
* **Levels of abstraction for computer systems**:
  - Physics → Devices → Analog Circuits → Digital Circuits → Logic Design → Microarchitecture → Architecture → Operating System → Application Software

### Discipline
* Restricting design choices to work more productively
* **Digital discipline**: Uses discrete voltages (0/1) instead of continuous analog voltages

### The Three "-Y's"
* **Hierarchy**: Dividing system into modules and submodules
* **Modularity**: Modules have well-defined functions and interfaces
* **Regularity**: Reusing modular components

## 1.3 The Digital Abstraction
* **Discrete-valued variables**: Finite number of values vs continuous physical variables
* **Binary representation**: Easier to distinguish two voltages than ten
* **Information measurement**: `D = log₂N bits`
* **Binary variable**: Carries 1 bit of information
* **Boolean logic**: Operates on binary variables (TRUE/FALSE, 1/0, HIGH/LOW)

## 1.4 Number Systems

### Decimal (Base 10)
* Digits: 0-9
* Column weights: powers of 10

### Binary (Base 2)
* Digits: 0, 1
* Column weights: powers of 2 (1, 2, 4, 8, 16...)

### Hexadecimal (Base 16)
* Digits: 0-9, A(10), B(11), C(12), D(13), E(14), F(15)
* Each hex digit = 4 binary digits (nibble)

### Data Units
* **Bit**: Binary digit
* **Nibble**: 4 bits
* **Byte**: 8 bits
* **Word**: Processor-dependent (32 or 64 bits)

### Binary Addition
* Similar to decimal addition
* Carry bit propagated when sum is 2 or 3 (10₂ or 11₂)

### Signed Binary Numbers

#### Sign/Magnitude
* MSB = sign (0=positive, 1=negative)
* Remaining bits = magnitude
* Two representations for zero (+0 and -0)

#### Two's Complement
* MSB has negative weight
* **Range for N-bit number**: `[–2^(N–1) to 2^(N–1) – 1]`
* **Sign reversal**: Invert all bits, then add 1
* **Overflow**: Occurs when same-sign addition produces opposite-sign result
* **Sign extension**: Copy sign bit to all new MSB positions

## 1.5 Logic Gates
* **NOT**: `Y = A̅`
* **AND**: `Y = A • B`
* **OR**: `Y = A + B`
* **XOR**: `Y = A ⊕ B` (TRUE if odd number of inputs are TRUE)
* **NAND**: `Y = A • B‾`
* **NOR**: `Y = A + B‾`
* **XNOR**: `Y = A ⊕ B‾` (Equality gate)

## 1.6 Beneath the Digital Abstraction

### Logic Levels
* **VOH**: Minimum output voltage for HIGH
* **VOL**: Maximum output voltage for LOW
* **VIH**: Minimum input voltage interpreted as HIGH
* **VIL**: Maximum input voltage interpreted as LOW
* **Forbidden zone**: Region between VIL and VIH

### Noise Margins
* **NML** = `VIL – VOL` (Low noise margin)
* **NMH** = `VOH – VIH` (High noise margin)

### Static Discipline
* Gates must produce valid outputs from valid inputs
* Enables composition of larger systems

## 1.7 CMOS Transistors

### nMOS Transistor
* Turns ON when gate = 1 (HIGH)
* Passes strong 0 (LOW) but weak 1 (HIGH)

### pMOS Transistor
* Turns ON when gate = 0 (LOW)
* Passes strong 1 (HIGH) but weak 0 (LOW)

### CMOS
* Uses complementary nMOS and pMOS networks
* Low static power consumption

## 1.8 Power Consumption

### Dynamic Power
* Power used to charge capacitances during switching
* Formula: `P_dynamic = α C V_DD² f`
  - `α` = activity factor
  - `C` = capacitance
  - `V_DD` = supply voltage
  - `f` = frequency

### Static Power
* Power consumed when system is idle (leakage current)
* Formula: `P_static = I_DD V_DD`
  - `I_DD` = quiescent supply current
