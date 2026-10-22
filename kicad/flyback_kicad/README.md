# Flyback KiCad project: 24V in, 12V/2A out, 100kHz

Power stage only, ported from the validated LTspice circuit. Made in KiCad 7 format. KiCad 8 and 9 open it and offer to upgrade the files: click Yes.

## Open it
1. Unzip the folder and keep every file together.
2. KiCad > File > Open Project > `flyback.kicad_pro`.
3. Double-click `flyback.kicad_sch` (schematic) or `flyback.kicad_pcb` (board).

## Get to a printable PCB
1. Schematic: double-click T1, set the Footprint field (see gaps below).
2. References (R1, C1 ...) are already set, no annotation needed.
3. PCB Editor: Tools > Update PCB from Schematic (F8) > Update PCB. All footprints and nets load; click to drop them on the board.
4. Place parts, then route with X. Keep GND_PRI and GND_SEC separate.
5. Draw the board outline on layer Edge.Cuts (Place > Line, then close the shape).
6. File > Print, or File > Plot for Gerbers.

## Nets (matches LTspice)
| Net | Pins |
|---|---|
| VIN | J1.1, T1.1 (dot), C3.1, R1.1 |
| GND_PRI | J1.2, J3.2, Q1.S (1-3), R3.2 |
| DRAIN | T1.2, Q1.D (5-8), D2 anode |
| SNUB | D2 cathode, C3.2, R1.2 |
| SEC_AC | T1.4, D1 anode |
| VOUT | D1 cathode, C1+, C2+, J2.1 |
| GND_SEC | T1.3 (dot), C1-, C2-, J2.2 |
| GATE_DRV | J3.1, R2.1 |
| GATE | R2.2, Q1.G (4), R3.1 |

## Parts
| Ref | Part | Footprint |
|---|---|---|
| Q1 | MCQ15N10YA-TP | SOIC-8 (S=1-3, G=4, D=5-8, from MCC datasheet) |
| D1 | 1N5822 Schottky | DO-201AD |
| D2 | UF4007 | DO-41 |
| C1, C2 | 47uF/25V electrolytic | Radial D6.3mm, pin 1 = + |
| C3 | 560nF/100V film | Rect 7.2 x 5.5mm, 5mm pitch |
| R1 | 390 ohm, 5W | Axial power 22.4mm |
| R2, R3 | 10 ohm, 10k | Axial DIN0207 |
| J1, J2 | 2-pin terminal block | 5.08mm |
| J3 | 2-pin header (gate drive in) | 2.54mm |
| T1 | Lp 20.7uH, Np:Ns = 1:1.57 | none yet |

## Known gaps
- T1 has no footprint. Pick one once the core and bobbin are chosen (or a placeholder header for bench wiring).
- No PWM controller, current sense resistor or feedback loop. Gate is driven externally through J3.
- R2 (10 ohm) and R3 (10k) are not in the LTspice simulation yet.
- Q1 is the only SMD part (SOIC-8); everything else is through-hole.
- R1 dissipates about 2.3W at the 30V clamp (30V^2 / 390 ohm), so the 5W part has 2x margin.
- 24V prototype spacing only. The 90-264VAC version needs new creepage and clearance.
