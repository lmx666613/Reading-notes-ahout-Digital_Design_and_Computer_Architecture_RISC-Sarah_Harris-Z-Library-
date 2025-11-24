# Chapter 2: Combinational Logic Design - Reading Notes

## 2.1 Introduction

### Circuit Definition
- A **circuit** processes discrete-valued variables with:
  - Input/output terminals
  - Functional specification (input-output relationship)
  - Timing specification (delay between input change and output response)

### Circuit Composition
- **Elements**: Circuits with inputs, outputs, and specifications
- **Nodes**: Wires carrying discrete-valued variables
  - Input nodes: Receive values from external world
  - Output nodes: Deliver values to external world
  - Internal nodes: Wires that are neither inputs nor outputs

### Combinational vs Sequential Circuits
- **Combinational**: Outputs depend only on current inputs (memoryless)
- **Sequential**: Outputs depend on current AND previous inputs (has memory)

### Combinational Composition Rules
A circuit is combinational if:
1. Every circuit element is combinational
2. Every node is either an input or connects to exactly one output terminal
3. No cyclic paths (each path visits nodes at most once)

### Bus Notation
- Single line with slash and number indicates **bus** (bundle of signals)
- Example: `A[3:0]` represents 4-bit bus

## 2.2 Boolean Equations

### Terminology
- **Complement**: Inverse of variable (`¬A`)
- **Literal**: Variable or its complement (`A`, `¬A`, `B`, `¬B`)
- **Implicant**: AND of one or more literals (`AB`, `ABC`, `B`)
- **Minterm**: Product involving ALL inputs to function (`ABC` for 3 variables)
- **Maxterm**: Sum involving ALL inputs to function (`A+B+C` for 3 variables)

### Operator Precedence
1. NOT (highest)
2. AND
3. OR (lowest)

### Canonical Forms
#### Sum-of-Products (SOP)
- Sum of minterms where output is TRUE
- Example: `Y = A·B + A·B` or `Y = Σ(m1, m3)`

#### Product-of-Sums (POS)
- Product of maxterms where output is FALSE
- Example: `Y = (A+B)·(A+B)` or `Y = Π(M0, M2)`

### Selection Guide
- Use SOP when output TRUE in few rows
- Use POS when output FALSE in few rows

## 2.3 Boolean Algebra

### Axioms (Fundamental Rules)
- A1: B = 0 if B ≠ 1 A1': B = 1 if B ≠ 0
- A2: 0 = 1 A2': 1 = 0
- A3: 0·0 = 0 A3': 1+1 = 1
- A4: 1·1 = 1 A4': 0+0 = 0
- A5: 0·1 = 1·0 = 0 A5': 1+0 = 0+1 = 1
  
### Key Theorems

#### Single Variable Theorems
- **Identity**: `B·1 = B`, `B+0 = B`
- **Null Element**: `B·0 = 0`, `B+1 = 1`
- **Idempotency**: `B·B = B`, `B+B = B`
- **Involution**: `¬(¬B) = B`
- **Complements**: `¬B·B = 0`, `¬B+B = 1`

#### Multi-Variable Theorems
- **Commutativity**: `B·C = C·B`, `B+C = C+B`
- **Associativity**: `(B·C)·D = B·(C·D)`, `(B+C)+D = B+(C+D)`
- **Distributivity**: `B·(C+D) = (B·C)+(B·D)`, `B+(C·D) = (B+C)·(B+D)`
- **Covering**: `B·(B+C) = B`, `B+(B·C) = B`
- **Combining**: `(B·C)+(B·C) = B`, `(B+C)·(B+C) = B`
- **Consensus**: `(B·C)+(¬B·D)+(C·D) = (B·C)+(¬B·D)`
- **De Morgan's**: `¬(B·C) = ¬B + ¬C`, `¬(B+C) = ¬B · ¬C`

### Proof Methods
- **Perfect Induction**: Prove by testing all possible input combinations
- Equation minimization goal: Fewest implicants with fewest literals

## 2.4 From Logic to Gates

