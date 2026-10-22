# Flyback Switching Power Supply

Design and simulation work for an isolated flyback switching power supply.

The project is being developed in two stages: a **low-voltage development prototype** for safe simulation and learning, followed by adaptation to the final universal AC input specification.

## Development Prototype Specifications

| Parameter           | Value   |
| ------------------- | ------- |
| Input               | 24 VDC  |
| Output              | 12 V    |
| Output power        | 24 W    |
| Output current      | 2 A     |
| Switching frequency | 100 kHz |
| Efficiency target   | 85%     |
| Regulation          | ±5%     |
| Isolation           | Yes     |

The low-voltage input is being used during the initial flyback design and simulation to avoid working with the high-voltage DC bus produced by an AC mains rectifier.

The output remains fixed at **12 V / 2 A** for this version. An adjustable-output version is planned as a future iteration.

## Final Target Specifications

| Parameter           | Value      |
| ------------------- | ---------- |
| Input               | 90–264 VAC |
| Input frequency     | 60 Hz      |
| Output              | 12 V       |
| Output power        | 24 W       |
| Output current      | 2 A        |
| Switching frequency | 100 kHz    |
| Efficiency target   | 85%        |
| Regulation          | ±5%        |
| Isolation           | Yes        |

The final version will use a universal AC input with a bridge rectifier, bulk capacitor, inrush-current limiting, and isolated flyback converter.

## Project Status

Currently paralleling the design process between kicad and ltspice simulation 

### Low-Voltage Flyback Development

* [ ] Low-voltage input stage — 24 VDC
* [ ] Flyback transformer design
* [ ] Primary-side switch + controller selection
* [ ] Secondary-side rectification + output filtering
* [ ] Feedback/compensation loop
* [ ] Efficiency and regulation validation

### Final AC Input Version

* [x] Bridge rectifier + bulk capacitor front-end — designed and simulated in LTspice
* [ ] Inrush current limiting (NTC/fuse)
* [ ] Adapt flyback design for ~126–373 VDC bus
* [ ] Primary-side switch + controller selection
* [ ] Secondary-side rectification + output filtering
* [ ] Feedback/compensation loop
* [ ] PCB layout

## Repo Structure

```text
/reports   - Written validation summaries with simulation screenshots
/sim       - LTspice schematic (.asc) and simulation files
```

## Reports

* [Rectifier & Bulk Capacitor Stage Validation](reports/rectifier_stage_validation_summary.md)

## Tools

* LTspice (schematic capture and simulation)

