# Assembly Workspace

A collection of Motorola 6800/68000 assembly language exercises, written for a computer organization . Each numbered folder contains an assignment description and its corresponding solution, covering arithmetic, conditional branching, array processing, and subroutines.

## Exercises

| Folder | Topic | Description |
|---|---|---|
| [`#1`](#1) | Arithmetic & memory | Computes `Z = (X + 3) * 6 - 4*Y` using values loaded from memory (`$90`, `$91`), storing the result at `$93`. Uses shift instructions (`ASLA`) for multiplication by powers of 2 |
| [`#2`](#2) | Conditional branching | Loads `x` and `y` from memory (`$50`, `$60`); if `x` is odd, computes `3x - y`, if even, computes `x/2` and `4y`; results stored back to the original addresses |
| [`#3`](#3) | Arrays & loops | Transforms a 5-element array `A` (starting at `$30`) into array `B` (`$40`) — halving even elements, doubling-and-incrementing odd elements — sums `B` into `$50`, then computes a difference array `C` |
| [`#4`](#4) | Subroutines & arrays | Similar array-transform-and-sum task to `#3`, but structured around a `JSR`-based subroutine for the add/subtract step, with a loop over a 5-element array |
| [`#5`](#5) | *(see note below)* | Task describes a nested-conditional arithmetic problem (`x = x*9 - y*7`, then conditional halving/doubling of `x`/`y`); **the committed source does not implement this** — see Discrepancies below |
| [`#6`](#6) | Arrays & comparison | Implements a C-style loop comparing two 5-element arrays `X` (`$80`) and `Y` (`$90`) element-wise; stores `1` into array `Z` (`$A0`) where `X[i] + Y[i] > 15`, else `0` |

Each folder also contains a `Contents` file with the original assignment/lab instructions.

## Discrepancies

**`#5`'s source file does not match its task description.** The assignment asks for an implementation of:
```c
x = (x * 9) - (y * 7);
if (x > 6) { if (y > 7) y *= 2; else y /= 2; }
else { x = x / 4; }
x = x + y;
```
but the committed code in `#5/#5` is an unrelated loop that increments a counter from 8 up to 10 and stores the result — it doesn't reference `x`, `y`, or any of the required memory addresses (`$50`, `$60`). This looks like the wrong file was committed for this exercise. If you have the correct solution, it should replace the current contents of `#5/#5`.

## Toolchain

These are written for the Motorola 6800/68HC11-style instruction set (`LDAA`/`LDAB`, `STAA`/`STAB`, `ASLA`, `BEQ`/`BNE`/`BPL`, `JSR`/`RTS`, etc.) as commonly used with 68xx simulators/assemblers in coursework (e.g. EASy68K or a 6800 simulator). No build system is included — assemble/run each file with whatever 6800-family assembler or simulator your course uses.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
