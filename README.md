# Rectangular FEA Stress Simulation

Small ANSYS finite-element project showing stress and deformation in a 2 mm x 6 mm x 1.25 mm rectangular beam under a 100 N static end load. The project was inspired by Zein Zreik's 3-DOF parallel robot project, but this is a separate FEA study.

[![Rectangular FEA stress animation](rectangle_cube_animation.gif)](rectangle_cube_animation.gif)

## Project

- Geometry: rectangular cantilever beam, fixed at one end
- Material: structural steel
- Load: 100 N in the +X direction on the free-end face
- Result focus: equivalent stress and total deformation
- Math notes: [docs/math.md](docs/math.md)
- Animation: [rectangle_cube_animation.gif](rectangle_cube_animation.gif)

## Files

```text
rectangle_cube_animation.gif   click-to-preview simulation animation
docs/                          formulas, assumptions, and hand-calculation notes
simulation/                    curated ANSYS setup notes and reproducibility files
assets/                        optional screenshots or final plots
```

## Next

- Add final screenshots or plots only if they clarify the result
- Decide whether any small ANSYS setup files should be included for reproducibility
