# Simple 8-bit CPU Specification

This document describes a basic 8-bit CPU architecture including its storage system and instruction set.

---

## Storage System

### Registers

- `PC`: Program Counter  
- General-purpose registers (8-bit wide):  
  - `R0` (also referred to as `RA`)
  - `R1`
  - `R2`
  - `R3`

### Memory

- Size: **16 bytes**
- Access granularity: **byte-addressable**
- Address range: `0x0` – `0xF`

---

## Instruction Set

All instructions are **1 byte (8 bits)** long. There are two main formats:

1. **Register-type instructions** (use two registers)
2. **Memory-type instructions** (use a memory address)

### Encoding Formats

| Instruction | Binary Format     | Description |
|-------------|-------------------|-------------|
| `mov`       | `0000 rtrs`     | Copy value from register `rs` to register `rt` |
| `add`       | `0001 rtrs`     | Add contents of `rs` to `rt`, store result in `rt` |
| `load`      | `1110 addr`       | Load value from memory address `addr` into `R0` |
| `store`     | `1111 addr`       | Store value from `R0` into memory address `addr` |

- `rt`: target register (2 bits)  
- `rs`: source register (2 bits)  
- `addr`: 4-bit memory address (for 16 bytes of memory)

---

## Notes

- Only 2-bit fields are needed to select among the four registers (`R0`–`R3`).
- `load` and `store` always operate on `R0`.
- Memory is accessed directly using 4-bit addresses.

---

## Example Register Encoding

| Register | Code |
|----------|------|
| `R0`     | `00` |
| `R1`     | `01` |
| `R2`     | `10` |
| `R3`     | `11` |

---

## Example Instructions (Binary)

- `mov R1, R0` -> `0000 01 00` -> `0x04`
- `add R2, R3` -> `0001 10 11` -> `0x1B`
- `load 0xF`   -> `1110 1111` -> `0xEF`
- `store 0xA`  -> `1111 1010` -> `0xFA`

---

Feel free to modify or expand the instruction set as needed for your test cases, simulation or project.