### Schematic Guidelines
- Inputs on left/top, outputs on right/bottom
- Gates flow left to right
- Use straight wires when possible
- Wires connect at T junctions
- Dots indicate connections, crossings without dots are not connected

### Implementation Styles
- **Two-level logic** (SOP form): NOT → AND → OR
- **Programmable Logic Array (PLA)**: Systematic array of inverters, ANDs, ORs
- **CMOS optimization**: Prefer NAND/NOR gates over AND/OR

### Multiple Output Circuits
- Example: 4-input priority circuit
- Output equations by inspection: `Y3 = A3`, `Y2 = A3·A2`, etc.
- **Don't cares (X)**: Used when input combinations don't affect output

## 2.5 Multilevel Combinational Logic

### Advantages
- Reduces hardware compared to two-level logic
- Example: 3-input XOR requires 4 AND gates + 1 OR gate in two-level, but only 2 XOR gates in multilevel

### Bubble Pushing Rules
1. Start at output and work toward inputs
2. Push output bubbles back to inputs
3. Cancel bubbles between gates
4. Change gate body (AND↔OR) when pushing bubbles

## 2.6 X's and Z's

### Illegal Value: X
- **Contention**: Node driven to both 0 and 1 simultaneously
- Causes: Unknown values, uninitialized inputs, fighting gates
- Can cause excessive power consumption and damage

### Floating Value: Z
- **High impedance**: Node not driven to any value
- **Tristate buffer**: Three output states (0, 1, Z)
- **Active high/low enable**: Control when buffer is enabled
- Used for shared buses in multi-chip systems

## 2.7 Karnaugh Maps

### Basic Concepts
- Graphical method for logic minimization (up to 4 variables)
- **Gray code ordering**: Adjacent squares differ in only one variable
- **Wraparound**: Map edges are considered adjacent

### K-map Rules
1. Use fewest circles to cover all 1's
2. Circles must contain only 1's
3. Circle sizes must be powers of 2 (1, 2, 4, 8...)
4. Circles should be as large as possible
5. Circles can wrap around edges
6. 1's can be circled multiple times

### Don't Cares in K-maps
- **X entries**: Can be 0 or 1
- Circle X's if they help make larger circles
- Ignore X's if not helpful for minimization

## 2.8 Combinational Building Blocks

### Multiplexers (Mux)
- **2:1 Mux**: `Y = S·D0 + S·D1`
- **4:1 Mux**: Needs 2 select lines
- **Implementation**: SOP logic, tristates, or hierarchical 2:1 muxes
- **Logic functions**: Can implement any N-input function with 2^N-input mux

### Decoders
- **N:2^N decoder**: N inputs, 2^N outputs
- **One-hot outputs**: Exactly one output HIGH at a time
- **Implementation**: AND gates with true/complementary inputs
- **Logic functions**: Combine with OR gates to sum minterms

## 2.9 Timing

### Key Concepts
- **Timing diagram**: Shows transient response
- **Rising/falling edge**: LOW→HIGH and HIGH→LOW transitions
- **50% point**: Measurement reference for delays

### Delay Types
- **Propagation delay (tpd)**: Maximum input-to-output delay
- **Contamination delay (tcd)**: Minimum input-to-output delay
- **Critical path**: Longest path through circuit (determines tpd)
- **Short path**: Shortest path through circuit (determines tcd)

### Glitches
- **Causes**: Different path delays, crossing prime implicant boundaries
- **Solutions**: Add consensus terms, but not always fixable
- **Impact**: Usually harmless if propagation delay is waited out

## 2.10 Summary

### Key Points
- Combinational circuits: Outputs depend only on current inputs
- Boolean algebra: Foundation for logic simplification
- K-maps: Visual minimization tool (2-4 variables)
- Building blocks: Multiplexers, decoders, priority circuits
- Timing: Critical for circuit performance
- Modern practice: CAD tools handle large optimizations

### Implementation Choices
- **Two-level vs multilevel**: Trade-off between speed and hardware
- **Gate types**: NAND/NOR preferred in CMOS
- **Design constraints**: Area, speed, power, cost
