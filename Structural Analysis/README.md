# Structural Analysis

ANSYS static structural setup notes and result media.

## Model Setup

- Analysis type: static structural
- Material: structural steel, S275N
- Fixed support: one end face of the beam
- Load: 100 N in the +X direction on the opposite end face
- Result quantities: equivalent stress and total deformation

## Results

- [Results/rectangle_cube_animation.gif](Results/rectangle_cube_animation.gif): stress/deformation animation exported for GitHub preview

Solver output used for the hand-check comparison gave a maximum equivalent stress of 861.3 MPa and maximum deformation of 0.0475 mm.
