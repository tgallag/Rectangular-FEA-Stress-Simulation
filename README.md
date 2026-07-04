# Rectangular FEA Stress Simulation

ANSYS finite-element study of a 2 mm x 6 mm x 1.25 mm structural-steel cantilever beam under a 100 N static end load.

[![Rectangular FEA stress animation](Structural%20Analysis/Results/rectangle_cube_animation.gif)](Structural%20Analysis/Results/rectangle_cube_animation.gif)

Project inspiration: [Zein Zreik's 3-DOF parallel robot project](https://github.com/ZeinZreik/Design-and-Implementation-of-a-3-DOF-Parallel-Robot).

## Project Scope

- Geometry: rectangular cantilever beam
- Material: structural steel, S275N
- Load case: 100 N applied in the +X direction on the free-end face
- Boundary condition: fixed support at the opposite end
- Result focus: equivalent stress and total deformation

## Project Organization

```text
Design/                 geometry drawings and dimensioned model views
Functional Analysis/    hand calculations, assumptions, and LaTeX math report
Structural Analysis/    ANSYS setup notes and stress/deformation result media
Programming/            reserved for scripts or code if added later
Report/                 final README/report figures and presentation visuals
```

## Key Deliverables

### Design

[![3D dimensioned beam view](Report/Figures/rectangular_beam_spaceclaim.png)](Design/Drawings/rectangular_beam_spaceclaim.pdf)

- [3D dimensioned view PDF](Design/Drawings/rectangular_beam_spaceclaim.pdf)
- [Dimensioned drawing PDF](Design/Drawings/rectangular_beam_dimensions.pdf)

### Functional Analysis

[![Calculation preview](Report/Figures/rectangular_beam_calculations.png)](Functional%20Analysis/Calculations/rectangular_beam_calculations.pdf)

- [Calculation PDF](Functional%20Analysis/Calculations/rectangular_beam_calculations.pdf)
- [LaTeX source](Functional%20Analysis/Calculations/rectangular_beam_calculations.tex)
- [Markdown calculation notes](Functional%20Analysis/calculation_notes.md)

### Structural Analysis

- [Stress animation GIF](Structural%20Analysis/Results/rectangle_cube_animation.gif)

## Results Snapshot

| Quantity | Hand estimate | ANSYS result |
| --- | ---: | ---: |
| Maximum equivalent stress | 720 MPa | 861.3 MPa |
| Estimated stress bound | 720 MPa | 917.7 MPa |
| Maximum deformation | 0.0432 mm | 0.0475 mm |

The ANSYS stress is higher than the beam-theory estimate because the fixed support creates a local 3D stress concentration. The deformation comparison is closer because the global cantilever stiffness is captured reasonably well by the hand calculation.


